# Bandit Level 11 → Level 12

## 🧩 Level Goal

The password for this level is stored in `data.txt`, which contains text encoded using the **ROT13 cipher**.

Your task is to decode it and find the real password.

---

## 🔑 Credentials

* Username: `bandit11`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
ls
cat data.txt
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

---

## 🚀 Solution Steps

### 1. Login via SSH

```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

---

### 2. Check file content

```bash
cat data.txt
```

Output:

```
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
```

👉 This is **ROT13 encoded text**

---

### 3. Decode the file

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

---

### 4. Final output

```
The password is 7x16JArUVv5LxVuJfsSVdbbtaHGl****
```

---

## 🔐 Password for Level 12

```text
7x16JArUVv5LxVuJfsSVdbbtaHGlw****
```

---

## 🧠 Explanation

### 🔐 What is ROT13?

ROT13 is a simple substitution cipher that shifts each letter by 13 positions in the alphabet. It is frequently used in CTF challenges to hide spoilers or basic text. 

It is NOT secure encryption — just a simple encoding technique.

---

### 🔎 Why decoding is needed

The file contains:

```
Gur cnffjbeq vf...
```

This is obfuscated and not readable directly.

So we decode it using the translate (`tr`) command to map the shifted letters back to their original positions:

```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

---

### ⚡ Key idea

| Action | Meaning                        |
| ------ | ------------------------------ |
| Encode | Shift text forward by 13 positions |
| Decode | Shift text again by 13 positions to reveal original |

---

## 📌 What I Learned

* How the ROT13 cipher works
* How to use the `tr` command for decoding and character mapping
* Reading hidden text from files
* Recognizing simple encoded data in CTF environments

---

## ⚠️ Important Insight

ROT13 is a symmetric encoding technique. Because the English alphabet has 26 letters, shifting by 13 twice returns you back to the exact same starting point.

Applying ROT13 to an already ROT13-encoded string will instantly decode it. It provides zero actual cryptographic security.

---

## ✅ Status

Completed
