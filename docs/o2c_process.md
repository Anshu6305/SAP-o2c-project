# 🔄 SAP Order-to-Cash (O2C) — Detailed Process Guide

**Author:** Anshuman Routray | Roll No: 23052783 | B.Tech CSE | KIIT University

---

## Overview

The Order-to-Cash (O2C) process in SAP SD covers the complete lifecycle of a sales transaction — from the moment a customer expresses interest to the moment payment is received and reconciled in the books.

```
Inquiry → Quotation → Sales Order → Delivery → Post Goods Issue → Billing → Payment
```

Each step generates a **SAP document** that is linked to the previous, creating a traceable **document flow**.

---

## Step 1: Sales Inquiry — T-Code: VA11

### What is it?
A Sales Inquiry is an informal request from a customer to know about product availability, pricing, and delivery timelines. It is a **pre-sales** document and does not create any binding commitment.

### Business Scenario
Radiant Electronics Ltd. contacts NovaTech Solutions requesting pricing information for 10 units of LED Smart TV 55".

### Transaction Steps
1. Open SAP GUI → Enter T-Code: **VA11**
2. Enter Inquiry Type: **IN**
3. Enter Sales Organization: **NT10**, Distribution Channel: **10**, Division: **01**
4. Click Enter
5. Fill in:
   - Sold-to Party: **CUS001** (Radiant Electronics)
   - Valid From / To: Current date to +30 days
   - Material: **MAT-1001**
   - Quantity: **10 EA**
6. Save → Note the Inquiry Number generated

### Key Fields
| Field | Value |
|---|---|
| Document Type | IN (Inquiry) |
| Sold-to Party | CUS001 |
| Material | MAT-1001 |
| Quantity | 10 EA |
| Requested Delivery Date | +7 days from today |

---

## Step 2: Sales Quotation — T-Code: VA21

### What is it?
A Sales Quotation is the company's **formal, binding offer** to the customer. It specifies price, quantity, delivery date, and payment terms. It has a validity period; if accepted within this window, it converts to a Sales Order.

### Business Scenario
NovaTech Sales Rep creates a quotation for Radiant Electronics based on their inquiry, offering ₹45,000 per unit with Net 30 payment terms.

### Transaction Steps
1. Open SAP GUI → Enter T-Code: **VA21**
2. Enter Quotation Type: **QT**
3. Reference the earlier Inquiry Number (or create fresh)
4. Fill in:
   - Sold-to Party: **CUS001**
   - Valid From / To: 30-day validity window
   - Material: **MAT-1001**, Quantity: **10 EA**
   - Net Price: ₹45,000
5. Save → Note the Quotation Number generated

### Key Fields
| Field | Value |
|---|---|
| Document Type | QT (Quotation) |
| Net Value | ₹4,50,000 |
| Validity Period | 30 days |
| Payment Terms | NT30 (Net 30) |

---

## Step 3: Sales Order — T-Code: VA01

### What is it?
The Sales Order (SO) is the **core binding document** of the O2C process. It represents customer acceptance of the quotation and triggers the entire fulfillment chain.

### Business Scenario
Radiant Electronics accepts the quotation and places a firm order for 10 units of LED Smart TV 55".

### Transaction Steps
1. Open SAP GUI → Enter T-Code: **VA01**
2. Enter Order Type: **OR** (Standard Order)
3. Reference the Quotation Number → Copy data
4. Verify all details:
   - Sold-to Party: CUS001
   - Ship-to Party: CUS001 (same, or specify alternate address)
   - Material: MAT-1001, Quantity: 10 EA
   - Requested Delivery Date: Agreed date
5. Check availability (ATP — Available-to-Promise)
6. Save → Note the Sales Order Number

### Key Fields
| Field | Value |
|---|---|
| Document Type | OR (Standard Order) |
| Sales Order Number | Auto-generated |
| Net Order Value | ₹4,50,000 |
| Delivery Date | Confirmed by ATP |
| Credit Check | Passed (within limit) |

---

## Step 4: Outbound Delivery — T-Code: VL01N

### What is it?
The Delivery document is created to **initiate shipment**. It triggers picking of goods from the warehouse (storage location). The delivery document is linked directly to the Sales Order.

### Business Scenario
NovaTech's warehouse team creates a delivery document for the 10 TVs to be picked and packed for Radiant Electronics.

### Transaction Steps
1. Open SAP GUI → Enter T-Code: **VL01N**
2. Enter Shipping Point: **NT01**
3. Selection Date: Requested delivery date
4. Reference the Sales Order Number
5. Click Enter
6. Review delivery line items (10 units of MAT-1001)
7. Perform Picking:
   - Enter Pick Quantity: 10
   - Storage Location: SL01
8. Save → Note the Outbound Delivery Number

### Key Fields
| Field | Value |
|---|---|
| Delivery Type | LF (Outbound Delivery) |
| Shipping Point | NT01 |
| Pick Quantity | 10 EA |
| Storage Location | SL01 |

---

## Step 5: Post Goods Issue (PGI) — T-Code: VL02N

### What is it?
Post Goods Issue (PGI) is the most critical inventory step in the O2C cycle. It **reduces stock** in the warehouse and legally transfers ownership of goods to the customer. Only after PGI can a billing document be created.

### Business Scenario
After the TVs are picked and packed, the warehouse manager posts the goods issue to confirm the goods have left the facility.

### Transaction Steps
1. Open SAP GUI → Enter T-Code: **VL02N**
2. Enter the Outbound Delivery Number
3. Click Enter → Review delivery
4. Click **Post Goods Issue** button
5. Confirm the posting date and document date
6. Save → Material Document created (inventory reduced)

### What Happens in the Background?
- Stock quantity decreases by 10 units in Plant NT01, SL01
- A Material Document is generated (MM)
- An Accounting Document is generated in FI:
  - **Debit:** Cost of Goods Sold (COGS)
  - **Credit:** Inventory Account

---

## Step 6: Customer Billing / Invoice — T-Code: VF01

### What is it?
Billing is the process of creating the **customer-facing invoice** based on the delivery. The billing document posts revenue to the P&L and creates an Accounts Receivable (AR) open item in FI.

### Business Scenario
The billing clerk creates the invoice for Radiant Electronics for 10 units at ₹45,000 each = ₹4,50,000 total.

### Transaction Steps
1. Open SAP GUI → Enter T-Code: **VF01**
2. Enter Billing Type: **F2** (Invoice)
3. Reference the Outbound Delivery Number
4. Click Enter → Review billing items
5. Verify:
   - Net Value: ₹4,50,000
   - Tax (GST 18%): ₹81,000
   - Total: ₹5,31,000
6. Save → Billing Document created, AR open item posted in FI

### Accounting Entry (FI)
| Entry | Account | Amount |
|---|---|---|
| Debit | Accounts Receivable (CUS001) | ₹5,31,000 |
| Credit | Revenue Account | ₹4,50,000 |
| Credit | GST Payable | ₹81,000 |

---

## Step 7: Incoming Payment Receipt — T-Code: F-28

### What is it?
The final step of the O2C cycle. The customer pays the invoice and the Accounts Receivable (AR) is **cleared** in SAP FI. This closes the revenue cycle.

### Business Scenario
Radiant Electronics transfers ₹5,31,000 to NovaTech's bank account within 30 days. The AR Accountant posts the payment in SAP.

### Transaction Steps
1. Open SAP GUI → Enter T-Code: **F-28**
2. Enter Document Date: Payment date
3. Bank Account: NT_BANK (NovaTech's house bank)
4. Amount: ₹5,31,000
5. Customer: CUS001
6. Select the open AR item (billing document)
7. Click **Process Open Items** → Match payment to invoice
8. Post → AR cleared; bank account credited

### Accounting Entry (FI)
| Entry | Account | Amount |
|---|---|---|
| Debit | Bank Account | ₹5,31,000 |
| Credit | Accounts Receivable (CUS001) | ₹5,31,000 |

---

## 📎 Complete Document Flow Summary

```
Inquiry (VA11)
    └── Quotation (VA21)
            └── Sales Order - OR (VA01)
                    └── Outbound Delivery - LF (VL01N)
                            └── Post Goods Issue (VL02N)
                                    ├── Material Document (MM)
                                    └── Billing Document - F2 (VF01)
                                                └── Accounting Document (FI)
                                                        └── Payment Clearing (F-28)
```

---

## 📊 Key SAP Reports for O2C Monitoring

| Report | T-Code | Purpose |
|---|---|---|
| Sales Order List | VA05 | View all open/closed sales orders |
| Delivery Monitor | VL06O | Track pending and completed deliveries |
| Billing Due List | VF04 | List all deliveries pending billing |
| Customer Line Items | FBL5N | View AR open items per customer |
| Customer Balance | FD10N | Customer account balance summary |

---

*Document prepared by: Anshuman Routray | Roll No: 23052783 | B.Tech CSE | KIIT University*
