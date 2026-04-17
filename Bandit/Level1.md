# Bandit Level 1 → Level 2

## 🧩 Level Goal

The goal of this level is to find the password for the next level. The password is stored in a file in the home directory.

---

## 🔑 Credentials

* Username: `bandit1`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash id="c9r2p1"
ssh bandit1@bandit.labs.overthewire.org -p 2220
ls
cat -
cat ./-
```

---

## 🚀 Solution Steps

1. Login using SSH:

   ```bash
   ssh bandit1@bandit.labs.overthewire.org -p 2220
   ```

2. List files in the home directory:

   ```bash
   ls
   ```

3. The output shows a file named:

   ```bash
   -
   ```

4. Initially, trying:

   ```bash
   cat -
   ```

   does not work and appears to hang.

5. After researching, it is found that `-` is treated as a special character in Linux (standard input).

6. To access the file, we must specify its path explicitly:

   ```bash
   cat ./-
   ```

7. This successfully prints the password.

---

## 🔐 Password for Level 2

```
263JGJPfgU6LtdEvgfWU1XP5yac29****
```

---

## 🧠 Explanation

In Linux, the symbol `-` is a special character and is often used to represent **standard input (stdin)**.

So when we run:

* `cat -` → it waits for input instead of reading a file

To solve this, we need to explicitly tell the system that `-` is a filename, not a special symbol.

* `./-` means:
  👉 “the file named `-` in the current directory”

* `cat ./-` → correctly reads the file

---

## 📌 What I Learned

* Special filenames can behave differently in Linux
* `-` is treated as standard input in many commands
* How to bypass special character issues using `./`
* Importance of researching errors and hints

---

## ⚠️ Note

This challenge is part of the OverTheWire wargame and is intended for educational purposes.

---

## ✅ Status

Completed
