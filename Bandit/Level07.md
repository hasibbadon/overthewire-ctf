# Bandit Level 7 → Level 8

## 🧩 Level Goal

The goal of this level is to find the password stored in a large file (`data.txt`) next to the word **"millionth"**.

---

## 🔑 Credentials

* Username: `bandit7`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
ls
grep "millionth" data.txt
```

---

## 🚀 Solution Steps

1. Login using SSH:

   ```bash
   ssh bandit7@bandit.labs.overthewire.org -p 2220
   ```

2. List files:

   ```bash
   ls
   ```

   → Found `data.txt`

3. The file is very large, so using `cat` is inefficient.

4. Use `grep` to search for the keyword:

   ```bash
   grep "millionth" data.txt
   ```

5. Output:

   ```bash
   millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7****
   ```

---

## 🔐 Password for Level 8

```id="p8q2ls"
dfwvzFQi4mU0wfNbFOe9RoWskMLg7e****
```

---

## 🧠 Explanation

This level focuses on searching **inside large files efficiently**.

### 🔎 Why not `cat`?

* `cat data.txt` prints everything
* File is huge → hard to read

### 🔎 `grep` usage

```bash
grep "millionth" data.txt
```

👉 Searches for lines containing `"millionth"`
👉 Returns only the matching line

---

## 🔁 Concept Reinforcement

### 🧭 `find` vs 🔎 `grep`

| Command | Purpose             |
| ------- | ------------------- |
| `find`  | Find files          |
| `grep`  | Search inside files |

---

## 💥 Real CTF Workflow

```bash
find . -type f -name "*.txt" -exec grep "password" {} \;
```

👉 Find files → then search inside them word password

---

## 📌 What I Learned

* How to search inside large files efficiently
* Using `grep` for keyword matching
* Avoiding manual reading of huge files
* Difference between `find` and `grep`
* Practical CTF workflow (find + grep)

---

## ⚠️ Note

This challenge is part of the OverTheWire wargame for educational purposes.

---

## ✅ Status

Completed
