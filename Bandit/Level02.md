# Bandit Level 2 → Level 3

## 🧩 Level Goal

The goal of this level is to find the password stored in a file with spaces in its name.

---

## 🔑 Credentials

* Username: `bandit2`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash id="w8k2lm"
ssh bandit2@bandit.labs.overthewire.org -p 2220
ls
cat ./--spaces\ in\ this\ filename--
cat -- "--spaces in this filename--"
```

---

## 🚀 Solution Steps

1. Login using SSH:

   ```bash
   ssh bandit2@bandit.labs.overthewire.org -p 2220
   ```

2. List files:

   ```bash
   ls
   ```

3. Found a file:

   ```bash
   --spaces in this filename--
   ```

4. Direct use of `cat` fails because:

   * Spaces break the filename into multiple arguments
   * `--` is treated as an option

5. First solution (escape spaces + relative path):

   ```bash
   cat ./--spaces\ in\ this\ filename--
   ```

6. Second solution (cleaner and important):

   ```bash
   cat -- "--spaces in this filename--"
   ```

---

## 🔐 Password for Level 3

```id="j9s2kd"
MNk8KNH3Usiio41PRUEoDFPqfxLPl****
```

---

## 🧠 Explanation

This level introduces two problems:

### 1. Spaces in filenames

* Linux treats spaces as separators
* So we must escape them using `\`
  👉 `this\ is\ file`

### 2. `--` special meaning

* Many commands treat `--` as the **end of options**
* Anything after `--` is treated as a filename, not an option

So:

* `cat -- "--spaces in this filename--"`
  👉 tells `cat`: “stop parsing options, this is a filename”

### Alternative method

* `./filename` avoids option confusion
* `\` escapes spaces

---

## 📌 What I Learned

* How to handle filenames with spaces
* How to escape characters using `\`
* Meaning of `--` (end of command options)
* Multiple ways to solve the same problem
* Importance of experimenting with commands

---

## ⚠️ Note

This challenge is part of the OverTheWire wargame for educational purposes.

---

## ✅ Status

Completed
