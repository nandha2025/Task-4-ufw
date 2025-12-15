

---

## 🚀 Steps Performed

### 1️⃣ Check and Enable UFW
- Verified current status and default policies, then enabled UFW.  
- Captured initial rules view: `screenshots/ufw_status_initial.png`.  

---

### 2️⃣ List Current Firewall Rules
- Displayed all existing rules with index numbers for easy management (add/remove).  
- This reflects the baseline ruleset before making changes.[file:1]  

---

### 3️⃣ Block Inbound Telnet (Port 23)
- Added a rule to **deny** inbound TCP connections on port **23** (Telnet).  
- Telnet is insecure because it sends credentials in clear text, so blocking it hardens the system.[file:1]  

Screenshot: `screenshots/ufw_deny_23.png`  

---

### 4️⃣ Test the Telnet Block Rule
- Attempted to connect to port 23 locally to verify that the firewall rule blocks access.  
- Connection reported as refused/filtered, confirming that the deny rule is effective.  

Screenshot: `screenshots/telnet_test_23.png`  

---

### 5️⃣ Allow SSH (Port 22)
- Created an **allow** rule for inbound SSH on port **22**, keeping secure remote access available.  
- Ensured the new SSH rule appears alongside the Telnet deny rule.  

Screenshot: `screenshots/ufw_allow_22.png`  

---

### 6️⃣ Remove the Telnet Block Rule (Restore State)

1. List rules with numbers:
2. Delete the Telnet deny rule by its index (example: `2`):
- Removed the temporary Telnet block rule to restore the firewall close to its original state, keeping only the desired rules (e.g., SSH allow).[file:1]  

Screenshot: `screenshots/ufw_after_delete_23.png`  

---

## 🔍 How UFW & Firewalls Filter Traffic

- A **firewall** inspects network packets and decides whether to **allow** or **block** them based on rules that match criteria such as IP address, port, and protocol.[file:1]  
- **UFW** is a user‑friendly frontend to Linux’s packet filtering (iptables/nftables), providing simple commands like `allow`, `deny`, and `delete` instead of complex raw rules.[file:1]  
- In this task, inbound rules were used to control what traffic can enter the system (e.g., blocking Telnet, allowing SSH), demonstrating basic host‑based firewall management.[file:1]  

---

## ✅ Outcome

By completing this task:

- Gained hands‑on experience managing firewall rules using UFW on Linux.[file:1]  
- Practiced blocking an insecure service (Telnet) and allowing a secure service (SSH).  
- Observed how rule changes directly affect real network connections through testing.  
