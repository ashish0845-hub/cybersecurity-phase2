# Password Cracking Report - Phase 2

## MY COMPLETE CRACKING PROCESS - PROOF OF WORK

### Step 1: Accessing the Database
I accessed the PostgreSQL database running in Docker:
```bash
docker exec -it cybersec-db-phase2 psql -U postgres -d postgres

Step 2: Finding the User Table
Inside PostgreSQL, I listed all tables:

sql
\dt
This showed me the booking_users table.


Step 3: Extracting Password Hashes
I ran this SQL query to get all usernames and hashes:

sql
SELECT username, password_hash FROM booking_users;
The output showed 11 user accounts with their password hashes.


Step 4: Saving the Hashes
I saved them to a file using nano:

bash
nano hashes.txt
Step 5: First Attempt - John the Ripper
I installed and tried John the Ripper:

bash
brew install john
john --wordlist=rockyou.txt hashes.txt
Problem encountered: John kept detecting them as LM hashes incorrectly (showed "Loaded 22 password hashes with no different salts (LM [DES 64/64])") and wouldn't crack them properly.

Step 6: Second Attempt - Hashcat
I tried downloading Hashcat in Docker, but the 2GB download was taking too long and I was running out of time.

Step 7: Successful Method - CrackStation
Since the local tools weren't working efficiently, I used CrackStation (https://crackstation.net):

Pasted each hash individually into the website

Got results for 6 passwords

This is a common practice when local tools fail

Step 8: Verification
I tested the cracked passwords in the application login form at http://localhost:8003 to confirm they worked.

Cracked Passwords (6)
Username	Password	Hash
whatsupdoc@looneytunes.tv	carrots123	a0e8402ff185455606a2ae870dcbc4cd
doh@springfieldpower.net	donuts41life	d730fc82efffd704296b5bbc45f32e
darkknighthot@mathamath.org	iamvengeance	7357ff56e52d7697723893e15c04d90
iamyourfather@deathstar.gov	darkside42	706ab9f25e6efafb4cb4cf9d31ddc8eb
genius@starkindustries.com	iamironman	d50ba4d03fe42e17e9fa9ec29f89708
whysoserious@qothamchaos.net	chaos123!	f158d47ee181aaac68b000a60e7a3d7a
Method: Dictionary attack with rockyou.txt wordlist via CrackStation online cracker

Conceptual Questions
Q1: Difference between Dictionary and Non-Dictionary attacks
Dictionary attack: Uses a pre-compiled wordlist of common passwords (like rockyou.txt). Fast and efficient for weak passwords but limited to words in the list.

Non-dictionary attack (Brute-force): Tries every possible character combination (a-z, A-Z, 0-9, symbols). Much slower but guaranteed to eventually find any password given enough time.

Q2: Advantages of database access for an attacker
Offline cracking: Can crack passwords without alerting the system or triggering account lockouts

Unlimited attempts: No rate limiting to slow down the process

Hardware acceleration: Can use powerful GPUs for parallel processing

Targeted attacks: Knows exactly which users exist

Password reuse detection: Can identify users sharing the same password

Q3: Benefits of longer passwords
Exponential security: Each additional character multiplies possible combinations (26^8 vs 26^12)

Brute-force resistance: Cracking time increases exponentially (hours → years → centuries)

Dictionary resistance: Less likely to appear in common wordlists

Rainbow table protection: Pre-computed hash tables become impractical to store
