<img width="1280" height="640" alt="AI-B2B-Skill" src="https://github.com/user-attachments/assets/379b94da-54a3-4052-ae57-257342cdec28" />

# LinkedIn Cold Outreach: AI B2B Lead Research Skill for Claude

A Claude skill that studies **your LinkedIn profile**, works out what you can offer, and builds a researched, scored list of prospects who are likely to need your services. For the best prospects it drafts personalized outreach for you to review.

It is built for freelancers and consultants selling **Data Analytics & Engineering** (BI, ETL, Python, SQL) and **Workflow Automation** (n8n, AI agents, API integrations). You can adapt it to your own services.

> It does research and drafting only. It never sends connection requests, messages or emails on your behalf.

---

## Flow

```mermaid
flowchart TB
    START(["▶ Run /linkedin-cold-outreach"])

    subgraph S1["① UNDERSTAND YOU"]
        direction TB
        A1["👤 Read LinkedIn profile<br/>headline · About · experience<br/>skills · projects · posts"]
        A2["🧩 Map your services<br/>Data Analytics & Engineering<br/>Workflow & Business Automation"]
        A1 --> A2
    end

    subgraph S2["② FIND PROSPECTS"]
        direction TB
        B1["🎯 Target decision-makers<br/>Founders · CEOs · CTOs<br/>Heads of Data · Ops Managers"]
        B2["🔎 Research each prospect<br/>profile · company · size<br/>business model · need signals"]
        B1 --> B2
    end

    subgraph S3["③ QUALIFY & SCORE"]
        direction TB
        C1{"Clear business<br/>problem found?"}
        C2["📊 Score out of 100<br/>Relevance 30 · Problem 30<br/>Authority 20 · Company 10 · Access 10"]
        C1 -- "Yes" --> C2
    end

    subgraph S4["④ DELIVER"]
        direction TB
        D1["📋 Ranked lead table<br/>13 fields per lead"]
        D2["✉️ Outreach drafts<br/>connection note · follow-up<br/>offer · conversation starter"]
        D3(["🙋 You review & send manually"])
        D1 --> D2 --> D3
    end

    EXC["🚫 Excluded<br/>no problem or score below 40"]

    START --> S1 --> S2 --> S3
    C1 -- "No" --> EXC
    C2 -- "40 and above" --> S4

    classDef start fill:#1f6feb,stroke:#0b3d91,color:#ffffff,stroke-width:2px
    classDef step fill:#e8f1ff,stroke:#1f6feb,color:#0b2545,stroke-width:1.5px
    classDef decision fill:#fff4d6,stroke:#d29922,color:#4a3500,stroke-width:1.5px
    classDef out fill:#e3f8e9,stroke:#2da44e,color:#0b3d1c,stroke-width:1.5px
    classDef stop fill:#ffe5e5,stroke:#cf222e,color:#5c0a12,stroke-width:1.5px

    class START start
    class A1,A2,B1,B2,C2 step
    class C1 decision
    class D1,D2,D3 out
    class EXC stop

    style S1 fill:#f6f8fa,stroke:#8c959f,stroke-dasharray: 5 3
    style S2 fill:#f6f8fa,stroke:#8c959f,stroke-dasharray: 5 3
    style S3 fill:#f6f8fa,stroke:#8c959f,stroke-dasharray: 5 3
    style S4 fill:#f6f8fa,stroke:#8c959f,stroke-dasharray: 5 3
```

---

## Lead scoring

| Criterion | Points |
|---|---|
| Relevance to your services | 30 |
| Evidence of a business problem | 30 |
| Decision-making authority | 20 |
| Company and business opportunity | 10 |
| Accessibility and outreach potential | 10 |

| Score | Category |
|---|---|
| 80-100 | High priority |
| 60-79 | Potential |
| 40-59 | Low priority |
| Below 40 | Excluded |

## Output

Each lead comes back as a table row with: **Name, LinkedIn Profile, Job Title, Company, Company Website, Location, Industry, Opportunity, Business Pain Point, Reason to Approach, Suggested Service, Lead Score, Priority.**

High-priority leads also get a personalized connection request, a follow-up message, a suggested service offering and a conversation starter.

---

## How anyone can use this skill on their own Claude

```mermaid
flowchart TB
    START(["🌐 Find this repo on GitHub"])

    subgraph G1["① GET THE SKILL"]
        direction TB
        A1["⬇️ Option A: download<br/>linkedin-cold-outreach.skill"]
        A2["📦 Option B: Download ZIP or git clone,<br/>then zip the linkedin-cold-outreach folder"]
    end

    subgraph G2["② MAKE IT YOURS"]
        direction TB
        B1["✏️ Edit SKILL.md<br/>§1 your services<br/>§2 your target titles & pains<br/>§4 scoring weights"]
    end

    subgraph G3["③ INSTALL"]
        direction TB
        C1["🖥️ Claude web / desktop<br/>Settings → Capabilities → Skills<br/>→ Upload skill"]
        C2["⌨️ Claude Code<br/>copy folder to<br/>~/.claude/skills/"]
    end

    subgraph G4["④ RUN"]
        direction TB
        D1["🔗 Give Claude your LinkedIn profile<br/>browser access or paste your text"]
        D2["▶️ Type /linkedin-cold-outreach<br/>add region · industry · company size"]
        D1 --> D2
    end

    subgraph G5["⑤ ACT & IMPROVE"]
        direction TB
        E1["📋 Review ranked leads<br/>and outreach drafts"]
        E2["✉️ Edit and send manually on LinkedIn"]
        E3["🔁 Report what worked<br/>and re-run with a sharper target"]
        E1 --> E2 --> E3
    end

    START --> G1 --> G2
    G2 --> C1
    G2 --> C2
    C1 --> G4
    C2 --> G4
    G4 --> G5
    E3 -. "refine" .-> D2

    classDef start fill:#1f6feb,stroke:#0b3d91,color:#ffffff,stroke-width:2px
    classDef step fill:#e8f1ff,stroke:#1f6feb,color:#0b2545,stroke-width:1.5px
    classDef edit fill:#fff4d6,stroke:#d29922,color:#4a3500,stroke-width:1.5px
    classDef install fill:#f3e8ff,stroke:#8250df,color:#2d1352,stroke-width:1.5px
    classDef out fill:#e3f8e9,stroke:#2da44e,color:#0b3d1c,stroke-width:1.5px

    class START start
    class A1,A2 step
    class B1 edit
    class C1,C2 install
    class D1,D2 step
    class E1,E2,E3 out

    style G1 fill:#f6f8fa,stroke:#8c959f,stroke-dasharray: 5 3
    style G2 fill:#f6f8fa,stroke:#8c959f,stroke-dasharray: 5 3
    style G3 fill:#f6f8fa,stroke:#8c959f,stroke-dasharray: 5 3
    style G4 fill:#f6f8fa,stroke:#8c959f,stroke-dasharray: 5 3
    style G5 fill:#f6f8fa,stroke:#8c959f,stroke-dasharray: 5 3
```

### Step by step

**1. Get the skill**
Download the repo as a ZIP (Code -> Download ZIP) or run `git clone https://github.com/<your-username>/<repo-name>.git`.

**2. Make it yours (important)**
`SKILL.md` is written in the first person about one freelancer's services. Open it and change:

- **Section 1**: your own service areas.
- **Section 2**: the job titles and pain points you want to target.
- **Section 4**: the scoring weights, if your priorities differ.

**3. Install it**

*Claude web / desktop:*
1. Zip the `linkedin-cold-outreach` folder, with `SKILL.md` directly inside it.
2. Go to Settings -> Capabilities -> Skills -> Upload skill and select the zip.

*Claude Code:*
```bash
cp -r <repo-name>/linkedin-cold-outreach ~/.claude/skills/
```

**4. Connect your LinkedIn profile**
Either give Claude browser or web access so it can read your profile page, or paste your headline, About and Experience text into the chat. Do not share passwords.

**5. Run it**
```text
/linkedin-cold-outreach
Focus on founders and heads of operations at 20-200 person logistics
and e-commerce companies in the UK and UAE.
```

**6. Review and send**
Check the ranked table, verify the details yourself, edit the drafts and send them manually. The skill never contacts anyone for you.

**7. Iterate**
Tell Claude which messages got replies and re-run with a tighter region, industry or company size.

### Troubleshooting

| Problem | Fix |
|---|---|
| Skill doesn't appear after upload | Check that `SKILL.md` is directly inside the zipped folder, not nested deeper, and that its header has `name` and `description` |
| `/linkedin-cold-outreach` not recognised | Start a new chat after installing |
| Claude can't read your LinkedIn | LinkedIn often blocks automated reads, so paste your profile text instead |
| Leads look generic | Add a target region, industry and company size to your prompt |

## Built-in safeguards

- Accuracy over volume: no invented names, titles, companies or pain points.
- Verified facts are kept separate from assumptions.
- Only public, verifiable information is used.
- No duplicate prospects across a list.
- No messages, requests or commitments are made on your behalf.

Use outreach responsibly and follow LinkedIn's terms of service and the privacy and anti-spam rules where you operate.

## Repository layout

```text
.
├── README.md
└── linkedin-cold-outreach/
    └── SKILL.md
```
