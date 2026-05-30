# Documents — Machine Learning

This folder holds all design and learning documents for every ML algorithm and concept.
Dual purpose: **learning mastery** and **interview preparation**.

---

## Folder Structure

```
documents/
├── fdd/          ← Functional Design Documents   (Owner: Product Owner Agent)
├── tdd/          ← Technical Design Documents    (Owner: Architect Agent)
├── interview/    ← Interview Q&A Documents       (Owner: Tech Interviewer Agent)
└── learning/     ← Learning Notes & Experiments  (Owner: Dev Data Agent)
```

---

## Document Types

| Type      | Folder       | Owner              | Purpose                                              |
|-----------|--------------|--------------------|------------------------------------------------------|
| FDD       | `fdd/`       | Product Owner      | What the algorithm does, when to use it, use cases   |
| TDD       | `tdd/`       | Architect          | How it works, math, implementation design            |
| Interview | `interview/` | Tech Interviewer   | Interview Q&A, common questions, key points          |
| Learning  | `learning/`  | Dev Data Agent     | Learning notes, experiments, code insights           |

---

## File Naming Convention

```
{TOPIC_ID}_{algorithm_name}_{doc_type}.md
```

### Examples
```
SL001_linear_regression_fdd.md
SL001_linear_regression_tdd.md
SL001_linear_regression_interview.md
SL001_linear_regression_learning.md
```

### Topic ID Reference

| Prefix | Category                |
|--------|-------------------------|
| MF     | ML Foundations          |
| SL     | Supervised Learning     |
| UL     | Unsupervised Learning   |
| DL     | Deep Learning           |
| RL     | Reinforcement Learning  |

---

## Document Creation Order (per algorithm)
1. FDD — Product Owner writes the functional perspective first
2. TDD — Architect writes the technical design based on FDD
3. Learning — Dev Data/Model adds notes during implementation
4. Interview — Tech Interviewer creates Q&A after learning is complete
