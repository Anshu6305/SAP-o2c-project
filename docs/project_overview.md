# 📌 Project Overview — SAP Order-to-Cash (O2C)

**Author:** Anshuman Routray | Roll No: 23052783 | B.Tech CSE | KIIT University

---

## 1. Business Context

**Company:** NovaTech Solutions Pvt. Ltd.  
**Industry:** Electronics Distribution  
**Location:** Bhubaneswar, Odisha (fictional)  
**Size:** Mid-sized enterprise with 500+ employees

NovaTech Solutions distributes a wide range of consumer and industrial electronics to B2B clients across eastern India. The company deals with bulk sales orders, multiple distribution channels, and a diverse customer base ranging from retail chains to government institutions.

---

## 2. Problem Statement

Before SAP implementation, NovaTech Solutions faced significant operational challenges in its sales and collections process:

| Challenge | Impact |
|---|---|
| Manual sales order entry via spreadsheets | Frequent data errors, slow processing |
| No centralized customer master | Duplicate customers, inconsistent pricing |
| Email-based delivery confirmations | Delayed invoicing, missed shipments |
| Manual invoice creation | Billing errors, customer disputes |
| No automated payment tracking | Poor AR visibility, delayed collections |
| No credit limit enforcement | Bad debt risk, over-extension of credit |

These issues resulted in an average **billing cycle delay of 7–10 days** and revenue leakage of approximately 3–5% per quarter.

---

## 3. Scope of the Project

This project covers the implementation and demonstration of the complete **Order-to-Cash (O2C)** process cycle within SAP ERP, specifically:

- **SAP SD (Sales & Distribution):** Inquiry, Quotation, Sales Order, Delivery, Post Goods Issue, Billing
- **SAP FI (Financial Accounting):** Customer Invoice, Accounts Receivable, Payment Receipt

The project does **not** cover:
- SAP CRM or Salesforce integration
- Multi-currency transactions
- Intercompany sales scenarios
- Returns and credit memo processing (marked as future scope)

---

## 4. Organizational Structure (SAP)

| SAP Object | Value | Description |
|---|---|---|
| Company Code | NT01 | NovaTech Solutions Pvt. Ltd. |
| Sales Organization | NT10 | India Sales Org |
| Distribution Channel | 10 | Direct Sales |
| Division | 01 | Electronics |
| Plant | NT01 | Bhubaneswar Plant |
| Storage Location | SL01 | Main Warehouse |

---

## 5. Master Data Used

### Customer Master
| Field | Value |
|---|---|
| Customer Name | Radiant Electronics Ltd. |
| Customer Number | CUS001 |
| City | Cuttack, Odisha |
| Credit Limit | ₹10,00,000 |
| Payment Terms | Net 30 Days |

### Material Master
| Field | Value |
|---|---|
| Material | LED Smart TV 55" |
| Material Number | MAT-1001 |
| Unit of Measure | EA (Each) |
| Price | ₹45,000 per unit |
| Available Stock | 200 units |

---

## 6. Key Stakeholders

| Role | Responsibility |
|---|---|
| Sales Representative | Creates inquiry, quotation, and sales order |
| Warehouse Manager | Processes delivery and post goods issue |
| Billing Clerk | Generates customer invoice |
| Accounts Receivable (AR) Accountant | Posts incoming customer payment |

---

## 7. Tools & Technology

- **Platform:** SAP ERP (ECC 6.0 / S/4HANA simulation)
- **Modules:** SAP SD, SAP MM, SAP FI
- **Access:** SAP GUI (SAPGUI 7.x)
- **Documentation:** Markdown + Screenshots

---

*Document prepared by: Anshuman Routray | Roll No: 23052783 | B.Tech CSE | KIIT University*
