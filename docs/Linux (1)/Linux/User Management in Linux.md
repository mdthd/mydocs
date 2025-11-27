# User Management in Linux

A **user account** in Linux is an identity used to access and interact with the system. It defines permissions, ownership of files, and access to system resources.

## User Accounts Attributes

| Attribute | Location (Field/Line) | Description |
| --- | --- | --- |
| **Username** | `/etc/passwd` → **1st field** | Unique name identifying the user. |
| **User ID (UID)** | `/etc/passwd` → **3rd field** | Numeric identifier for the user. |
| **Group ID (GID)** | `/etc/passwd` → **4th field** | Primary group ID associated with the user. |
| **Supplementary Groups** | `/etc/group` → **lines where user appears** | Additional groups the user belongs to. |
| **Home Directory** | `/etc/passwd` → **6th field** | Default directory assigned to the user. |
| **Shell** | `/etc/passwd` → **7th field** | Default command-line interpreter (e.g., `/bin/bash`). |
| **Password (hashed)** | `/etc/shadow` → **2nd field** | Encrypted password for authentication. |
| **Account Expiry Date** | `/etc/shadow` → **8th field** | Date when the account becomes inactive. |
| **Password Expiry Date** | `/etc/shadow` → **5th field** | Date when the password must be changed. |
| **Minimum Password Age** | `/etc/shadow` → **3rd field** | Minimum days before password can be changed. |
| **Maximum Password Age** | `/etc/shadow` → **4th field** | Maximum days before password must be changed. |
| **Password Warning Period** | `/etc/shadow` → **6th field** | Days before expiry to warn user. |
| **Inactive Period** | `/etc/shadow` → **7th field** | Days after password expiry before account is disabled. |
| **Account Status** | `passwd -S` → **output status field** | Indicates if account is active or locked. |
| **Login History** | `last` → **lines per login event** | Records of user logins. |
| **Failed Login Attempts** | `faillog` → **per-user entry** | Tracks unsuccessful login attempts. |
| **Full Name (GECOS)** | `/etc/passwd` → **5th field** | User’s full name and optional info (comma-separated). |
| **Email Address** | GECOS or external systems | Can be manually added or managed via LDAP/email systems. |
| **Office Location** | `/etc/passwd` → **GECOS field (2nd item)** | Optional field for user’s office location. |
| **Work/Home Phone** | `/etc/passwd` → **GECOS field (3rd/4th items)** | Optional phone numbers. |
| **Custom Metadata** | LDAP or external identity systems | Additional attributes like department, title, etc. |