# 📝 Task 1: Data Engineer Log Processing Challenge


### 🎯 Scenario:

You are working as a **junior Data Engineer** in a company. Your manager gave you a raw log file and asked you to clean and organize it.

You need to:

1. **Create a project folder structure** under your home directory:
    
    ```
    ~/project_pipeline/
        ├── data/
        │    ├── raw/
        │    └── processed/
        └── logs/
    
    ```
    
2. Inside `data/raw/`, create a file called `server.log` with at least these sample lines (you can add more):
    
    ```
    INFO 2025-09-21 Server started
    ERROR 2025-09-21 Database connection failed
    INFO 2025-09-21 User logged in
    WARNING 2025-09-21 Disk almost full
    ERROR 2025-09-21 Timeout while querying API
    INFO 2025-09-21 Backup completed
    
    ```
    
3. **Process the log file** using Bash commands:
    - Extract only the lines with `ERROR`.
    - Count how many errors are there.
    - Save the extracted errors into `data/processed/errors.txt`.
    - Save the count of errors into `logs/error_count.txt`.
4. **Bonus twist (tricky part):**
    - Sort the errors alphabetically and remove duplicates before saving.
    - Compress the `errors.txt` file into `errors.txt.gz`.
    - Make sure file permissions are set so only the owner can read/write it.

---

### ✅ Expected Deliverables:

- Folder structure exists.
- `errors.txt.gz` inside `data/processed/` (containing unique, sorted error lines).
- `error_count.txt` inside `logs/` with just a number (e.g., `2`).
- Correct permissions on `errors.txt.gz` (`rw-------`).






## ⚙️ Steps Performed

```bash
# Extract all error lines from the log file
grep -i "error" server.log > errors.txt

# Count total errors
grep -c -i "error" server.log > logs/error_count.txt

# Sort and remove duplicate entries
sort errors.txt | uniq > errors_sorted.txt

# Compress and secure the final output
gzip errors_sorted.txt
chmod 600 errors_sorted.txt.gz




