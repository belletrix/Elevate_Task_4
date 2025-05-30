
### 📄 **Setup and Use a Firewall on Windows/Linux**

---

#### 🔧 **Objective:**

To configure and test basic firewall rules on both **Windows** and **Linux** operating systems.

---

### 🐧 **Part A: Linux (Using UFW)**

#### ✅ Steps Performed:

1. **Enabled UFW:**

```bash
sudo ufw enable
```

2. **Checked Current Rules:**

```bash
sudo ufw status numbered
```

3. **Blocked Inbound Traffic on Port 23 (Telnet):**

```bash
sudo ufw deny 23
```

4. **Tested Telnet Block:**

```bash
telnet localhost 23
```

> Result: Connection refused or timeout (as expected)

5. **Allowed SSH Port 22 (For remote login):**

```bash
sudo ufw allow 22
```

6. **Deleted Test Rule (to restore state):**

```bash
sudo ufw delete deny 23
```

7. **Verified Final Rules:**

```bash
sudo ufw status
```

#### 📝 Explanation:

UFW is a front-end for `iptables` that simplifies firewall rule management. We added a rule to block port 23 (Telnet), tested it, and then removed the rule. The firewall filters traffic based on port, direction, and IP rules.

---

### 🪟 **Part B: Windows (Using Windows Defender Firewall)**

#### ✅ Steps Performed:

1. **Opened Firewall Interface:**

   * `Start → Windows Defender Firewall with Advanced Security`

2. **Created New Inbound Rule:**

   * Action: **New Rule → Port → TCP → 23 → Block the connection**
   * Applied to: Domain, Private, Public
   * Named: **Block Telnet Port 23**

3. **Tested Telnet Block:**

   * Opened **PowerShell as Administrator**
   * Installed Telnet (if not already installed):

     ```powershell
     dism /online /Enable-Feature /FeatureName:TelnetClient
     ```
   * Ran test:

     ```powershell
     telnet localhost 23
     ```
   * Expected result: **Connection failed** (rule successfully blocked it)

4. **Allowed SSH Port 22 (Optional for OpenSSH users):**

   * Similar steps as above but chose port 22 and **"Allow the connection"**

5. **Deleted the Block Rule (to restore defaults):**

   * Went to Inbound Rules → Right-clicked the rule → **Delete**

#### 📝 Explanation:

Windows Firewall uses inbound and outbound rules to manage traffic. We blocked port 23 to prevent Telnet access and verified the block using PowerShell.

---

### 📸 **Screenshots Attached:**

* Telnet Connection Attempt
* Windows Defender Firewall Inbound Rule
* PowerShell Telnet Test Result

---

### ✅ **Conclusion:**

Both Linux (UFW) and Windows Defender Firewall allow administrators to control traffic using rule-based systems. Blocking unnecessary ports like Telnet enhances system security.

