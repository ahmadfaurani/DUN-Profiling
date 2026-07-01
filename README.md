# DUN Profiling V1 Workflow

**Three-Dimensional Constituency Intelligence for Johor PRN 2026**

---

## 📋 Overview

This repository contains the complete documentation for the **DUN Profiling V1** workflow — a validated, production-ready methodology for generating comprehensive political intelligence packages for Johor State Election (PRN) 2026.

**Workflow Status:** ✅ Production  
**Version:** 1.0  
**Last Updated:** 2026-07-01  
**Classification:** TLP:AMBER

---

## 🗳️ What is DUN Profiling V1?

DUN Profiling V1 is a **five-step analytical workflow** that transforms raw electoral data into actionable operational guidance for war room teams:

```
Step 1: Demographics → PD-level voter composition (SPR XLSX)
Step 2: Candidates   → Candidate profiles + demographic alignment (News + Nominations)
Step 3: Historical   → Voting patterns + swing analysis (ElectionData.MY)
Step 4: Synthesis    → Master operational brief (Integrated guidance)
Step 5: GitHub Upload → Private repository with structured workspace
```

**Output:** 4 intelligence briefs per constituency (Demographic, Candidate, Historical, Master Operational)

---

## 📁 Repository Structure

| Directory / File | Description |
|------------------|-------------|
| `README.md` | This file — workflow overview and quick start |
| `WORKFLOW-PROMPTS.md` | Detailed prompts for each of the 5 steps |
| `WORKFLOW-SCHEMA.md` | Input/output schemas, data structures, validation rules |
| `CONFIG.md` | Configuration options, environment variables, deployment settings |
| `EXAMPLES.md` | Real-world examples from completed constituencies (N27 Layang-Layang) |

---

## 🚀 Quick Start

### Prerequisites

1. **GitHub CLI** authenticated with `repo` scope
2. **SPR Electoral Roll XLSX** files for target constituencies
3. **ElectionData.MY API key** (https://electiondata.my/console)
4. **OpenClaw** installed and configured

### Execution Modes

#### Mode 1: Manual (Current Production)
```bash
# Execute each step via OpenClaw agent session
openclaw skill run dun-profiling-step1 --spr-xlsx <path> --code N16 --name "Sungai Balang"
openclaw skill run dun-profiling-step2 --code N16 --news-sources "..."
openclaw skill run dun-profiling-step3 --code N16 --api-key ${ELECTIONDATA_API_KEY}
openclaw skill run dun-profiling-step4 --demographic-brief <path> --candidate-brief <path> --historical-brief <path>
openclaw skill run dun-profiling-step5 --brief-files <paths> --github-token ${GITHUB_TOKEN}
```

#### Mode 2: Semi-Automated (Planned)
```bash
python tools/dun-profiling/run-single.py --code N16 --spr-xlsx <path> --api-key ${ELECTIONDATA_API_KEY}
```

#### Mode 3: Fully Automated (Future)
```bash
python tools/dun-profiling/run-batch.py --constituencies N16,N17,N27 --parallel 3
```

---

## ✅ Completed Constituencies

| Constituency | Code | Parliament | Status | Completed Date |
|--------------|------|------------|--------|----------------|
| Layang-Layang | N27 | P149 | ✅ Full (5 steps) | 2026-07-01 |
| Sungai Balang | N16 | P146 | ✅ Partial (4 steps) | 2026-06-27 |
| Semerah | N17 | P147 | ✅ Partial (4 steps) | 2026-06-27 |
| Endau | N32 | P154 | ✅ Partial (4 steps) | 2026-06-29 |

---

## 🔍 Core Truth Validation System (CVS)

All outputs pass mandatory CVS validation:

| Requirement | Application |
|-------------|-------------|
| **Multi-Source Verification** | Tier 1 claims (numbers, names, dates) require ≥2 independent sources |
| **Confidence Assertion Tags** | All analytical claims tagged: [HIGH] / [MEDIUM] / [LOW] |
| **Speculation Demarcation** | All predictive claims flagged: `SPECULATION:` or `SCENARIO:` |
| **Conflict Resolution** | Disagreements tagged [CONFLICTING], both values shown |
| **Validation Gate** | All output must pass: `./tools/truth-validator/validate.sh <output>.md` |

---

## 📊 Workflow Performance

| Metric | Target | Current |
|--------|--------|---------|
| Time per constituency (manual) | <2 hours | ~2 hours |
| Time per constituency (automated) | <25 minutes | N/A (not built) |
| CVS compliance rate | 100% | 100% (completed seats) |
| Brief document completeness | 100% | 100% (4/4 seats) |

---

## 🔒 Access Control

**Repository Visibility:** Private  
**TLP Marking:** TLP:AMBER — Distribution limited to war room team only.

**Collaborators:**
- Add war room team members via GitHub Settings → Collaborators

---

## 📚 Documentation Index

| Document | Purpose |
|----------|---------|
| [WORKFLOW-PROMPTS.md](./WORKFLOW-PROMPTS.md) | Step-by-step prompts for execution |
| [WORKFLOW-SCHEMA.md](./WORKFLOW-SCHEMA.md) | Technical schemas and validation rules |
| [CONFIG.md](./CONFIG.md) | Configuration and deployment guide |
| [EXAMPLES.md](./EXAMPLES.md) | Real-world output examples |

---

## 🆘 Support

**Issues:** Report workflow issues, documentation gaps, or CVS validation failures  
**Maintenance:** Political Intelligence Team  
**Next Review:** 2026-07-15

---

**Workflow Owner:** Political Intelligence Team  
**Classification:** TLP:AMBER  
**CVS Status:** ✅ Validated
