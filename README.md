# 📝 Text File Character Counter

**Subject:** Performance in Cyber-Physical Systems
**Author:** Guilherme Montoya (Yashic)

A Java program that counts character occurrences in `.txt` files from a directory, using **multithreading** for optimized performance.

---

## 🚀 Features

* ✅ **Multithreaded processing** for efficient file reading
* ✅ Character frequency counting (A-Z, case insensitive)
* ✅ Execution time measurement
* ✅ Optimized for both small (100 files) and large (35,000 files) datasets
* ✅ Automatic thread count based on available processors

---

## 🛠️ Implementation Details

### 📂 Core Logic

1. **File Discovery:**
   Scans the specified directory for `.txt` files.

2. **Thread Management:**

   * Files are evenly divided into batches.
   * Each thread processes its assigned batch.

3. **Character Counting:**

   * Converts text to uppercase.
   * Counts occurrences of characters A-Z, ignoring others.

4. **Result Aggregation:**

   * Merges results from all threads.
   * Displays final character counts and processing statistics.

---

## ⚙️ Thread Optimization

The number of threads is automatically calculated based on the number of available processors:

```java
int numThreads = Runtime.getRuntime().availableProcessors();
```

You can also manually set the thread count if desired.

---

## 📊 Visual Representation of Processing

```mermaid
graph TD
    A[.txt Files in Directory] --> B{Split into Batches}
    B --> C1[Thread 1]
    B --> C2[Thread 2]
    B --> C3[...]
    B --> Cn[Thread N]
    
    C1 --> D1[Count Characters]
    C2 --> D2[Count Characters]
    C3 --> D3[Count Characters]
    Cn --> Dn[Count Characters]

    D1 --> E[Aggregate Results]
    D2 --> E
    D3 --> E
    Dn --> E

    E --> F[Display Final Counts and Execution Time]
```

This diagram illustrates how the files are divided among multiple threads, each counting characters in parallel, and finally aggregating the results.

---

## ⏱️ Performance Considerations

* ✅ Tested with both sample (100 files) and production (35,000 files) datasets.
* ✅ Thread count can be adjusted for specific hardware configurations.
* ✅ Execution time is displayed for benchmarking purposes.

---

## 🏁 How to Use

1. Run the `auto_unzip` shell script:

```bash
chmod +x auto_unzip.sh # To grant execution permission
./auto_unzip.sh # Execute to unzip both folders
```

2. Compile the program:

```bash
javac Main.java
```

3. Run the program:

```bash
java Main
```

4. When the program starts, you will see the following menu:

```
Which folder do you want to process?
1. All
2. Sample
3. Exit
```

* **Option 1:** processes all `.txt` files inside the **"All"** folder.
* **Option 2:** processes all `.txt` files inside the **"Sample"** folder.
* **Option 3:** exits the program.

5. Check the output in the console:

* Total number of files processed
* Successfully processed files
* Files with errors (if any)
* Consolidated character frequency (A-Z)
* Total execution time in milliseconds

6. If you want to clean all, just:

```bash
chmod +x clean_txt_files.sh # To grant execution permission
./clean_txt_files.sh # To clean all .txt files
``` 

---

## 📦 Code Structure

```java
public class CharacterCounter {
    // Main components:
    // - File discovery and validation
    // - Thread creation and management
    // - Character counting logic
    // - Result aggregation and display
}
```

---

## ✅ My Sample Output

```
-------------------------------------------------------
Current dir: /user/path/project
-------------------------------------------------------

Which directory do you want to process?
1. All
2. Sample
3. Exit
Enter your choice: 1
Number of .txt files to process: 100
Using 12 threads

Processing summary for 'All/amostra':
Total files: 100
Successfully processed: 100
Files with errors: 0
Time elapsed: 56 ms

Consolidated letter count:
A: 21246
B: 2130
C: 6504
D: 9155
E: 19566
F: 1923
...
Y: 62
Z: 626

Which directory do you want to process?
1. All
2. Sample
3. Exit
Enter your choice: 2
Number of .txt files to process: 34055
Using 12 threads

Processing summary for 'Sample':
Total files: 34055
Successfully processed: 34055
Files with errors: 0
Time elapsed: 1183 ms

Consolidated letter count:
A: 7584025
B: 710564
C: 2248600
D: 3228111
E: 6765352
...
Y: 45953
Z: 215838

```

---

## 🔧 Technical Notes

* Case-insensitive counting: A-Z treated the same as a-z.
* Non-alphabetic characters are ignored.
* Efficient file handling using `java.nio` and buffered reading.
* Designed for modern multi-core processors for maximum performance.

---