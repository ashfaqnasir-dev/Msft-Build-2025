# 🔌 Microsoft 365 Copilot: Connectors & Actions Guide (BRK167)

> **Overview:** Pichli videos mein humne dekha ke AI Agent kaise banate hain. Is session ka maqsad yeh hai ke Copilot ya Custom Agent ko sirf ek generic chatbot ke bajaye company ke data se jod kar practical kaam karne ke qabil banaya jaye.

---

## 🧠 Core Concept: Dimaag, Ilm aur Haath-Paanv

Ek smart enterprise AI assistant teen cheezon se complete hota hai:

| Component | Role | Tamsil (Analogy) | Misal |
| :--- | :--- | :--- | :--- |
| **Agent / Model** | Sochne aur faisla karne ki taqat | **Dimaag (Brain)** | GPT-4o / Semantic Kernel |
| **Connectors** | Bahir ke systems se data parhna | **Aankh aur Kaan (Knowledge)** | Jira, Salesforce, SQL DB |
| **Actions** | Asal system mein tabdeeli karna | **Haath aur Paanv (Tools)** | Ticket banana, Email bhejna, Calendar event create karna |

---

## 1. 🔗 Copilot Connectors (Knowledge Barhana)

### Concept
Aam taur par Copilot sirf Microsoft 365 ke internal data (Outlook, Teams, SharePoint) ko janta hai. Agar company ka data bahar ke systems (Jira, ServiceNow, Salesforce, SQL Database, ya custom wiki) mein para ho, toh Copilot wahan tak direct nahi pohnch sakta.

**Connectors** wo bridge (pul) hain jo bahir ke data ko Microsoft Graph Index ke sath sync kar dete hain, taake user jab bhi sawal kare, Copilot enterprise-wide authentic jawab de sake.

### 🛠️ How-To: Connectors Kaise Setup Karein

```
[External Data: Jira/SQL] 
       │
       ▼ (Graph Connector + Auth Keys)
[Microsoft Graph Index] 
       │
       ▼ (Grounding Context)
[M365 Copilot / Agent]
```

* **Step 1 (Portal Access):** Microsoft 365 Admin Center ya **Microsoft Graph Connectors Admin Portal** open karein.
* **Step 2 (Select Source):** **"Add a connector"** par click karein aur apna data source chunein (e.g., Salesforce, Jira, Confluence, Azure SQL, custom enterprise website).
* **Step 3 (Authentication & Security):** External system ki API credentials (OAuth / API keys) configure karein aur ACL (Access Control Lists) set karein taake employees ko sirf wahi data nazar aaye jiska unke paas permission ho.
* **Step 4 (Property Mapping & Crawl):** Define karein ke kon sa content index karna hai (e.g., ticket description, project status, author name) aur sync schedule set karein.
* **Natija (Result):** Jab user poochhega: *"Jira mein kal kaunse bugs high priority mark hue?"*, toh Copilot direct external Jira records se grounded answer provide karega.

---

## 2. ⚡ Actions & Plugins (Kaam Karwana)

### Concept
Data parhna (Read) ek pehlu hai, lekin data ke mutabiq asal system mein **Create, Update, ya Delete** action perform karna doosra pehlu hai. 

**Actions** Copilot ko power dete hain ke wo sirf text generating bot na rahe, balki APIs aur business workflows ko invoke karke system level par action execute kare.

### 🛠️ How-To: Actions Kaise Configure Karein

```
[User Prompt] 
       │ "Support ticket create karo..."
       ▼
[Copilot Studio: Intent Matching]
       │
       ▼ (Triggers & Input Extraction)
[Action: Power Automate Flow / REST API]
       │
       ▼ (Execution)
[Final Action Completed in System]
```

* **Step 1 (Open Copilot Studio):** **Microsoft Copilot Studio** portal mein apne agent ko open karein.
* **Step 2 (Add Action):** Left navigation panel se **"Actions"** (ya Plugins) tab par jayein aur **"Add an action"** select karein.
* **Step 3 (Integration Method):**
  * **Option A — Power Automate Flow (No-Code):** Pre-built template use karein (e.g., *Send notification*, *Approve request*, *Update row in Excel*).
  * **Option B — REST API / OpenAPI Specification (Pro-Code):** Apni company ke custom software ki API swagger file ya URL enter karein.
* **Step 4 (Triggers & Parameter Mapping):**
  * Model ko context dein ke yeh action kis intent par call hoga (e.g., *"Create new support incident"*).
  * System prompts aur parameters map karein (e.g., `ticketTitle`, `severityLevel`, `userEmail`).
* **Natija (Result):** User kahega: *"Mera laptop screen issue hai, ticket generate kardo."* Copilot details verify karega aur background API call karke ITSM tool mein actual ticket number generate kar ke user ko return karega.

---

## 📌 Executive Summary

```
                       ┌─────────────────────────┐
                       │  Agent Core (Reasoning) │
                       └───────────┬─────────────┘
                                   │
               ┌───────────────────┴───────────────────┐
               ▼                                       ▼
    ┌──────────────────────┐               ┌──────────────────────┐
    │  CONNECTORS (Inputs) │               │   ACTIONS (Outputs)  │
    │  - Read Only         │               │  - Write / Execute   │
    │  - Knowledge Bridge  │               │  - Trigger Workflows │
    │  - Graph Indexing    │               │  - REST APIs / Flows │
    └──────────────────────┘               └──────────────────────┘
```

1. **Connector:** Kaan aur Aankh — Bahar ka data safe tareeqay se Copilot ke knowledge base mein lata hai.
2. **Action:** Haath aur Paanv — Copilot ko real-world systems mein kaam karne aur changes lane ki taqat deta hai.