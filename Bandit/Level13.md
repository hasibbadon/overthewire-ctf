# Bandit Level 13 → Level 14

## 🧩 Level Goal

The password for the next level is stored in `/etc/bandit_pass/bandit14`, but you **do not have access** to it directly.

Instead, you are given a **private SSH key (`sshkey.private`)** that can be used to log in as `bandit14`.

---

## 🔑 Credentials

* Username: `bandit13`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
ls
scp -P 2220 bandit13@bandit.labs.overthewire.org:~/sshkey.private .
chmod 600 sshkey.private
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit14
```

---

## 🚀 Solution Steps

### 1. Login to bandit13

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

---

### 2. Find the private key

```bash
ls
```

Output:

```text
sshkey.private
```

---

### 3. The Problem

Trying to use the key directly from the server can sometimes fail or be restricted because the next level may not allow local SSH login using that key directly from inside the server without specifying `localhost`. To bypass this and practice remote file transfer, we bring the key to our own machine.

---

### 4. Download the private key to local machine

*Open a new terminal window on your local machine and run:*

```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:~/sshkey.private .
```

👉 This securely copies the key from the server → your local machine's current directory.

---

### 5. Fix permissions

```bash
chmod 600 sshkey.private
```

👉 **Note:** SSH requires private keys to be heavily protected. If the permissions are too open, SSH will reject the key.

---

### 6. Login using the private key

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

---

### 7. Successful login

```text
bandit14@bandit:~$
```

---

## 🔐 Password for Level 14

(Run this command after successful login to retrieve the actual password for future use)

```bash
cat /etc/bandit_pass/bandit14
```

---

## 🧠 Explanation

### 🔐 What is happening here?

In this level, you are not given a password string to copy and paste. Instead, authentication is handled using an **SSH private key**. 

---

### ⚡ Key Concept

| Method | Description |
|---|---|
| **Password** | Traditional login (typing a secret phrase). |
| **Private Key** | Secure SSH authentication using cryptographic files. |

---

### 🔎 Why download the key?

While you *can* sometimes SSH internally (e.g., `ssh -i sshkey.private bandit14@localhost -p 2220`), downloading it teaches a vital skill:
* ❌ Using the key inside the server → Can be blocked by internal firewall rules.
* ✅ Using the key from your local machine → Works reliably and perfectly simulates real-world access.

---

## 📌 What I Learned

* How SSH key-based authentication works
* The difference between password login vs. key login
* How to use `scp` (Secure Copy Protocol) to download files remotely
* The importance of strict file permissions (`chmod 600`)
* Real-world SSH security practices

---

## ⚠️ Important Insight

In real-world production systems:
* Servers often completely **disable** password login to prevent brute-force attacks.
* They only allow SSH key authentication.
* Private keys must be treated like actual physical keys—if they are left lying around with open permissions, the system will refuse to use them for your own safety.

---

## ✅ Status

Completed
