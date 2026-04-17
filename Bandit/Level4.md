# Bandit Level 4 → Level 5

## 🧩 Level Goal

The goal of this level is to find the password stored in one of many files. Only one file contains human-readable text.

---

## 🔑 Credentials

* Username: `bandit4`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
ls
cd inhere
cat ./-file07
file ./*
file ./* | grep ASCII
strings ./*
strings ./* | grep -E '^[a-zA-Z0-9]{20,}$'
```

---

## 🚀 Solution Steps

1. Login using SSH:

   ```bash
   ssh bandit4@bandit.labs.overthewire.org -p 2220
   ```

2. Navigate to the directory:

   ```bash
   cd inhere
   ```

3. List files:

   ```bash
   ls
   ```

4. There are multiple files (`-file00` to `-file09`).

5. First approach (manual):

   * Open each file using `cat`
   * Most files show unreadable (binary) data
   * One file shows readable text → `-file07`

6. Smarter approach (automated):

   Find readable files:

   ```bash
   file ./* | grep ASCII
   ```

   Output:

   ```bash
   ./-file07: ASCII text
   ```

7. Extract readable strings:

   ```bash
   strings ./* | grep -E '^[a-zA-Z0-9]{20,}$'
   ```

---

## 🔐 Password for Level 5

```id="p9s3kd"
4oQYVPkxZOOEOO5pTW81FB8j8lxXGU****
```

---

## 🧠 Explanation

This level teaches how to deal with multiple files efficiently.

### 1. Binary vs Text Files

* Most files contain binary data → unreadable characters
* Only one file contains readable ASCII text

### 2. `file` command

* Used to detect file type
* Example:

  ```bash
  file ./-file07
  ```

  → shows `ASCII text`

### 3. `grep`

* Filters output based on pattern

### 4. Pipe `|`

* Combines commands
* Output of one command → input of another

Example:

```bash
file ./* | grep ASCII
```

👉 Only shows files that contain readable text

### 5. `strings`

* Extracts readable text from binary files

---

## 📌 What I Learned

* Difference between binary and text files
* How to analyze multiple files efficiently
* Using `file` to detect file types
* Using `grep` to filter results
* Using `|` (pipe) to combine commands
* Thinking smarter instead of manual work

---

## ⚠️ Note

This challenge is part of the OverTheWire wargame for educational purposes.

---

## ✅ Status

Completed
