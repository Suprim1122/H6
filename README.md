# H6 Cybersecurity Assignment - February 2026

## x) Summary of Schneier's Applied Cryptography (Sections 2.3 & 2.4)

### 1.One-Way Functions
* **What it is:** Imagine a blender. It is very easy to turn an apple into apple juice (going forward). But it is impossible to turn the juice back into a solid apple (going backward).
* **How it works in math:** A one-way function is a mathematical process that is easy to calculate in one direction, but extremely hard (practically impossible) to reverse.
* **Why it matters:** They are the building blocks of modern security, making sure secrets stay secret even if the math process is known.

### 2. One-Way Hash Functions
* **What it is:** A hash function takes any amount of data (like a single password or an entire book) and scrambles it into a fixed-size string of letters and numbers called a "hash".
* **Key Rules:**
    * It is a one-way function (you can't read the hash and figure out the original password).
    * If you change even one tiny letter in the original data, the hash output changes completely.
* **Use case:** Websites use this to store passwords safely. Instead of saving your actual password, they save the "hash." When you log in, they hash what you typed and see if the two hashes match.


## a) Installing and Testing Hashcat

**Step 1: Install Hashcat**
I opened my terminal and typed the following command to install Hashcat:
bash
sudo apt update
sudo apt install hashcat
<img width="1025" height="535" alt="Screenshot 2026-03-05 at 8 32 59" src="https://github.com/user-attachments/assets/542cc1e5-be68-4d38-98db-9bb6f1903edd" />

To crack a password, Hashcat needs a list of common passwords to guess from. A famous one is called rockyou.txt.



## b) Cracking the Target Hash
**The Target:** d595b2086532422bbe654bc07ea030df

**Step 1: Identify the Hash**
The hash is 32 characters long, and it contains numbers and letters from a-f. This strongly suggests it is an MD5 hash.


**Step 2: Run Hashcat**
I used Hashcat to crack it. Here is what the command means:
* -m 0 tells Hashcat the hash type is MD5.
* -a 0 tells Hashcat to do a "dictionary attack" (read from a wordlist).
bash
hashcat -m 0 -a 0 target.txt /usr/share/wordlists/rockyou.txt
**Result:**
Hashcat successfully cracked the hash! The hidden password was: **disobey**


<img width="1025" height="735" alt="Screenshot 2026-03-05 at 8 36 29" src="https://github.com/user-attachments/assets/fa531a66-c2b7-4cc9-9580-3e2d53f79b8a" />

