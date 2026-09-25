# EXPLAINABILITY — Personal Finance Tracker Agent

> **Admissibility & Transparency Report for OpenGAP / Agent Passport**  
> *Agent Name:* Personal Finance Tracker Agent (`personal-finance-tracker-agent`)  
> *Specification:* OpenGAP v0.1.0  
> *Domain:* Finance / Personal Financial Planning & Portfolio Analytics  

---

## 1. Overview & Fiduciary Purpose

Personal Finance Tracker Agent is an autonomous wealth management and budgeting copilot developed for individuals tracking personal cash flows, bank transactions, and investment holdings. The underlying desktop application uses Python, wxPython, and modular storage engines (`CJS`) to ingest CSV spreadsheets, JSON records, and local Shelve databases.

The agent's primary purpose is to provide transparent, unbiased financial guidance without requiring users to link external bank credentials or store sensitive ledgers in third-party clouds. By reconciling transaction streams, categorizing spending, and evaluating asset allocations, the agent converts raw financial rows into actionable budgeting advice and net worth milestones.

---

## 2. How the Agent Decides (Decision-Making Logic)

Personal Finance Tracker Agent operates across a deterministic four-stage financial planning pipeline:

```
[Local CSV / JSON / DB Ledger] ──> [Schema & Transaction Parsing] ──> [Category & Cash Flow Audit]
                                                                                     │
                                                                                     ▼
[Budgeting Advice & Wealth Report] <── [Prudence & Safety Gate] <── [Portfolio Valuation & Yields]
```

### 2.1 Transaction Ingestion & CJS Serialization Validation
- **Decision:** Validates whether incoming transaction records conform to standard debit/credit schemas.
- **Rules:**
  - Verifies date formats, currency decimal precision, and non-empty payee/category descriptors.
  - Detects duplicate transaction entries based on identical timestamp, amount, and memo fingerprints.

### 2.2 Category Classification & Expense Velocity Evaluation
- **Decision:** Groups transactions into standardized economic buckets (Housing, Utilities, Food, Transportation, Healthcare, Discretionary).
- **Rules:**
  - Computes monthly expenditure run rates and burn velocity.
  - Flags category expenditures exceeding user-defined budget thresholds by > 10%.

### 2.3 Stock Portfolio Valuation & Asset Allocation Analysis
- **Decision:** Evaluates investment assets and portfolio diversification.
- **Rules:**
  - Calculates cost basis, current market values, and unrealized capital gains/losses.
  - Assesses asset distribution (equities vs. cash reserves) and flags over-concentration (> 25% in a single ticker).

### 2.4 Cash Flow Forecasting & Financial Safety Gate
- **Decision:** Projects net savings trajectory over 3, 6, and 12-month forward horizons.
- **Rules:**
  - Enforces emergency fund prioritization (maintaining 3 to 6 months of fixed living expenses in liquid reserves).
  - Assesses debt-servicing ratios and warns against deficit spending before allocating funds to speculative investments.

---

## 3. Data Sources & Inputs Used

| Data Input | Source | Purpose | Data Handling & Privacy |
|---|---|---|---|
| **Transaction Ledgers** | Local CSV files / SQLite / Shelve DB | Transaction history, dates, amounts, payees, and categories | Stored strictly on local device; read-only memory ingestion; zero cloud egress |
| **Stock Holdings** | User-entered stocklist (`model/stocklist.py`) | Share quantities, purchase dates, buy prices, ticker symbols | Maintained in local application state; evaluated in memory |
| **User Budget Targets** | Settings / user configuration (`settings.py`) | Monthly budget limits per category and savings goals | Local configuration file; not shared with external endpoints |
| **User Query Prompts** | Natural language interface | Requests for budget summaries, spending trends, or savings forecasts | Processed ephemerally; discarded post-response |

Personal Finance Tracker Agent complies with financial privacy standards:
- **Zero Cloud Retention:** Ledgers, bank account identifiers, and net worth numbers are never transmitted to cloud databases or used for model retraining.
- **PII Redaction:** Credit card numbers, account numbers, and personal identifiers are masked or redacted in analytical logs.
- **PCI-DSS & GDPR Alignment:** User retains complete data sovereignty with zero persistent telemetry.

---

## 4. Known Limitations & Failure Modes

Reviewers and users should note the following system boundaries:

1. **Manual Entry & CSV Import Delays:**
   - *Limitation:* The system does not maintain live automated bank scrapers (e.g., Plaid/Yodlee) due to security and privacy design choices; transactions reflect data up to the last imported CSV file.
   - *Mitigation:* The agent provides clear import prompts and transaction deduplication tooling to make periodic manual CSV reconciliation seamless.

2. **Absence of Real-Time Market Ticker Streaming:**
   - *Limitation:* Without a configured financial market API key, stock prices reflect user-updated valuation records rather than second-by-second market ticks.
   - *Mitigation:* The agent clarifies whether asset valuations are based on recorded closing prices or manual cost basis.

3. **Tax & Jurisdictional Variations:**
   - *Limitation:* Capital gains tax brackets, local municipal taxes, and deduction rules vary significantly across global jurisdictions.
   - *Mitigation:* The agent provides pre-tax cash flow estimates and directs users to qualified local tax professionals for statutory filings.

4. **Non-Certified Fiduciary Boundary:**
   - *Limitation:* The agent functions as an analytical productivity copilot and does not hold regulatory licenses as a certified financial planner (CFP) or registered investment advisor (RIA).
   - *Mitigation:* All outputs include clear fiduciary disclaimers stating that insights are educational budget projections, not guaranteed investment mandates.

---

## 5. Verification, Safety & Human Oversight

- **Deterministic Balance Reconciliation:** Cash flow calculations are mathematically validated using standard double-entry accounting formulas.
- **User Transaction Authority:** The agent cannot initiate bank transfers, liquidate equities, or alter account balances autonomously.
- **Immutable Local Audit Trail:** All transaction modifications, category edits, and file exports are recorded in structured local logs.
- **Kill Switch:** Application and analysis workers can be terminated immediately with zero residual processes.
