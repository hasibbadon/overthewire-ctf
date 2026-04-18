# Bandit Level 5 → Level 6

## 🧩 Level Goal

The goal of this level is to find the password stored in a file with specific conditions:

* Human-readable
* Exactly 1033 bytes in size
* Not executable

---

## 🔑 Credentials

* Username: `bandit5`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash id="k7m2pl"
ssh bandit5@bandit.labs.overthewire.org -p 2220
ls
cd inhere
find . -type f -size 1033c
cat ./maybehere07/.file2
```

---

## 🚀 Solution Steps

1. Login using SSH:

   ```bash
   ssh bandit5@bandit.labs.overthewire.org -p 2220
   ```

2. Navigate to the directory:

   ```bash
   cd inhere
   ```

3. There are many directories and files, so manual searching is not efficient.

4. Based on the hint:

   * File size = 1033 bytes
   * File type = regular file
   * Not executable

5. Use the `find` command:

   ```bash
   find . -type f -size 1033c
   ```

6. Output:

   ```bash
   ./maybehere07/.file2
   ```

7. Read the file:

   ```bash
   cat ./maybehere07/.file2
   ```

---

## 🔐 Password for Level 6

```id="n2k8qp"
HWasnPhtq9AVKe0dmk45nxy20cvUa****
```

---

## 🧠 Explanation

This level introduces searching files using conditions.

### 1. `find` command

* Used to search files and directories

### Important flags:

* `.` → start searching from current directory
* `-type f` → only look for files
* `-size 1033c` → file size exactly 1033 bytes (`c` = bytes)

### 2. Why not manual search?

* There are many directories and files
* Manual checking is slow and inefficient

### 3. Extra condition (from research)

```bash
find . -type f -size 1033c ! -executable
```

* `! -executable` → exclude executable files
* Makes the search more precise

---

## 📌 What I Learned

* How to use `find` command effectively
* Searching files based on size and type
* Using conditions to filter results
* Importance of automation over manual work
* How to handle large numbers of files

---

## ⚠️ Note

This challenge is part of the OverTheWire wargame for educational purposes.

---

## ✅ Status

Completed
