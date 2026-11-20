# Week 3 Project – Password Cracking with John the Ripper & NetworkWalks Tools

## Project Overview

This project is part of the Week 3 Cybersecurity & Ethical Hacking practical tasks from NetworkWalks Academy.

The objective was to understand password recovery techniques by testing password-protected PDF documents using two different approaches:

1. John the Ripper (JTR)
2. NetworkWalks Hash Calculator and Password Cracker

Both modules demonstrate how password hashes can be extracted and tested against password dictionaries to recover weak passwords.

---

## Module 1 – Password Cracking with John the Ripper (JTR)

### Objective

To recover the password of an encrypted PDF document using John the Ripper on Kali Linux.

### Tools Used

- Kali Linux
- John the Ripper
- PDF2John
- RockYou Wordlist
- Terminal

### Practical Implementation

**Step 1 – Verify John the Ripper**

Checked whether John the Ripper was installed:

```bash
which john
```

Output:

```text
/usr/sbin/john
```

**Step 2 – Locate PDF2John**

Located the PDF hash extraction script:

```bash
find /usr/share/john -iname '*pdf2john*'
```

Output:

```text
/usr/share/john/pdf2john.pl
```

**Step 3 – Extract PDF Hash**

Used PDF2John to extract the password hash from the encrypted PDF:

```bash
perl /usr/share/john/pdf2john.pl "My Locked PDF1.pdf" > hash1.txt
```

The extracted hash was saved in `hash1.txt`.

**Step 4 – Prepare RockYou Wordlist**

Initially, RockYou was available in compressed format.

Checked the wordlist directory:

```bash
ls -lh /usr/share/wordlists/
```

Extracted the compressed dictionary:

```bash
sudo gzip -dk /usr/share/wordlists/rockyou.txt.gz
```

**Step 5 – Perform Dictionary Attack**

Executed John the Ripper using the RockYou dictionary:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash1.txt
```

John successfully identified the matching password.

**Step 6 – Display Recovered Password**

```bash
john --show hash1.txt
```

### Result

**Recovered PDF Password:**

`good-luck`

**Captured Flag:**

`nw{cybersecurity_flag_captured_2608}`

The recovered password successfully unlocked the PDF, revealing the NetworkWalks congratulations page.

---

## Module 2 – Password Cracking with NetworkWalks Tools

### Objective

To extract a password-protected PDF hash and recover its password using NetworkWalks online tools.

### Tools Used

- NetworkWalks Hash Calculator
- NetworkWalks Password Cracker
- Google Chrome
- Password Dictionary

### Practical Implementation

**Step 1 – Open Hash Calculator**

Visited:

https://networkwalks.com/hash-calculator/

**Step 2 – Upload Encrypted PDF**

Uploaded the assigned PDF:

`My Locked PDF1 (for NW Tools Lab WK3-PM2).pdf`

The website identified the document as encrypted and generated a crackable PDF hash.

**Step 3 – Extract PDF Hash**

Copied the complete hash beginning with `$pdf$`.

**Step 4 – Open Password Cracker**

Visited:

https://networkwalks.com/password-cracker/

**Step 5 – Enter PDF Hash**

Pasted the extracted PDF hash into the Password Cracker input field.

Selected the built-in password dictionary containing 100 password candidates.

**Step 6 – Start Dictionary Attack**

Clicked the Start Cracking button.

The tool tested different password candidates against the supplied PDF hash.

**Step 7 – Recover Password**

The tool successfully identified a matching password.

### Result

**Recovered PDF Password:**

`password1`

**Captured Flag:**

`nw{networkwalks_flag1_jtr_270521_1}`

The recovered password successfully unlocked the PDF and displayed the NetworkWalks congratulations page.

---

## Technical Concepts Learned

### 1. Password Hashing

Hashing converts input data into a fixed-format representation. Password hashes can be tested against candidate passwords, but they cannot simply be reversed into plaintext.

### 2. Dictionary Attack

A dictionary attack tests passwords from a predefined wordlist against a password hash until a matching candidate is found.

### 3. John the Ripper

John the Ripper is a password auditing and recovery tool that supports multiple hash formats, including password-protected PDFs.

### 4. PDF2John

PDF2John extracts password hash information from encrypted PDF documents into a format that John the Ripper can process.

### 5. Password Security

The practical demonstrated why commonly used and predictable passwords are vulnerable to dictionary-based attacks.

---

## Final Results

| Project Module | Tool Used | Recovered Password | Status |
|---|---|---|---|
| W3-PM1 | John the Ripper | good-luck | Completed |
| W3-PM2 | NetworkWalks Tools | password1 | Completed |

### Captured Flags

**PM1:**
```text
nw{cybersecurity_flag_captured_2608}
```

**PM2:**
```text
nw{networkwalks_flag1_jtr_270521_1}
```

---

## Key Takeaways

- Learned how to extract password hashes from encrypted PDF files.
- Practiced dictionary-based password recovery.
- Gained hands-on experience with John the Ripper.
- Learned to use PDF2John for PDF hash extraction.
- Explored browser-based password recovery tools.
- Understood the importance of strong and unpredictable passwords.
- Successfully completed both essential Week 3 project modules.

## Conclusion

Successfully completed both essential modules of the Week 3 Password Cracking Project.

The practical exercises provided hands-on experience with password hash extraction, dictionary attacks, password recovery and PDF encryption.

This project improved my understanding of password security and demonstrated the importance of using strong passwords to protect sensitive documents.

**Project Status: COMPLETED**

**Training:** NetworkWalks Academy  
**Category:** Cybersecurity & Ethical Hacking  
**Week:** 3  
**Project:** Password Cracking with JTR and NetworkWalks Tools

---

*All testing was performed on the assigned training PDFs provided for this educational lab.*
