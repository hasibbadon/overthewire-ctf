# Bandit Level 3 → Level 4

## 🧩 Level Goal

The goal of this level is to find the password stored in a hidden file inside a directory.

---

## 🔑 Credentials

* Username: `bandit3`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash id="z8k3lp"
ssh bandit3@bandit.labs.overthewire.org -p 2220
ls
cd inhere
ls -la
cat ...Hiding-From-You
```

---

## 🚀 Solution Steps

1. Login using SSH:

   ```bash
   ssh bandit3@bandit.labs.overthewire.org -p 2220
   ```

2. List files in the home directory:

   ```bash
   ls
   ```

3. Found a directory:

   ```bash
   inhere
   ```

4. Enter the directory:

   ```bash
   cd inhere
   ```

5. Using normal `ls`, no files are visible:

   ```bash
   ls
   ```

6. Use `ls -la` to show hidden files:

   ```bash
   ls -la
   ```

7. Found a hidden file:

   ```bash
   ...Hiding-From-You
   ```

8. Read the file:

   ```bash
   cat ...Hiding-From-You
   ```

---

## 🔐 Password for Level 4

```id="d7s2pl"
2WmrDFRmJIq3IPxneAaMGhap0pFhF****
```

---

## 🧠 Explanation

By default, the `ls` command does **not show hidden files**.

In Linux:

* Files starting with `.` (dot) are considered hidden
* `..` represents parent directory
* `.` represents current directory

The file:

```bash
...Hiding-From-You
```

starts with dots, so it is hidden.

To view hidden files:

* `ls -a` → shows hidden files
* `ls -la` → shows hidden files with details

Once discovered, the file can be read normally using `cat`.

---

## 📌 What I Learned

* Hidden files start with `.` in Linux
* `ls` vs `ls -a` vs `ls -la`
* How to explore directories step by step
* Importance of checking hidden files in CTF challenges

---

## ⚠️ Note

This challenge is part of the OverTheWire wargame for educational purposes.

---

## ✅ Status

Completed

