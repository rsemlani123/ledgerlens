# 📒 LedgerLens — AI Invoice-to-Journal-Entry & GL Coding Assistant

**Paste a vendor invoice → get a balanced journal entry with the right GL account, in seconds.**

LedgerLens automates the first (and most repetitive) step of Accounts Payable: reading an invoice, deciding which General Ledger account it belongs to, and writing the double-entry. Instead of typing entries by hand hundreds of times a month, an accountant reviews a suggested entry that is already coded and always balanced.

> 🔗 **Live demo:** _add your GitHub Pages link here after publishing_
> 💼 Built by Rohneet Semlani — M.S. Finance (Arizona State University) | Staff Accountant / AP-AR

---

## The problem it solves

In Accounts Payable, every invoice has to be read, matched to the correct expense account (GL coding), and booked as a journal entry before month-end close. Done manually, this is slow and a common source of posting errors. LedgerLens takes the invoice text and does the first pass automatically, so the accountant reviews instead of retypes — cutting coding time and reducing mistakes before they reach the books.

## What it does

- **Reads the invoice** — extracts vendor, invoice number, date, subtotal, tax, and total.
- **Codes the GL account** — matches keywords in the invoice to a built-in chart of accounts (e.g. "software subscription" → *5020 Software & Subscriptions Expense*).
- **Writes the journal entry** — books `Dr Expense` + `Dr Input Tax` against `Cr Accounts Payable`.
- **Guarantees balance** — checks that total debits equal total credits and flags anything that doesn't.
- **Shows confidence** — warns when no clear GL match is found, so it can be reviewed.

## How it works

1. The invoice text is parsed with pattern matching to pull out amounts and details.
2. Keywords are compared against a chart of accounts to select the GL account.
3. The tool constructs a standard double-entry and verifies debits = credits.
4. Results are displayed in a clean, auditable table.

**Accounting logic behind the entry**

| Account | Debit | Credit |
|---|---|---|
| Expense / Asset (e.g. 5020 Software) | Net amount | — |
| 1360 Input Tax / Sales Tax Receivable | Tax amount | — |
| 2100 Accounts Payable | — | Total amount |

## Built with

- **HTML, CSS, JavaScript** — single self-contained file, no installation needed.
- **A rule-based accounting engine** — a chart of accounts + keyword logic that mirrors how GL coding is done, designed to be swappable with an AI model later.
- **AI-assisted development** — built and tested with the help of AI tools (Claude / ChatGPT) as a pair-programming partner.

## Chart of accounts (sample)

Covers common expense categories: Software & Subscriptions, Professional Fees, Utilities, Rent, Travel & Entertainment, Marketing, Repairs & Maintenance, Telephone & Internet, Office Equipment (Fixed Asset), Office Supplies, Prepaid Insurance, and Freight & Shipping — with a general expense fallback.

## How to run it

1. Download or clone this repository.
2. Open `index.html` in any web browser.
3. Click a sample invoice (or paste your own) and press **Generate Journal Entry**.

## Roadmap

- Connect a live AI model (LLM) for smarter extraction of messy, real-world invoices.
- Support PDF and image upload with text recognition (OCR).
- Export entries to CSV for import into QuickBooks / SAP / NetSuite.
- Add multi-currency and multi-line-item support.

## Disclaimer

LedgerLens is a portfolio demonstration tool. Suggested entries should always be reviewed by a qualified accountant before posting to the books.