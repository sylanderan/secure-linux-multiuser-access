# Secure Multi-User Linux Access

Configured a secure multi-user Linux environment on AWS EC2, implementing role-based access control and SSH hardening to eliminate password-based login vulnerabilities.

## What I Built

- Provisioned an AWS EC2 instance (Ubuntu 26.04) with a properly configured security group
- Created a new Linux user account with controlled, role-based sudo privileges
- Verified group membership and access levels to confirm least-privilege access
- Disabled password-based SSH authentication in the SSH daemon configuration
- Enforced SSH key-only authentication, restarting the SSH service to apply changes
- Verified the hardened configuration by testing key-based login from a fresh session

## Tech Stack

- AWS EC2
- Linux (Ubuntu) User & Group Management
- SSH / sshd_config
- Access Control (sudo, least privilege)

## Steps

### 1. User Creation
Created a new user account on the server:

\`\`\`bash
sudo adduser opsuser
\`\`\`

### 2. Role-Based Sudo Access
Granted controlled administrative privileges instead of full root access:

\`\`\`bash
sudo usermod -aG sudo opsuser
\`\`\`

Verified group membership:

\`\`\`bash
groups opsuser
\`\`\`

### 3. SSH Hardening
Edited the SSH daemon configuration to disable password login:

\`\`\`
# /etc/ssh/sshd_config
PasswordAuthentication no
\`\`\`

Restarted the SSH service to apply the change:

\`\`\`bash
sudo systemctl restart ssh
\`\`\`

### 4. Verification
Opened a fresh terminal session and connected using only the SSH key — confirming password authentication was fully disabled and the server was only accessible via key-based login.

## Screenshots

<img width="1920" height="1020" alt="Screenshot 2026-08-16 113731" src="https://github.com/user-attachments/assets/6ea08e9a-429a-4f11-b8c2-8ae2ba229e61" />
<img width="1920" height="1020" alt="Screenshot 2026-08-16 114119" src="https://github.com/user-attachments/assets/1efe8f93-d59e-42cc-bcfd-f77d590568d7" />
<img width="1920" height="1020" alt="Screenshot 2026-08-16 114317" src="https://github.com/user-attachments/assets/d37d4a86-8cd9-4b03-ba59-ff99662aea06" />

## What I Learned

Hands-on experience implementing Linux access control and SSH security hardening — core practices for securing production servers in cloud support and system administration roles.
