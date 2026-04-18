# Bandit Level 12 → Level 13

## 🧩 Level Goal

The password for the next level is stored in `data.txt`, which is a **hexdump of a file that has been repeatedly compressed**.

Your task is to reverse the process step by step to recover the original file and extract the password.

---

## 🔑 Credentials

* Username: `bandit12`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
ssh bandit12@bandit.labs.overthewire.org -p 2220
mkdir /tmp/hasibbadon
cd /tmp/hasibbadon
cp ~/data.txt .
xxd -r data.txt data.bin
file data.bin
mv data.bin data.gz
gzip -d data.gz
file data
mv data data.bz2
bzip2 -d data.bz2
file data
mv data data.gz
gzip -d data.gz
file data
tar -xf data
file data5.bin
tar -xf data5.bin
file data6.bin
tar -xf data6.bin
file data8.bin
mv data8.bin data.gz
gzip -d data.gz
file data
cat data
```

---

## 🚀 Solution Steps

### 1. Setup working directory

```bash
mkdir /tmp/hasibbadon
cd /tmp/hasibbadon
cp ~/data.txt .
```

---

### 2. Convert hexdump back to binary

```bash
xxd -r data.txt data.bin
file data.bin
```

---

### 3. First decompression (gzip)

```bash
mv data.bin data.gz
gzip -d data.gz
file data
```

---

### 4. Second decompression (bzip2)

```bash
mv data data.bz2
bzip2 -d data.bz2
file data
```

---

### 5. Third decompression (gzip again)

```bash
mv data data.gz
gzip -d data.gz
file data
```

---

### 6. Extract tar archive

```bash
tar -xf data
```

---

### 7. Repeat extraction steps

```bash
file data5.bin
tar -xf data5.bin
file data6.bin
tar -xf data6.bin
file data8.bin
```

---

### 8. Final gzip extraction

```bash
mv data8.bin data.gz
gzip -d data.gz
file data
```

---

### 9. Get final password

```bash
cat data
```

Output:

```
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdT****
```

---

## 🔐 Password for Level 13

```text
FO5dwFsc0cbaIiH0h8J2eUks2vdT****
```

---

## 🧠 Explanation

### 🔐 What is happening here?

The file has been wrapped in multiple layers like a Russian nesting doll. First, it was compressed multiple times using a mix of `gzip`, `bzip2`, and `tar`. Finally, the resulting binary file was converted into a **hexdump** (a text representation of binary data). 

Each layer must be reversed step by step using the correct tool.

---

### 🔎 Why checking the file type is needed

Because the extensions were removed or misleading, we cannot guess how the file is compressed. We must use the `file` command to read the file's **magic bytes** (headers) to figure out what kind of archive we are dealing with at each step.

---

### ⚡ Key idea

| Action / Command | Meaning                        |
| ---------------- | ------------------------------ |
| `xxd -r`         | Revert a hexdump back to a binary file |
| `file`           | Identify the actual file type based on headers |
| `gzip -d`        | Decompress a gzip archive      |
| `bzip2 -d`       | Decompress a bzip2 archive     |
| `tar -xf`        | Extract files from a tarball   |

---

## 📌 What I Learned

* How to reverse hexdumps using `xxd -r`
* How to reliably identify file types using the `file` command
* How multiple compression layers work
* How to extract nested archives (`gzip`, `bzip2`, `tar`)
* Real-world forensic decompression logic

---

## ⚠️ Important Insight

In real-world systems, attackers (or automated systems) may:
* Compress data multiple times to bypass simple filters
* Hide malicious payloads inside nested archives
* Encode files (like using hexdumps or Base64) before storage or transmission

Therefore, always check the true file type using the `file` command before blindly opening or executing an unknown file based purely on its extension.

---

## ✅ Status

Completed
