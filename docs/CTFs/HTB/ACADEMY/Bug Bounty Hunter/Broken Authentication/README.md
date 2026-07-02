# Broken Authentication

Vulnerabilities in authentication mechanisms that allow attackers to compromise accounts, bypass login, or impersonate other users.

## Common Vulnerabilities

| Vulnerability | Description |
|---------------|-------------|
| Weak passwords | No complexity requirements, default creds |
| No rate limiting | Enables brute force |
| Predictable tokens | Guessable session IDs or password reset tokens |
| Insecure "remember me" | Long-lived tokens stored insecurely |
| 2FA bypass | OTP reuse, missing validation, response manipulation |
| Username enumeration | Different response for valid vs invalid username |
| Password reset flaws | Predictable token, no expiry, host header injection |

## Username Enumeration

```bash
# Different responses reveal valid usernames
curl -s -o /dev/null -w "%{http_code} %{size_download}" http://target/login -d "user=admin&pass=wrong"
curl -s -o /dev/null -w "%{http_code} %{size_download}" http://target/login -d "user=invalid&pass=wrong"

# Timing differences
time curl -s http://target/login -d "user=admin&pass=wrong"
time curl -s http://target/login -d "user=notexist&pass=wrong"
```

## 2FA Bypass

```
1. Response manipulation: change {"success":false} to {"success":true}
2. Try OTP 000000–999999 if no rate limit (6-digit = 1M combos)
3. Reuse OTP from own account if same algorithm
4. Skip 2FA step entirely by jumping directly to post-2FA URL
5. Modify userId parameter during 2FA to another user
```

## Password Reset Attacks

```bash
# Host header injection → steal reset token
POST /reset-password HTTP/1.1
Host: attacker.com    # Token sent to this domain if not validated

# Predictable token
# token=base64(email+timestamp) → forge for any user

# Token not expiring → reuse old reset links from email
```

## Session Management Testing

```bash
# Decode JWT
echo "eyJ..." | base64 -d

# Test JWT none algorithm
header.payload.   # empty signature with alg:none

# Test session fixation
# 1. Get session before login
# 2. Login with session ID
# 3. Check if session ID remains the same
```
