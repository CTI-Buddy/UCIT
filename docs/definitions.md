# UCIT Definitions

This document defines the key terms used in the Universal Cyber Incident Taxonomy (UCIT). These definitions are intended to support consistent labeling and reporting across incident response teams, tools, and workflows.


<img width="1359" height="758" alt="image" src="https://github.com/user-attachments/assets/33741271-1fee-4743-9dd4-a15f169cd9b5" />


---

## 📂 Top-Level Categories

### **Boundary Activity**
Activity observed at the perimeter of the organization’s environment, originating from external sources and interacting with systems or services before any confirmed internal access has been established.  These are specifically NOT attempts at system intrusion (which should be labelled as such).

**Examples:**
- Scanning or probing of public web services  
- Denial of service attacks  

---

### **System Intrusion**
Activity where an adversary has gained or is attempting to gain access to internal systems, accounts, or infrastructure. This includes any post-access behavior, such as execution, lateral movement, or data theft.

**Examples:**
- Successful phishing or credential abuse
- Password spray at a login portal
- Malware deployment or command and control traffic  
- Privilege escalation, persistence, or impact to operations  
- Data exfiltration from internal assets

---

### **Noncompliance Activity**
Security-relevant events not caused by malicious actors, but by failure to follow policy, configuration standards, or operational security practices. These still present risk but fall outside traditional attack behavior.  Further second-level categorization should be organization or policy specific, dependant on organizational needs.

**Examples:**
- Insecure storage or accidental exposure of data  
- Unauthorized use of unapproved tools  
- Systems with outdated patches or misconfigured controls  
- Deviations from organizational security policy

> ⚠️ Note: Noncompliance Activity is not evaluated against adversary techniques and was excluded from comparative testing. It is intended for organizational use as a flexible category aligned to internal governance.

---

## 📚 ATT&CK Technique Definitions (UCIT-Compatible)

These tactic-level descriptions are based on the MITRE ATT&CK framework and are used in UCIT as the behavioral middle layer of the trinomial naming structure.

---

### **Reconnaissance**
The adversary is trying to gather information they can use to plan future operations.

Reconnaissance consists of techniques that involve adversaries actively or passively gathering information that can be used to support targeting. Such information may include details of the victim organization, infrastructure, or staff/personnel. This information can be leveraged by the adversary to aid in other phases of the adversary lifecycle, such as using gathered information to plan and execute Initial Access, to scope and prioritize post-compromise objectives, or to drive and lead further Reconnaissance efforts.

---

### **Impact (Network or Endpoint Denial of Service)**
Impact consists of techniques that adversaries use to disrupt availability or compromise integrity by manipulating business and operational processes. Techniques used for impact can include destroying or tampering with data. In some cases, business processes can look fine, but may have been altered to benefit the adversaries’ goals. These techniques might be used by adversaries to follow through on their end goal or to provide cover for a confidentiality breach.

---

### **Initial Access**
Initial Access consists of techniques that use various entry vectors to gain their initial foothold within a network. Techniques used to gain a foothold include targeted spearphishing and exploiting weaknesses on public-facing web servers. Footholds gained through initial access may allow for continued access, like valid accounts and use of external remote services, or may be limited-use due to changing passwords.

---

### **Execution**
Execution consists of techniques that result in adversary-controlled code running on a local or remote system. Techniques that run malicious code are often paired with techniques from all other tactics to achieve broader goals, like exploring a network or stealing data. For example, an adversary might use a remote access tool to run a PowerShell script that does Remote System Discovery.

---

### **Persistence**
Persistence consists of techniques that adversaries use to keep access to systems across restarts, changed credentials, and other interruptions that could cut off their access. Techniques used for persistence include any access, action, or configuration changes that let them maintain their foothold on systems, such as replacing or hijacking legitimate code or adding startup code.

---

### **Privilege Escalation**
Privilege Escalation consists of techniques that adversaries use to gain higher-level permissions on a system or network. Adversaries can often enter and explore a network with unprivileged access but require elevated permissions to follow through on their objectives. Common approaches are to take advantage of system weaknesses, misconfigurations, and vulnerabilities.

---

### **Defense Evasion**
Defense Evasion consists of techniques that adversaries use to avoid detection throughout their compromise. Techniques used for defense evasion include uninstalling/disabling security software or obfuscating/encrypting data and scripts. Adversaries also leverage and abuse trusted processes to hide and masquerade their malware. Other tactics’ techniques are cross-listed here when those techniques include the added benefit of subverting defenses.

---

### **Credential Access**
Credential Access consists of techniques for stealing credentials like account names and passwords. Techniques used to get credentials include keylogging or credential dumping. Using legitimate credentials can give adversaries access to systems, make them harder to detect, and provide the opportunity to create more accounts to help achieve their goals.

---

### **Discovery**
Discovery consists of techniques an adversary may use to gain knowledge about the system and internal network. These techniques help adversaries observe the environment and orient themselves before deciding how to act. They also allow adversaries to explore what they can control and what’s around their entry point in order to discover how it could benefit their current objective. Native operating system tools are often used toward this post-compromise information-gathering objective.

---

### **Lateral Movement**
Lateral Movement consists of techniques that adversaries use to enter and control remote systems on a network. Following through on their primary objective often requires exploring the network to find their target and subsequently gaining access to it. Reaching their objective often involves pivoting through multiple systems and accounts. Adversaries might install their own remote access tools to accomplish Lateral Movement or use legitimate credentials with native network and operating system tools, which may be stealthier.

---

### **Collection**
Collection consists of techniques adversaries may use to gather information and the sources information is collected from that are relevant to following through on the adversary's objectives. Frequently, the next goal after collecting data is to either steal (exfiltrate) the data or to use the data to gain more information about the target environment. Common target sources include various drive types, browsers, audio, video, and email. Common collection methods include capturing screenshots and keyboard input.

---

### **Command and Control**
Command and Control consists of techniques that adversaries may use to communicate with systems under their control within a victim network. Adversaries commonly attempt to mimic normal, expected traffic to avoid detection. There are many ways an adversary can establish command and control with various levels of stealth depending on the victim’s network structure and defenses.

---

### **Exfiltration**
Exfiltration consists of techniques that adversaries may use to steal data from your network. Once they’ve collected data, adversaries often package it to avoid detection while removing it. This can include compression and encryption. Techniques for getting data out of a target network typically include transferring it over their command and control channel or an alternate channel and may also include putting size limits on the transmission.



---

## 🔐 Compromise Levels

### **Root**
The adversary has obtained administrative or system-level access on at least one affected system or account. This includes domain admin, root user, or full cloud tenancy control.

**Examples:**
- Compromised domain controller  
- Root shell access  
- Cloud global admin privileges

---

### **User**
The adversary has gained access using standard (non-privileged) credentials or accounts, such as employee logins or user-level system access.

**Examples:**
- User mailbox access  
- Workstation access via phishing  
- Access to shared network drives

---

### **Unknown**
The adversary’s level of access cannot be confidently determined based on current telemetry. This is common during early-stage triage or ambiguous detections.

**Examples:**
- Suspicious outbound traffic from unidentified host  
- Obfuscated script execution with unclear privilege context  
- Detection on asset with missing visibility

---

## 📊 Incident Status Values

### **Open**
The incident is currently being investigated. The UCIT label reflects what is known at the time of triage and may be updated as the investigation progresses.

---

### **Closed**
The incident investigation is complete. No further action is required. The UCIT label is considered final, and the record may optionally include a **Final Observed Technique** field.

---

### **Benign**
After investigation, the activity was determined to be non-malicious. This includes false positives, internal testing, or other harmless behavior.

---

### **Unsuccessful**
The adversary attempted malicious action but failed to gain access or achieve an objective. No system compromise or meaningful impact occurred.

**Examples:**
- Failed login attempts  
- Exploit blocked by endpoint protection  
- Network scan dropped at perimeter firewall

---

For examples and usage, see [usage-guide.md](./usage-guide.md) or explore the [100-scenario dataset](./mapping-examples/100-scenarios.csv).
