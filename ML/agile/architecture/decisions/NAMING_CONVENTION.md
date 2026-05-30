# 🏗️ Naming Convention — Owned by Architect Agent

---

## 1. Worklog File Naming Convention

All worklog files across all agents must follow this format:

```
YYYYMMDD_HHMMSS_subject.md
```

| Part    | Format     | Example          |
|---------|------------|------------------|
| Date    | YYYYMMDD   | 20260530         |
| Time    | HHMMSS     | 143000           |
| Subject | snake_case | project_kickoff  |
| Ext     | .md        | .md              |

**Example:**
```
20260530_143000_project_kickoff.md
20260530_160000_linear_regression_session.md
```

---

## 2. Document File Naming Convention

All documents in `documents/` must follow this format:

```
{TOPIC_ID}_{algorithm_name}_{doc_type}.md
```

| Part          | Example             | Options                          |
|---------------|---------------------|----------------------------------|
| TOPIC_ID      | SL001               | MF, SL, UL, DL, RL + number     |
| Algorithm     | linear_regression   | snake_case                       |
| Doc Type      | fdd                 | fdd / tdd / interview / learning |

**Examples:**
```
SL001_linear_regression_fdd.md
SL001_linear_regression_tdd.md
SL001_linear_regression_interview.md
SL001_linear_regression_learning.md
UL004_pca_tdd.md
DL001_ann_interview.md
```

---

## 3. Topic ID Reference

| Prefix | Category                | ID Range |
|--------|-------------------------|----------|
| MF     | ML Foundations          | MF001–MF006 |
| SL     | Supervised Learning     | SL001–SL009 |
| UL     | Unsupervised Learning   | UL001–UL006 |
| DL     | Deep Learning           | DL001–DL005 |
| RL     | Reinforcement Learning  | RL001–RL003 |

---

## 4. Worklog Folder Structure

```
agile/worklogs/
├── architect/
├── product_owner/
├── scrum_master/
├── dev_data/
├── dev_model/
├── dev_mlops/
├── tech_interviewer/
└── learn/
    ├── ml_foundations/
    ├── supervised_learning/
    ├── unsupervised_learning/
    ├── deep_learning/
    └── reinforcement_learning/
```

---

## 5. Worklog File Template

```markdown
# [Agent Name] — Work Log
## Date: YYYY-MM-DD
## Time: HH:MM:SS
## Subject: [subject]

### What Was Done
-

### Decisions Made
-

### Pending / Next Steps
-
```

---

## 6. Rules (Enforced by Scrum Master)
- One file per session per agent
- File name must match date/time of session
- Subject must be short and descriptive (max 4 words, snake_case)
- No vague subjects like `misc` or `work`
- Documents must follow `{TOPIC_ID}_{algorithm_name}_{doc_type}.md` format

---
*Defined by: Architect Agent | Updated: 2026-05-30*
