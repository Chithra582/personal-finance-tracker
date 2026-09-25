# Personal Finance Tracker — AI Financial Planning & Portfolio Agent

![HiDevs GitAgent Passport](https://img.shields.io/badge/HiDevs-GitAgent%20Passport-blueviolet?style=flat-square)
![OpenGAP](https://img.shields.io/badge/OpenGAP-v0.1.0-blue?style=flat-square)
![License](https://img.shields.io/badge/license-GPL--3.0-green?style=flat-square)
![Agent](https://img.shields.io/badge/agent-personal--finance--tracker--agent-orange?style=flat-square)

An autonomous **Personal Finance and Portfolio Management Intelligence Agent** built with Python, wxPython, and modular storage engines (`CJS`).

The agent ingests local transaction ledgers, classifies expenses across standardized economic categories, evaluates stock asset allocations, projects cash flow trajectories, and computes savings velocity—all while guaranteeing local-first data sovereignty with zero cloud retention.

---

## Key Capabilities

| Capability | Purpose |
|---|---|
| **Expense & Budget Analysis** | Categorizes debit transactions, calculates monthly burn velocity, and monitors category budget limits. |
| **Investment Portfolio Tracking** | Audits equity holdings, computes unrealized capital gains/losses, and flags asset concentration risks. |
| **Cash Flow Forecasting** | Projects forward net savings over 3, 6, and 12-month horizons and calculates emergency fund adequacy. |
| **Ledger Serialization Auditing** | Validates multi-format data persistence (CSV, JSON, Shelve DB) with deduplication and schema integrity. |

---

## Tech Stack

- **Desktop Framework**: Python 3 & wxPython
- **Storage & Serialization**: CSV, JSON, and Python Shelve DB via `CJS`
- **Protocol**: OpenGAP Specification v0.1.0

---

## Repository Structure

```text
personal-finance-tracker/
├── agent.yaml                 # OpenGAP spec 0.1.0 root definition
├── SOUL.md                    # Core fiduciary persona, cent-level exactitude, local data sovereignty
├── EXPLAINABILITY.md          # 5-section transparency report satisfying Checkpoint 2
├── RULES.md                   # Immutable boundaries (MUST ALWAYS / MUST NEVER)
├── DUTIES.md                  # Segregation of duties (Maker, Executor, Checker, Auditor)
├── README.md                  # Comprehensive documentation with GitAgent Passport badges
├── fintrack.py                # Main desktop application runner
├── settings.py                # User application settings & configuration
├── functions/
│   ├── cjs.py                 # Multi-format CSV/JSON/Shelve serialization engine
│   └── funcs.py               # Financial utility helpers
├── model/
│   └── stocklist.py           # Equity portfolio valuation model
├── gui/                       # wxPython interface components
├── skills/
│   ├── expense-budget-analyzer/SKILL.md
│   ├── investment-portfolio-tracker/SKILL.md
│   ├── cash-flow-forecaster/SKILL.md
│   └── ledger-serialization-auditor/SKILL.md
└── tools/
    ├── expense-analyzer.yaml
    ├── portfolio-evaluator.yaml
    ├── cashflow-projector.yaml
    └── ledger-auditor.yaml
```

---

## Run Locally

1. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
2. **Start the Desktop Application**:
   ```bash
   python fintrack.py
   ```

---

## HiDevs GitAgent Passport Submission

- **Portal**: [HiDevs GitAgent Passport](https://app.hidevs.xyz/passport/submit)
- **Repository**: `Chithra582/personal-finance-tracker`
- **Category**: **Finance**
