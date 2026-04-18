# Bandit Level 6 → Level 7

## 🧩 Level Goal

The goal of this level is to find the password stored in a file somewhere on the system with the following conditions:

* Owned by user `bandit7`
* Owned by group `bandit6`
* Exactly 33 bytes in size

---

## 🔑 Credentials

* Username: `bandit6`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash id="k9p2lm"
ssh bandit6@bandit.labs.overthewire.org -p 2220
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```

---

## 🚀 Solution Steps

1. Login using SSH:

   ```bash
   ssh bandit6@bandit.labs.overthewire.org -p 2220
   ```

2. The file is not in the home directory, so we need to search the entire system.

3. Use the `find` command with conditions:

   ```bash
   find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
   ```

4. Output:

   ```bash
   /var/lib/dpkg/info/bandit7.password
   ```

5. Read the file:

   ```bash
   cat /var/lib/dpkg/info/bandit7.password
   ```

---

## 🔐 Password for Level 7

```id="l2m8qp"
morbNTDkSW6jIlUc0ymOdMaLnOlFV****
```

---

## 🧠 Explanation

This level focuses on **advanced file searching across the system**.

### 🔍 `find` breakdown

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

* `/` → search from root (entire filesystem)
* `-user bandit7` → file owned by user `bandit7`
* `-group bandit6` → file belongs to group `bandit6`
* `-size 33c` → file size exactly 33 bytes (`c` = bytes)

---

### ⚠️ Handling Errors

When searching the whole system, many directories are restricted.

You saw lots of:

```
Permission denied
```

To hide these errors:

```bash
2>/dev/null
```

👉 This redirects error output (stderr) to `/dev/null` (black hole)

---

### 🧠 Why this matters

* Real systems have thousands of files
* Many directories are restricted
* You must filter smartly and ignore noise

---

## 📌 What I Learned

* Searching entire system using `find /`
* Filtering using user, group, and size
* Understanding file ownership
* Using `2>/dev/null` to hide errors
* Working efficiently in restricted environments

---

## ⚠️ Note

This challenge is part of the OverTheWire wargame for educational purposes.

---

## ✅ Status

Completed
