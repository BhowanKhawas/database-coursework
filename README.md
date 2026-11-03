# 🏦 Bank Management System: Enterprise Relational Database (DBMS)

![SQL](https://img.shields.io/badge/SQL-Relational%20Database-CC292B?style=flat&logo=microsoftsqlserver&logoColor=white)
![Database](https://img.shields.io/badge/DBMS-ERD%20%26%20Normalization-blue?style=flat)
![Academic](https://img.shields.io/badge/Academic-Roehampton-red?style=flat)
![License](https://img.shields.io/badge/License-Academic%20Use-lightgrey?style=flat)

An enterprise-grade relational database management system (DBMS) designed to manage core banking operations. The system models real-world financial workflows including multi-branch operations, customer accounts, loan management, fixed deposits, cheque/card transactions, ATM logging, and customer service issue tracking.

---

## 📌 Project Information

- **Module:** Database Management System (Group Coursework)
- **Institution:** University of Roehampton
- **Authors:**
  - **Bhowan Khawas** (Student ID: A00028871)
  - **Sangit Khadka** (Student ID: A00022268)

---

## 🎯 Business Concept & Core Objectives

The goal of this system is to provide a secure, scalable, and fully normalized relational database architecture capable of powering day-to-day retail and commercial banking operations.

### Primary Features
1. **Consolidated Account Management:** Multi-account mapping (`Savings`, `Current`, etc.) tied directly to branch and customer entities.
2. **Loan & Fixed Deposit Handling:** Complete credit management tracking loan approvals, interest rates, payment schedules, and fixed deposit maturity dates.
3. **Transactional Services:** Multi-channel transaction monitoring spanning cheque processing, debit/credit cards, and remote ATM logs.
4. **Branch & Staff Governance:** Administrative tracking of branch offices and employee assignments.
5. **Customer Support Ticketing:** Integrated customer service module for issue resolution tracking.

---

## 📐 Entity-Relationship Diagram (ERD) Architecture

The database architecture consists of **12 core entities** organized into a normalized relational model.

### 12 Core Entities & Primary Keys

| Entity | Primary Key | Description / Key Attributes | Foreign Keys |
| :--- | :--- | :--- | :--- |
| **`branch`** | `branch_id` | Branch offices and contact information. | None |
| **`employee`** | `employee_id` | Bank staff, personal info, and branch assignment. | `branch_id` |
| **`customers`** | `customer_id` | Customer personal profiles, contact details, and registration. | `branch_id` |
| **`account`** | `account_number` | Bank accounts, types, current balance, open date, and status. | `customer_id` |
| **`cheque`** | `cheque_id` | Cheque issue logs, cheque numbers, amounts, and statuses. | `account_number` |
| **`transaction`** | `transaction_id` | Account level financial transfers, types, amounts, and timestamps. | `account_number` |
| **`card`** | `card_number` | Issued payment cards, types, expiry dates, CVVs, and statuses. | `account_number` |
| **`atm_transaction`** | `atmtransaction_id` | Card-based ATM usage logs, amounts, dates, times, and locations. | `card_number` |
| **`loan`** | `loan_id` | Customer loan applications, loan types, interest rates, and status. | `customer_id` |
| **`loan_payment`** | `payment_id` | Installment repayments made against approved customer loans. | `loan_id` |
| **`fixed_deposit`** | `fd_id` | Customer investment accounts, rates, maturity dates, and amounts. | `customer_id` |
| **`customer_service`** | `service_id` | Support tickets, customer issues, resolution dates, and statuses. | `customer_id` |

---

## 🗄️ Database Schema & Data Constraints

The physical implementation ensures high data integrity through strict SQL data types and relational constraints:

- **Primary & Foreign Key Integrity:** All primary keys use `INT NOT NULL` auto-identifiers, while relational foreign keys preserve referential integrity across branches, customers, and accounts.
- **Monetary Precision:** All currency fields (`balance`, `amount`) are defined as `DECIMAL(15,2)` to prevent floating-point rounding errors during financial calculations.
- **Unique Constraints:** Applied to critical unique tokens including `email`, `cheque_number`, and `card_number`.
- **Temporal Logging:** Dedicated `DATE` and `TIME` data types record exact transaction occurrences, loan approval dates, and fixed deposit maturity dates.

---

## 📂 Repository Structure

.
├── Bank final.pdf              # Group Coursework Report & Complete ERD Documentation
└── README.md                   # Project documentation
└── SQL code
