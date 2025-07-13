# UCIT Usage Guide

The Universal Cyber Incident Taxonomy (UCIT) is a flexible, behavior-based system for classifying cyber incidents in a structured, consistent way. This guide provides practical instructions for applying UCIT in real-world environments, whether you're using it in a SIEM, ticketing system, or spreadsheet.

---

## 📌 When to Use UCIT

UCIT is designed to support both:
- **Point-in-time reporting** (initial detection, triage, early classification)
- **Final classification** (at investigation closeout or postmortem)

It can be applied:
- As part of an alert enrichment or ticketing workflow
- When generating dashboards, KPIs, or trend reports
- To normalize incident labels across teams or environments
- As a drop-in replacement for legacy category fields

---

## 🔧 The UCIT Label Format

Each UCIT label consists of **three components**:

(Incident Category) – (ATT&CK Technique) – (Compromise Level)


### Example:
System Intrusion – Credential Access – User


This tells you:
- The adversary had internal access (System Intrusion)
- Their behavior involved stealing credentials (Credential Access)
- They operated with user-level permissions (User)

---

## 🧩 Components Explained

### 1. Incident Category
Describes the nature and scope of the activity:
- **Boundary Activity** – Activity at the perimeter, before access is gained
- **System Intrusion** – Confirmed access or execution inside the environment
- **Noncompliance Activity** – Policy violations or risky configurations (not malicious)

See [`definitions.md`](./definitions.md) for full category descriptions.

---

### 2. ATT&CK Technique
Describes what the adversary is doing, using **MITRE ATT&CK TACTICS** (not sub-techniques):

Examples:
- Execution
- Credential Access
- Discovery
- Command and Control
- Impact

These tactics are well-known, standardized, and easily mappable from telemetry.

> ⚠️ Use only the ATT&CK **tactic name** (e.g., *Execution*), not the technique or sub-technique ID.

---

### 3. Compromise Level
Reflects the adversary’s observed level of access at the time of detection:
- **Root** – Admin, system-level, or domain-level access
- **User** – Standard user or session-level access
- **Unknown** – Access level unclear or cannot be confidently determined

Use “Unknown” conservatively but realistically when visibility is limited.

---

## ✅ Examples

| Detection Scenario | UCIT Label |
|--------------------|------------|
| Beaconing to known C2, no confirmed level of access yet | `Boundary Activity – Command and Control – Unknown` |
| Phishing email leads to RDP access with user creds | `System Intrusion – Initial Access – User` |
| EDR alert shows credential dumping from LSASS | `System Intrusion – Credential Access – Root` |
| User forwards sensitive data to personal Gmail | `Noncompliance Activity – Data Handling – User` |

---

## 📘 Optional: Final Observed Technique

Once an incident is closed, you should append a **Final Observed Technique** to show the full impact or end-state.

### Example:
Initial UCIT Label: System Intrusion – Execution – User
Final Observed Technique: Exfiltration


This helps differentiate early detections from what the attacker actually achieved and supports retrospective analysis and KPI development.

---

## 🎯 Best Practices

- **Apply UCIT as early as possible.** Labels help drive triage, escalation, and routing.
- **Don’t overthink access level.** If it’s not root/system, use “User.” If unsure, use “Unknown.”
- **Favor ATT&CK tactic-level terms.** This avoids overspecifying behavior before the investigation matures.
- **Use Final Technique to show closure.** It gives analysts a way to reflect what actually happened and a snapshot view of the entire detected kill-chain.

---

## 🔄 Integrating into Tools

You can incorporate UCIT into:
- SIEM platforms (as a normalized tag or lookup field)
- SOAR playbooks (auto-assign labels based on detection rules)
- Ticketing systems (ServiceNow, Jira, etc.)
- Post-incident reporting templates
- Threat intelligence platforms for IOC context

---

## 🧪 Testing and Validation

UCIT has been tested against [100 real-world scenarios](./mapping-examples/100-scenarios.csv), with side-by-side comparisons to DoD, CISA, and Verizon DBIR labels. These examples can be used as training data or for tuning detection-to-label logic.

---

## 💬 Need Help?

Open an issue or join the discussion in the [GitHub Discussions](https://github.com//CTI-Buddy/UCIT/discussion) tab.
