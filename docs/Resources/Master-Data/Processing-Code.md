# Processing Codes

## Overview

A set of numbers that describe the type of the transaction as well as the account type being used. Required on all transaction requests and upload detail records.

The Processing code has 3 subdivisions 

- Positions 1 – 2, [Transaction Type](#transactiontype)
- Positions 3 – 4, [Account Type (From)](#fromaccounttype)
- Positions 5 – 6, [Account Type (To)](#toaccounttype)

---

## Transaction Type

Describes the transaction being performed. Valid values are

| Transaction Type | Description |
| ------ | ------ |
| 00 | Goods and Services (Authorizations and Full Reversals)/Pre-Authorization Purchase with Cash Back ( Canada Debit only ) |
| 01 | Withdrawal/cash advance |
| 02 | Adjustment of a return (Canada Debit only) |
| 04 | Check verification |
| 09 | Purchase with Cash Back ( excluding Canada Debit ) |
| 20 | Return/Refund (Debit and Credit Host Capture) |
| 21 | Payment (only specified private label formats) |
| 22 | Payment Reversal (only specified private label formats) |
| 22 | Adjustment of a Sale (Debit only) |
| 28 | Load or Load/Activate Prepaid Card Account (Visa Only) |
| 30 | Available Funds Inquiry (non-captured) |
| 31 | Balance Inquiry on Prepaid Debit/ EBT cards |
| 45 | Capture Only/Force Post Transaction (Host Draft Capture Merchants Only) |
| 50 | Debit ‘Bill Payment’ Purchase for Card Not Present transactions (Internet, VRU, Call-Center, and Recurring). Not applicable for EMV transactions. |
| 54 | Debit ‘POS PINless’ Purchase for Card Present, Magstripe Swipe transactions only. Not applicable for EMV transactions. This value is defunct. Please check with your First Data Relationship Manager. |
| 55 | Debit ‘Bill-Payment’ Refund/Return for Card Not Present transactions (Internet, VRU, Call-Center, and Recurring) Not applicable for EMV transactions. |
| 59 | Debit ‘POS PINless’ Refund/Return for Card Present, Magstripe Swipe transactions only. Not applicable for EMV transactions. This value is defunct. Please check with your First Data Relationship Manager. |
| 72 | Activate Prepaid Card Account (Visa Only) |
| 90 | Signature Capture Data Present or Debit Key Exchange |
| 99 | Test transaction (0800 — Network Admin) |

---

## From Account Type

Describes the cardholder account type affected for cardholder account debits and inquiries and the "from" account type for cardholder account transfer transaction.

| Account Type | Description |
| ------ | ------ |
| 00 | Default Account (Credit, Debit, and check only) |
| 10 | Savings Account (Debit — Canada only) – Excluding UnionPay |
| 20 | Checking Account (Debit — Canada only) – Excluding UnionPay |
| 90 | Default Account (Debit only) |
| 96 | Cash Benefits Account (EBT Only) |
| 98 | Food Stamps Account (EBT Only) |

---

## To Account Type

Describes the cardholder account type affected for cardholder account credits and the "to" account type for cardholder account transfer transaction.

| Account Type | Description |
| ------ | ------ |
| 00 | Default Account (Credit, Debit, check, and EBT) |
| 10 | Savings Account (Debit — Canada only) – Excluding UnionPay |
| 20 | Checking Account (Debit — Canada only) – Excluding UnionPay |
| 46 | Force Post Transaction (logged to Billing File, not switched to Association) for debit only |

---

## See Also

- [API Explorer](../api/?type=post&path=/payments/v1/charges)

---
