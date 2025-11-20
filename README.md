# 🔐 Linux IAM & Hardening — Ethical Hacking Mini Project  

---

## 🧩 Project Overview  
This project demonstrates the implementation #of a **secure IAM (Identity & Access Management)** model and basic **system hardening** techniques on a **Kali Linux (Debian-based)** virtual machine.  

The core objective was to design and apply a secure user, group, and permission policy, identify and remediate common system misconfigurations, and fully document all security improvements for auditing and compliance.

The detailed report, including the implementation steps, evidence of misconfiguration remediation (e.g., fixing world-writable directories and unrestricted `NOPASSWD` sudo entries), and final recommendations, is attached below and available via the provided GitHub link.

---

## 🎯 Objectives  
- Create users and groups with **least privilege access**  
- Apply **POSIX permissions + ACLs** on shared folders  
- Configure **sudoers** file with specific command-level control  
- Detect and fix **common misconfigurations**  
- Maintain **audit logs** for privileged changes  
- Produce a full **remediation report and checklist**

---

## ⚙️ Environment & Tools  
| Component | Description |
|------------|-------------|
| **OS** | Kali Linux (Debian-based) |
| **Tools Used** | `sudo`, `useradd`, `groupadd`, `chmod`, `chown`, `getfacl`, `visudo`, `tar`, `bash` |
| **Privileges** | Sudo required |
| **Audit** | Manual logging (`/var/log/manual_audit.log`) |

---

## 🧠 System Design
### 👥 Roles & Groups
| Role | Group | Users | Access Level |
|------|--------|--------|---------------|
| **Sysadmin** | `sysadmin` | `alice` | Limited sudo (system/user management) |
| **Developer** | `project` | `bob`, `carol` | Full read/write to `/srv/project` |
| **Auditor** | `auditor` | `dave` | Read-only access |

---

## 🛠️ Implementation
### Step 1: Clone and Run  
```bash
git clone https://github.com/<your-username>/linux-iam-hardening.git
cd linux-iam-hardening
chmod +x setup_iam_kali.sh
sudo ./setup_iam_kali.sh

This script will:
✅ Create groups (sysadmin, project, auditor)
✅ Create users (alice, bob, carol, dave)
✅ Apply ACLs and setgid on /srv/project
✅ Configure least-privilege sudoers entries
✅ Detect & fix 3 common security misconfigurations
✅ Log all actions to /var/log/manual_audit.log
✅ Generate evidence in ~/iam_project/evidence/

🧾 Evidence Collected

User & group listings (id, getent)

Folder ACLs (getfacl /srv/project)

Sudo privileges (sudo -l)

Permission fixes (ls -l /etc/passwd /etc/shadow)

Manual audit logs (/var/log/manual_audit.log)

| Issue                          | Description                        | Fix                                              |
| ------------------------------ | ---------------------------------- | ------------------------------------------------ |
| World-writable `/etc/cron.d`   | Allowed any user to edit cron jobs | `chmod 755 /etc/cron.d`                          |
| Unrestricted `NOPASSWD` sudo   | Allowed root without password      | Removed & replaced with command whitelisting     |
| Weak `/etc/passwd` permissions | World-readable sensitive data      | `chmod 644 /etc/passwd && chmod 600 /etc/shadow` |

| File                                             | Description                      |
| ------------------------------------------------ | -------------------------------- |
| `setup_iam_kali.sh`                              | Main automation script           |
| `baseline_policy.txt`                            | Role-based access control policy |
| `remediation_checklist.txt`                      | Security checklist               |
| `docs/report.txt`                                | Detailed report (plain text)     |
| `docs/slides_outline.txt`                        | Slide content for presentation   |
| `Linux_IAM_Hardening_Report_Lakshya_Borikar.pdf` | Final report (formatted PDF)     |

🧰 Recommended Improvements

Replace temporary passwords with SSH keys

Enable auditd for enterprise environments

Centralize logs to a SIEM platform

Review and update sudo rules monthly


**Author:** PRIYANSHU DEWANGAN
**Institute:** Rungta College of Engineering and Technology(R1) 
**Department:** Computer Science & Engineering(Artificial Intelligence & Machine Learning)
**Course:** Ethical Hacking Project  
**Submission:** November 2025

📜 License

This project is created for educational purposes only.
You may freely fork, reuse, and modify it for learning or demonstration.
