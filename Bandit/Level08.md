# Bandit Level 8 → Level 9

## 🧩 Level Goal

The goal of this level is to find the password in `data.txt`.
The password is the **only line that occurs once**.

---

## 🔑 Credentials

* Username: `bandit8`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
sort data.txt | uniq -u
```

---

## 🚀 Solution Steps

1. Login using SSH:

   ```bash
   ssh bandit8@bandit.labs.overthewire.org -p 2220
   ```

2. The file contains many repeated lines.

3. We need to find the **unique (non-duplicate) line**.

4. Use:

   ```bash
   sort data.txt | uniq -u
   ```

5. Output:

   ```bash
   4CKMh1JI91bUIZZPXDqGanal4xvA****
   ```

---

## 🔐 Password for Level 9

```text
4CKMh1JI91bUIZZPXDqGanal4xvAg****
```

---

## 🧠 Explanation

This level introduces **sorting + filtering duplicates**.

### 🔁 Why `sort` is needed

* `uniq` only works on **adjacent (neighboring) lines**
* If the file is unsorted → duplicates are scattered

👉 So we first use:

```bash
sort data.txt
```

→ Groups identical lines together

---

### 🔍 `uniq -u`

```bash
uniq -u
```

* Shows only **unique lines**
* Removes duplicates completely

---

### 💥 Combined Command

```bash
sort data.txt | uniq -u
```

👉 Workflow:

* `sort` → group duplicates
* `uniq -u` → extract only the unique line

---

## ❗ When you DON'T need `sort`

If file is already like:

```
apple
apple
banana
banana
```

👉 Then:

```bash
uniq -u
```

works directly

But in CTF (like Bandit):
👉 files are intentionally **unsorted**

---

## 📌 What I Learned

* How to find unique values in a file
* Why `sort` is important before `uniq`
* How `uniq` works internally
* Using pipe `|` to combine commands
* Thinking logically about data processing

---

## ⚠️ Note

This challenge is part of the OverTheWire wargame for educational purposes.

---

## ✅ Status

Completed
