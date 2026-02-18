# Password Cracking Report - Phase 2

## Cracked Passwords (6)

| Username | Password | Hash |
|----------|----------|------|
| whatsupdoc@looneytunes.tv | carrots123 | a0e8402fe185455606a2ae870dcbc4cd |
| doh@springfieldpower.net | donuts4life | d730fc82effd704296b5bbcf45f323e |
| darkknighthot@mathamath.org | iamvengeance | 735f7f5e652d7697723893e1a5c04d90 |
| iamyourfather@deathstar.gov | darkside42 | 706ab9fc256efafb4cb4cf9d31ddc8eb |
| genius@starkindustries.com | iamironman | d50ba4dd3fe42e17e9fa9ec29f89708 |
| whysoserious@gothamchaos.net | chaos123! | f158d479ee181aac68b000a60e7a3d7a |

**Method**: Dictionary attack with rockyou.txt wordlist

## Conceptual Questions

### Q1: Difference between Dictionary and Non-Dictionary attacks
**Dictionary attack**: Uses a pre-compiled wordlist of common passwords. Fast but limited to words in the list.
**Non-dictionary attack**: Tries all possible character combinations. Slower but guaranteed to find the password eventually.

### Q2: Advantages of database access
- Offline cracking without rate limits or account lockouts
- Can use powerful hardware (GPUs) for faster cracking
- Knows exact usernames to target
- Can identify password reuse across accounts

### Q3: Benefits of longer passwords
- Exponentially more combinations
- Resists brute-force attacks
- Less likely to appear in dictionary wordlists
- Protects against rainbow table attacks
