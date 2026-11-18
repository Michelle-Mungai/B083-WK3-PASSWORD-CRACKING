Password Cracking with JTR & NetworkWalks Tools

📌 Overview

This repository documents Week 3 of the Cybersecurity & Ethical Hacking Internship at Networkwalks Technologies (Batch B083), focused on password recovery techniques applied to encrypted PDF files.

Two distinct methodologies were used to achieve the same objective: a locally installed toolset (John the Ripper with the Johnny GUI) and a browser-based toolset developed by Networkwalks (Hash Calculator and Password Cracker). Both approaches follow the same underlying principle — extract the file's password hash, then run a dictionary attack against it.

Module	Topic	Tools Used
PM1	Password Cracking with JTR	John the Ripper (CLI), Johnny (GUI), online PDF hash extractor
PM2	Password Cracking with Networkwalks Tools	Networkwalks Hash Calculator, Networkwalks Password Cracker

🎯 Objectives

Understand the mechanics of password recovery tools and their reliance on password strength rather than encryption weaknesses
Extract a crackable hash from a password-protected PDF
Evaluate a locally installed CLI/GUI toolset against browser-based equivalents
Recover and validate the original password using both methodologies

🧩 Module 1: Password Cracking with JTR

Task 1 — Install and Configure John the Ripper & Johnny
By using Kali Linux, John the ripper is already found within the system. No extra installation required.

Task 2 — Extract the PDF Hash
The locked PDF was uploaded to an online hash extraction utility (pdf2john-equivalent) to generate a crackable hash.

Hashing Tool

Result: A $pdf$... formatted hash was extracted, compatible with both John the Ripper and hashcat.

Task 3 — Load the Hash and Execute the Attack
The hash was saved to a text file, imported into Johnny via Open password file (PASSWD format), and the attack was initiated.

Result: The hash was correctly identified as Format: PDF, and the password was recovered as good-luck.

🧩 Module 2: Password Cracking with Networkwalks Tools

Target file: My Locked PDF1.pdf

Task 1 — Extract the Hash via the Networkwalks Hash Calculator
The locked PDF was uploaded to the Networkwalks Hash Calculator, which parses files client-side and returns a crackable hash without any server upload.

Network Walks Hashing Tool

Result: A $pdf$... hash (pdf2john/hashcat-compatible) was generated entirely within the browser.

Task 2 — Load the Hash into the Networkwalks Password Cracker
The extracted hash was submitted to the Networkwalks Password Cracker, a browser-based dictionary attack utility.

Task 3 — Execute the Dictionary Attack
The attack was run against the tool's built-in 100-password wordlist.

Result: The password was recovered as 1qaz2wsx.

Task 4 — Verify by Unlocking the PDF
The recovered password was used to open the encrypted PDF in Adobe Acrobat Reader, confirming successful recovery.

Pdf Successfully Unlocked

🔍 Security Observations

Observation	Insight: 
Weak or common passwords are cracked within seconds	Dictionary attacks are highly effective against passwords present in common wordlists
PDF encryption strength is independent of password strength	The cryptographic algorithm is not compromised — only the password itself is guessed
Browser-based tools eliminate the installation barrier	The Networkwalks tools replicate John the Ripper's dictionary-attack logic entirely client-side, with no software installation required
GUI tools reduce technical entry barriers	Johnny enables password recovery workflows without requiring command-line proficiency.

📋 Verification Checklist: 
 John the Ripper (CLI) downloaded and configured
 Johnny (GUI) installed and linked to john.exe
 PDF hash extracted via JTR-compatible method
 Password recovered via Johnny
 PDF hash extracted via Networkwalks Hash Calculator
 Password recovered via Networkwalks Password Cracker
 Encrypted PDF successfully unlocked using recovered password

💡 What I Learned: 
This module reinforced that password recovery tools do not compromise encryption algorithms — they exploit weak or predictable passwords by testing candidate values against an extracted hash at high speed. Extracting the hash from the protected file, rather than attacking the file directly, is what makes offline cracking feasible.

Comparing the John the Ripper/Johnny workflow against the Networkwalks browser-based tools highlighted that the underlying methodology — hash extraction followed by a dictionary attack — remains consistent regardless of interface. Browser-based tools offer convenience and zero-installation accessibility, while the desktop toolset provides greater flexibility through larger wordlists, rule-based mangling, and GPU-accelerated cracking via hashcat. Ultimately, the exercise underscored that password strength, not encryption method, is the primary control against this class of attack.

🔗 Resources: 
Openwall — John the Ripper
Openwall — Johnny GUI
Networkwalks — Hash Calculator
Networkwalks — Password Cracker

Author: Michelle Mungai
