# Bandit Level 0 → Level 1

## 🧩 Level Goal

The goal of this level is to log into the Bandit server using SSH and retrieve the password for the next level.

---

## 🔑 Credentials

* Username: `bandit0`
* Password: `bandit0`
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
```

---

## 🚀 Solution Steps

1. Open a Linux terminal.
2. Connect to the server using SSH.
3. Since SSH uses a custom port here, we specify `-p 2220`.
4. After login, list files using `ls`.
5. A file named `readme` appears.
6. Read it using `cat readme`.
7. The password for the next level is inside the file.

---

## 🧠 Explanation

SSH (Secure Shell) is used to remotely access another machine securely over a network.

Normally SSH runs on **port 22**, but in this challenge it runs on **port 2220**, so we must manually specify it using `-p`.

* `ssh bandit0@bandit.labs.overthewire.org` → connects to the remote server using username `bandit0`
* `-p 2220` → tells SSH to use port 2220 instead of default 22
* `ls` → lists files in the current directory
* `cat readme` → prints file contents

After login, we are inside a remote Linux system and can execute commands normally.

---

## 🔐 Password for Level 1

ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5****

---

## 📌 What I Learned

* How SSH works for remote login
* Difference between default port (22) and custom port (2220)
* Basic Linux commands (`ls`, `cat`)
* How to explore a remote system

---

## ⚠️ Note

This is part of the OverTheWire wargame environment used for learning cybersecurity.

---

## ✅ Status

Completed
