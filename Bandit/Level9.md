# Bandit Level 9 → Level 10

## 🧩 Level Goal

Find the password inside `data.txt`.
The file contains **human-readable strings hidden inside binary data**.

---

## 🔑 Credentials

* Username: `bandit9`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
strings data.txt
strings data.txt | grep "="
```

---

## 🚀 Solution Steps

1. Login via SSH:

   ```bash
   ssh bandit9@bandit.labs.overthewire.org -p 2220
   ```

2. Try reading file normally:

   ```bash
   cat data.txt
   ```

   → Output is unreadable (binary data)

3. Try `grep`:

   ```bash
   grep "=" data.txt
   ```

   ❌ Problem:

   ```
   grep: data.txt: binary file matches
   ```

4. Use `strings` to extract readable text:

   ```bash
   strings data.txt
   ```

5. Now filter meaningful patterns:

   ```bash
   strings data.txt | grep "="
   ```

6. Find password:

   ```
   FGUW5ilLVJrxX9kMYMmlN4MgbpfM****
   ```

---

## 🔐 Password for Level 10

```text
FGUW5ilLVJrxX9kMYMmlN4MgbpfM****
```

---

## 🧠 Explanation

### 💥 Why `grep` failed

* `grep` works on **text files**
* But `data.txt` contains **binary data**
* So grep says:

  ```
  binary file matches
  ```

---

### 🔎 Why `strings` works

```bash
strings data.txt
```

* Extracts only **human-readable text**
* Ignores binary noise
* Perfect for CTFs and malware analysis

---

## 🔗 Pipe Magic

```bash
strings data.txt | grep "="
```

### What happens:

* `strings` → extracts readable text
* `grep "="` → filters lines containing `=`

---

## 📌 Key Learning

* Difference between **text vs binary files**
* Why `grep` fails on binary data
* How `strings` helps extract hidden data
* Combining tools using pipe `|`

---

## ⚠️ Important Insight

This level teaches a real cybersecurity concept:

> 🔥 Attackers hide data inside binary files
> 🔥 Analysts use `strings` to extract hidden content

---

## ✅ Status

Completed
