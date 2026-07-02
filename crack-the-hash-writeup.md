# TryHackMe – Crack the Hashes Walkthrough

This writeup covers both levels of the **Crack the Hashes** room. I solved all hashes using **hashes.com** – a fast online hash resolver that gave me instant results.  
Below I also explain the **traditional method** using hashcat for each hash type, in case you want to understand the underlying process.

---

# Traditional Method (hashcat)

Normally, you would identify the hash type and then run hashcat with the appropriate mode and wordlist:


Example for MD5
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt

For SHA1
hashcat -m 100 -a 0 hash.txt rockyou.txt

For SHA256
hashcat -m 1400 -a 0 hash.txt rockyou.txt

For bcrypt
hashcat -m 3200 -a 0 hash.txt rockyou.txt

For SHA512crypt ($6$)
hashcat -m 1800 -a 0 hash.txt rockyou.txt

For SHA1 with salt (hash:salt)
hashcat -m 110 -a 0 hash.txt rockyou.txt
This can take a long time depending on the wordlist and hardware.
To save time, I used hashes.com – it resolves common hashes in seconds.

Level 1 – Solved Hashes
Hash	Type	Answer
1	48bb6e862e54f2a795ffc4e541caed4d	MD5	easy
2	CBFDAC6008F9CAB4083784CBD1874F76618D2A97	SHA1	password123
3	1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032	SHA256	letmein
4	$2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom	bcrypt	bleh
5	279412f945939ba78ce0758d3fd83daa	MD5	Eternity22

Level 2 – Solved Hashes
Hash	Type	Answer
6	F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85	SHA256	paule
7	1DFECA0C002AE40B8619ECF94819CC1B	MD5	n63umy8lkf4i
8	$6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.	SHA512crypt (Unix)	waka99
9	e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme	SHA1 (with salt)	481616481616

Notes
All hashes were resolved using hashes.com – it’s a great time‑saver for CTF challenges.

For hash #9, the format is hash:salt – it's a salted SHA1.

Always verify the hash type before attempting to crack it (use tools like hashid or hash-identifier).

