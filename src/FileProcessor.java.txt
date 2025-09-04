import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class FileProcessor {
    public static void main(String[] args) {
        System.out.println("2025-09-04 10:00:12 INFO  Starting FileProcessor...");

        try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
            System.out.println("2025-09-04 10:00:13 INFO  Opening file: data.txt");
            String line;
            long start = System.currentTimeMillis();
            while ((line = br.readLine()) != null) {
                // Simulate slow processing
                try { Thread.sleep(1000); } catch (InterruptedException e) {}
                System.out.println("2025-09-04 10:00:15 INFO  Processing line: " + line);
            }
            long end = System.currentTimeMillis();
            if (end - start > 2000) {
                System.out.println("2025-09-04 10:00:18 WARN  Processing is slow (" + (end - start) + "ms)");
            }
            System.out.println("2025-09-04 10:00:19 INFO  Finished processing.");
        } catch (IOException e) {
            System.out.println("2025-09-04 10:00:13 ERROR File not found: data.txt");
            System.out.println("2025-09-04 10:00:14 INFO  Retrying with backup file...");
        }
    }
}
