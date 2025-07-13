<img width="1024" height="1024" alt="071425" src="https://github.com/user-attachments/assets/c9824708-d046-430a-ad72-1844b5f4e865" />


# Universal Cyber Incident Taxonomy (UCIT)

The Universal Cyber Incident Taxonomy (UCIT) is a practical, open-source framework for labeling and classifying cyber incidents based on MITRE ATT&CK. It’s designed to provide clear, consistent short-form naming for security events—usable in real-time during detection and response, and structured enough to support long-term analysis and reporting.

Most existing frameworks (like those from CISA, DoD, or Verizon) suffer from vague categories, ambiguous overlap, or a lack of behavioral depth. UCIT was built from the ground up to fix that.

---

## 🔍 What Is UCIT?

UCIT uses a **trinomial naming convention** to describe incidents as objects:

(High-Level Category) – (Behavioral Technique) – (Compromise Level)


Each label reflects:

- **What kind of incident it is** (e.g., System Intrusion, Boundary Activity)
- **What the adversary was doing** (e.g., Credential Access, Discovery)
- **How much access they had** (User, Root, or Unknown)

It can be used during triage or investigation and is extended post-incident using a closeout **Final Observed Technique** field for complete granularity.

---

## 🧠 Why Use UCIT?

- Clear, structured incident labeling in plain English
- Based on the MITRE ATT&CK framework (tactic-level only)
- Designed for point-in-time triage and long-term metrics
- Flexible enough to be integrated into SIEMs, SOARs, or manual IR workflows
- Already tested against [100 realistic incident scenarios](docs/100-scenarios.csv)

---

## 🔧 How It Works

An example UCIT label:

System Intrusion – Credential Access – User

This tells you:
- The activity was **inside the environment**
- The behavior involved **stealing credentials**
- The adversary had **user-level access**

Once the investigation concludes, you can append a final technique:

Final Observed Technique: Exfiltration


---

## 📚 Documentation

| Section | Description |
|--------|-------------|
| [`docs/definitions.md`](docs/definitions.md) | Definitions for UCIT's core categories and structure |
| [`docs/usage-guide.md`](docs/usage-guide.md) | How to apply UCIT in a SOC environment |
| [`docs/mapping-examples/`](docs/mapping-examples.md) | Visual flowchart mappings selected from the 100 test scenarios |

---


## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 💬 Questions?

Open an issue or start a discussion in the [Discussions](https://github.com/CTI-Buddy/UCIT/discussions) tab.




