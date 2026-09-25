---
name: ledger-serialization-auditor
description: Audit and validate data serialization across CSV, JSON, and Shelve database formats.
---

# Ledger Serialization Auditor Skill

## Overview
Manages multi-format financial data persistence via the CJS engine, ensuring data integrity across imports and exports.

## Operations
1. Validates file header structures for CSV and JSON ledgers.
2. Detects schema corruption or malformed currency figures.
3. Guarantees safe atomic writes during file exports.
