# ðADVANCED 03: Broken Authentication via Targeted SQL Injection

## ðGoal
Bypass the login form to gain unauthorized administrator access, proving a **Broken Authentication** vulnerability.

## ðMethodology
Due to tool and proxy interference, the attack pivoted from using Burp Suite to using the **Browser Developer Console** to manually send the API request containing the malicious payload. This isolated the attack from environmental factors.

### Key Steps
1.  **Target:** POST request to `/rest/user/login`.
2.  **Exploitation Method:** Fetch API call executed in the browser console.
3.  **Payload:** Targeted SQL Injection to bypass the password check for a known user:
    * **Email:** `admin@juice-sh.op'--`
    * **Mechanism:** The `'` closes the email string, and the `--` comments out the mandatory password verification clause in the backend query.

---

## ðKey Findings

### 1. Successful Login Bypass
The application executed the payload and returned a successful authentication response (`status: true`), along with a **JSON Web Token (JWT)** for the session.

### 2. Information Disclosure
The successful response confirmed the user's details, including the email: **`umail: admin@juice-sh.op`**.

### 3. Impact
* **Severity:** **Critical**
* **Risk:** Complete system compromise is possible. Any attacker can gain full administrator privileges without credentials, leading to data theft, modification, and denial of service.

---
