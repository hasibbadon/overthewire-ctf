# Bandit Level 10 → Level 11

## 🧩 Level Goal

The password for this level is stored in `data.txt`, which contains **Base64 encoded data**.

Your task is to decode it and find the real password.

---

## 🔑 Credentials

* Username: `bandit10`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
ls
cat data.txt
base64 -d data.txt
```

---

## 🚀 Solution Steps

### 1. Login via SSH

```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

---

### 2. Check file content

```bash
cat data.txt
```

Output:

```
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
```

👉 This is **Base64 encoded text**

---

### 3. Decode the file

```bash
base64 -d data.txt
```

---

### 4. Final output

```
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj****
```

---

## 🔐 Password for Level 11

```text
dtR173fZKb0RRsDFSGsg2RWnpNVj****
```

---

## 🧠 Explanation

### 🔐 What is Base64?

Base64 is a way to encode binary/text data into readable characters.

It is NOT encryption — just encoding.

---

### 🔎 Why decoding is needed

The file contains:

```
VGhlIHBhc3N3b3JkIGlz...
```

This is not readable directly.

So we decode it using:

```bash
base64 -d
```

---

### ⚡ Key idea

| Action | Meaning                        |
| ------ | ------------------------------ |
| Encode | Convert text → Base64          |
| Decode | Convert Base64 → original text |

---

## 📌 What I Learned

* What Base64 encoding is
* How to decode encoded files
* Difference between encoding vs encryption
* Using `base64 -d` in Linux
* Recognizing encoded data in CTFs

---

## ⚠️ Important Insight

Many real systems store or transmit:

* API tokens
* cookies
* config values

in Base64 format.

So decoding is a key cybersecurity skill.

---

## ✅ Status

Completed
