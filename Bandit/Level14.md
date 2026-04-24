# Bandit Level 14 → Level 15

## 🧩 Level Goal

The password for the next level can be retrieved by submitting the **password of the current level** to a service running on **localhost at port 30000**.

---

## 🔑 Credentials

* Username: `bandit14`
* Password: (from previous level)
* Host: `bandit.labs.overthewire.org`
* Port: `2220`

---

## 🛠️ Commands Used

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit14
telnet localhost 30000
nc localhost 30000
```

---

## 🚀 Solution Steps

### 1. Login via SSH

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

---

### 2. Get current level password

```bash
cat /etc/bandit_pass/bandit14
```

Output:

```text
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

---

### 3. Connect to the service

Using `telnet`:

```bash
telnet localhost 30000
```

---

### 4. Submit the password

Once connected, paste the password from the previous step:

```text
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

---

### 5. Receive next password

Output:

```text
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2t****
```

---

### 💡 Alternative Method: Using netcat

You can also achieve the exact same result using `nc` (netcat):

```bash
nc localhost 30000
```

Then simply paste the password and hit enter.

---

## 🔐 Password for Level 15

```text
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJ****
```

---

## 🧠 Explanation

### 🔐 What is happening here?

This level introduces interacting with a live network service running locally. The server is listening on port `30000`. You must connect to this port using a raw TCP connection, send the correct password string, and receive the automated response. 

**Important Behavior:**
* The service expects *only* the exact password. 
* Any extra input or commands (like `ls` or `dir`) will be evaluated as incorrect, and the service will return an error or ignore it.
* After a correct input is received, it prints the flag and automatically closes the connection.

---

### ⚡ Key Concept

| Tool | Purpose |
| :--- | :--- |
| `telnet` | An older protocol and command-line tool used to establish interactive, bidirectional text-based communication over TCP. |
| `nc` (netcat) | A versatile, lightweight "Swiss Army knife" network tool used to read from and write to network connections using TCP or UDP. |

---

## 📌 What I Learned

* How to interact with TCP services running on specific ports
* The practical difference between `telnet` and `nc`
* How to send raw text input to a remote service via the command line
* Basic client-server communication concepts

---

## ⚠️ Important Insight

In real-world systems and infrastructure:
* Many critical services (like databases, internal APIs, or cache servers) run on specific, non-standard ports.
* Authentication and communication often happen over raw TCP sockets.
* Tools like `nc` and `telnet` are incredibly powerful for debugging, testing services, or establishing simple connections during penetration testing and system administration.

---

## ✅ Status

Completed
