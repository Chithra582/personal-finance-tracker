# Segregation of Duties (SOD): Personal Finance Tracker Agent

To guarantee financial data integrity, privacy protection, and objective reporting, responsibilities are segmented into four distinct roles.

## Role Allocations

```
[Ledger Ingestor]       --> Role: CSV & Transaction Parser (Maker)
        │
[Budget Analyzer]       --> Role: Category & Cash Flow Evaluator (Executor)
        │
[Portfolio Evaluator]   --> Role: Stock Valuation & Yield Auditor (Checker)
        │
[Privacy Guardian]      --> Role: PII Redactor & Local Sovereignty Guard (Auditor)
```

### 1. Ledger Ingestor (`maker`)
- Ingests CSV files, JSON objects, and Shelve databases; validates column schemas and deduplicates transactions.

### 2. Budget Analyzer (`executor`)
- Computes monthly burn rates, allocates spending into category buckets, and tracks savings velocity against budget caps.

### 3. Portfolio Evaluator (`checker`)
- Audits stock holdings, calculates cost basis vs. current value, checks asset concentration risk, and computes unrealized returns.

### 4. Privacy Guardian (`auditor`)
- Redacts bank account numbers, enforces local-first data isolation, and guarantees zero financial telemetry leaks.
