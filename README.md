# 🧾 SAP Order-to-Cash (O2C) — Full Sales Cycle

> A SAP SD capstone project demonstrating the complete end-to-end Order-to-Cash process using SAP ERP.

---

## 👤 Author Details

| Field | Details |
| --- | --- |
| **Name** | Anshuman Routray |
| **Roll Number** | 23052783 |
| **Programme** | B.Tech |
| **Specialization** | Computer Science and Engineering (CSE) |
| **Course** | SAP Order to Cash |
| **University** | Kalinga Institute of Industrial Technology (KIIT) |

---

## 📌 Introduction

The Order-to-Cash (O2C) process is one of the most critical revenue-generating workflows in any organization. It covers everything from receiving a customer inquiry to collecting the final payment for goods or services delivered. This project demonstrates the complete O2C cycle using SAP Sales & Distribution (SD) and Financial Accounting (FI) modules within an SAP ERP environment.

The project uses a fictional company called **NovaTech Solutions Pvt. Ltd.** — a mid-sized electronics distribution firm — as the business context throughout all documentation and demonstrations.

---

## 🧩 Business Problem

NovaTech Solutions was managing its sales and order fulfillment activities using spreadsheets and manual approval chains. This created several issues:

- No real-time visibility into customer orders or delivery status
- Duplicate billing due to manual invoice creation
- Delays in approvals because there was no structured workflow
- No centralized customer master database for order history and credit checks
- Revenue leakage due to untracked shipments and missed billing cycles

The goal of this project was to implement SAP SD's O2C cycle to eliminate these inefficiencies and bring full process automation and traceability.

---

## 🎯 Objectives

- Understand and configure the full O2C cycle in SAP SD
- Execute each transaction step using the correct T-Codes
- Demonstrate document flow from Sales Inquiry to Payment Receipt
- Show integration between SAP SD and SAP FI modules
- Document the entire process clearly for academic and practical reference

---

## 🔧 SAP Modules Used

| Module | Full Name | Role in O2C |
| --- | --- | --- |
| **SD** | Sales & Distribution | Handles sales orders, delivery, billing |
| **MM** | Materials Management | Handles inventory, goods issue confirmation |
| **FI** | Financial Accounting | Handles customer invoicing and payment receipt |

---

## 🔄 End-to-End Workflow

```
[Customer Inquiry Received]
         |
         v
 ┌───────────────────┐
 │  Sales Inquiry    │  T-Code: VA11
 │                   │  (Customer asks about product/price availability)
 └────────┬──────────┘
          |
          v
 ┌───────────────────┐
 │  Sales Quotation  │  T-Code: VA21
 │                   │  (Formal quote with price/terms sent to customer)
 └────────┬──────────┘
          |
          v
 ┌───────────────────┐
 │  Sales Order      │  T-Code: VA01
 │  (SO)             │  (Customer confirms; binding sales order created)
 └────────┬──────────┘
          |
          v
 ┌───────────────────┐
 │  Delivery         │  T-Code: VL01N
 │  Processing       │  (Outbound delivery document created, goods picked)
 └────────┬──────────┘
          |
          v
 ┌───────────────────┐
 │  Post Goods       │  T-Code: VL02N
 │  Issue (PGI)      │  (Inventory reduced; ownership transferred to customer)
 └────────┬──────────┘
          |
          v
 ┌───────────────────┐
 │  Customer         │  T-Code: VF01
 │  Billing/Invoice  │  (Invoice generated based on delivery)
 └────────┬──────────┘
          |
          v
 ┌───────────────────┐
 │  Payment Receipt  │  T-Code: F-28
 │                   │  (Customer payment posted; AR cleared)
 └───────────────────┘
```

---

## ✅ Features

- Complete 7-step O2C process demonstrated
- Real business scenario using NovaTech Solutions
- Document flow linkage across all SAP transactions
- Integration between SD, MM, and FI shown clearly
- Screenshot documentation for each key step
- Simple, academic-friendly language throughout

---

## 📋 Process Overview

| Step | Activity | T-Code | Module |
| --- | --- | --- | --- |
| 1 | Sales Inquiry | VA11 | SD |
| 2 | Sales Quotation | VA21 | SD |
| 3 | Sales Order | VA01 | SD |
| 4 | Delivery Processing | VL01N | SD/MM |
| 5 | Post Goods Issue | VL02N | SD/MM |
| 6 | Customer Billing | VF01 | SD/FI |
| 7 | Payment Receipt | F-28 | FI |

---

## 🖼️ Screenshots

All screenshots are stored in the `/screenshots` folder as per the naming convention. The following are captured for each step:

| File Name | Description |
| --- | --- |
| `01_VA11_inquiry_creation.png` | Sales Inquiry creation screen |
| `02_VA21_quotation_creation.png` | Quotation with pricing and validity |
| `03_VA01_sales_order.png` | Sales Order with line items and schedule lines |
| `04_VL01N_delivery.png` | Outbound delivery document creation |
| `05_VL02N_pgi.png` | Post Goods Issue confirmation screen |
| `06_VF01_billing.png` | Customer invoice (billing document) |
| `07_F28_payment_receipt.png` | Incoming payment posting against invoice |
| `08_document_flow.png` | Full document flow chain in SAP |

---

## 📚 Learning Outcomes

After completing this project, I was able to:

- Understand how a sales order flows through an ERP system end to end
- Execute SAP SD transactions with confidence
- Understand how SAP SD, MM, and FI are integrated
- Identify how document flow works (Inquiry → Quotation → SO → Delivery → PGI → Invoice → Payment)
- Appreciate the value of 3-step revenue matching in preventing billing errors and revenue leakage

---

## 🚀 Future Improvements

- Add **SAP CRM / S/4HANA Sales** for customer relationship management integration
- Include **Credit Management** (FD32) to automate credit limit checks on sales orders
- Explore **Fiori apps** for mobile-based order confirmation and delivery workflows
- Add **reporting** using SAP Analytics Cloud or S/4HANA Embedded Analytics
- Implement **Returns Processing** using Return Orders (RE document type) and Credit Memos

---

## 📁 Project Structure

```
SAP-o2c-project/
│── README.md                      ← You are here
│── docs/
│    ├── project_overview.md       ← Business context and scope
│    ├── o2c_process.md            ← Detailed step-by-step process guide
│── screenshots/                   ← SAP transaction screenshots (see guide)
│── report/
│    ├── final_report.md           ← Full academic report (4–5 pages)
```

---

## 🏫 Disclaimer

This project is created for academic purposes as part of the SAP Order to Cash course at KIIT University. All company names and data used are fictional.

---

Screenshots are stored in the `/screenshots` folder as per the naming convention described in `screenshots/SCREENSHOT_GUIDE.md`.

---

*Made with ❤️ by Anshuman Routray | KIIT University | 2025–26*

---

**Author:** Anshuman Routray  
**Roll No:** 23052783  
**KIIT University**
