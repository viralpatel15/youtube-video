# V02 – Late Payments Killing Your Cash Flow? ERPNext Sales Cycle Solution

**Length:** ~13 minutes | **Demo company:** ABC Manufacturing Pvt. Ltd. | **Style:** Use case → ERPNext solution → live demo (story under 1 minute)

**Format:** 🎙 = what you say | 🖥 = what you do on screen | 🏷 = on-screen tag | ✅ = checkpoint before moving on

**Retention rule:** every demo step carries a small tag linking the use case to the ERPNext feature (🏷 *Use case: goods delivered, invoice not raised* → *ERPNext: Delivery Note "To Bill"*).

---

# PART A – PREPARATION

## Use Case Summary

**Company:** ABC Manufacturing Pvt. Ltd. sells steel rods to dealers.
**Problem:** Goods were delivered 20 days ago, but the invoice was not even created. Payment terms were never agreed in writing, and nobody tracks which customer is overdue. Cash is stuck.

| Cause | ERPNext feature that solves it |
| --- | --- |
| Delivered, but invoice not raised | Delivery Note status **To Bill**, Sales Invoice created from Delivery Note |
| Payment terms never fixed, so no due date | **Payment Terms Template** on Customer, Quotation, and Invoice |
| Nobody tracks overdue payments | **Payment Entry** against invoice, **Accounts Receivable** report, **Dunning** reminders |

## Demo Data

| Item | Value |
| --- | --- |
| Customer (live demo) | Sharma Traders |
| Customer (pre-created, overdue) | Patel Hardware |
| Item | Steel Rod 10mm (from V01) |
| Sale | 20 Nos × ₹750 = **₹15,000** (no tax, to keep the demo simple) |
| Payment terms | Net 15 (100% due 15 days after invoice date) |
| Payment received | ₹10,000 by bank, so ₹5,000 stays outstanding |
| Pre-created overdue invoice | Patel Hardware, 25 Nos × ₹1,000 = **₹25,000**, posted 45 days ago on Net 30, so **15 days overdue** |
| Warehouse | Main Store - ABC |

> The demo is without GST so the flow stays clear. In India, add your Sales Taxes and Charges template (GST) on Quotation, Sales Order, and Invoice. Say this on camera in one line.

## Pre-Create Before Recording

These save time and are shown, not built, on camera.

- [ ] Customer **Patel Hardware**
- [ ] Payment Terms Template **Net 30** (used by the old invoice)
- [ ] Sales Invoice for Patel Hardware: ₹25,000, with **Edit Posting Date and Time** checked, posting date 45 days ago, payment terms Net 30, **Update Stock off**, Submitted
- [ ] **Dunning Type** "First Reminder" (rate of interest 0, dunning fee 0, body text written)
- [ ] Stock of Steel Rod 10mm in Main Store - ABC is at least 20 (63 if you continue from V01)
- [ ] Hook diagram and solution-map slide ready

## Do NOT Pre-Create (record live)

Payment Term and Payment Terms Template "Net 15", customer Sharma Traders, and the Quotation, Sales Order, Delivery Note, Sales Invoice, and Payment Entry.

## Recording Order and Running Numbers

| # | Transaction | ERPNext document | Amount | Result |
| --- | --- | --- | --- | --- |
| T1 | Create payment terms | Payment Term + Payment Terms Template | – | Net 15 |
| T2 | Create customer | Customer | – | Default terms Net 15 |
| T3 | Quote the customer | Quotation | ₹15,000 | Submitted |
| T4 | Customer confirms | Sales Order | ₹15,000 | To Deliver and Bill |
| T5 | Ship the goods | Delivery Note | ₹15,000 | Status **To Bill**, Main Store −20 |
| T6 | Catch unbilled deliveries, then invoice | Sales Invoice | ₹15,000 | Due date = invoice date + 15 days |
| T7 | Receive part payment | Payment Entry | ₹10,000 | Invoice **Partly Paid**, outstanding ₹5,000 |
| T8 | Track receivables | Accounts Receivable report | – | Sharma ₹5,000, Patel ₹25,000 overdue |
| T9 | Send a reminder | Dunning | – | Reminder for Patel Hardware |
| T10 | (Optional) automatic reminder | Notification | – | Alert after due date |

**Final position:** total receivable ₹30,000 = Sharma Traders ₹5,000 (not yet due) + Patel Hardware ₹25,000 (15 days overdue).

### Setup Checklist

- [ ] Use today's date for every live document
- [ ] Browser zoom 110–125%, notifications off
- [ ] One full dry run on a test site (field names and report columns can differ by version)

---

# PART B – SCRIPT AND RECORDING STEPS

## Part 1 – Hook (0:00–0:30)

🖥 Hook diagram, revealed in steps: "Delivered 20 days ago" → "Invoice: not created" → "Payment: not received" → "Cash flow: stuck".

🎙 "You delivered the goods 20 days ago. But the invoice is not even created.

So the customer is not paying. Your team is not following up. And your own bills are due this week.

This is how profitable businesses run out of cash. In this video, I'll show you how ERPNext fixes this, from the quotation all the way to the payment, step by step."

---

## Part 2 – The Use Case in 45 Seconds (0:30–1:15)

🖥 Use case slide, then the causes table revealed row by row.

```text
USE CASE
Company:   ABC Manufacturing Pvt. Ltd.
Customer:  Sharma Traders
Sale:      20 steel rods = ₹15,000
Problem:   Goods delivered, cash not collected
```

| Cause | Result |
| --- | --- |
| Delivered, invoice not raised | Payment clock never starts |
| No payment terms fixed | No due date to follow |
| No overdue tracking | Nobody follows up |

🎙 "Welcome to the channel. In this series, I take one real business problem and solve it using ERPNext and other Frappe products.

Today's use case: ABC Manufacturing sells steel rods to Sharma Traders. The goods are delivered, but the cash is not collected.

When we checked, there were three causes. The invoice was not raised after the delivery. The payment terms were never fixed, so there was no due date. And nobody was tracking which customers were overdue.

So the problem is not the customer. The problem is that the sales process has gaps between the order, the delivery, the invoice, and the payment. Let's see what ERPNext gives us to close those gaps."

---

## Part 3 – The ERPNext Solution Map (1:15–2:45)

🖥 Solution-map slide, one row at a time.

| Business need | ERPNext feature | Use case link |
| --- | --- | --- |
| Agree price and terms upfront | Quotation, Sales Order, Payment Terms | Due date from day one |
| Know what is delivered but not billed | Delivery Note status **To Bill** | Invoice never forgotten |
| Invoice with a proper due date | Sales Invoice with Payment Terms | Net 15 |
| Record every payment against the invoice | Payment Entry | ₹10,000 received |
| See who owes what | Accounts Receivable report | ₹30,000 outstanding |
| Chase overdue payments | Dunning (reminder) | Patel Hardware |

🎙 "Here is the complete solution in one slide. ERPNext closes the gaps with six features.

One: Quotation, Sales Order, and Payment Terms. Price and payment terms are agreed before delivery, so the due date exists from day one.

Two: the Delivery Note. When goods are delivered but not billed, the Delivery Note shows the status To Bill. Nothing is forgotten.

Three: the Sales Invoice, created directly from the Delivery Note, with the due date calculated from the payment terms.

Four: Payment Entry. Every payment is recorded against the invoice, so you always know the outstanding amount.

Five: the Accounts Receivable report. One screen shows who owes you how much, and for how many days.

And six: Dunning, the payment reminder. ERPNext prepares and sends the reminder for overdue invoices.

Let's build this flow from scratch in ERPNext."

---

## Part 4 – Live Demo (2:45–11:45)

### T1 – Payment Terms: Net 15 (2:45–3:30)

🏷 *Use case: no payment terms → ERPNext: Payment Terms Template*

🖥 **Accounts → Payment Term → New**

| Field | Value |
| --- | --- |
| Payment Term Name | Net 15 |
| Invoice Portion | 100 |
| Due Date Based On | Day(s) after invoice date |
| Credit Days | 15 |

Save. Then **Accounts → Payment Terms Template → New**

| Field | Value |
| --- | --- |
| Template Name | Net 15 |
| Payment Term row | Net 15 |

Save.

✅ Template "Net 15" saved.

🎙 "First, the payment terms. A Payment Term says when the money is due. I create one called Net 15: 100 percent of the invoice, due 15 days after the invoice date.

Then I put it in a Payment Terms Template, also called Net 15. A template can have more than one term, for example 50 percent advance and 50 percent after 30 days. We keep it simple today.

Once this is ready, ERPNext calculates the due date automatically on every invoice. No one has to remember."

### T2 – Customer: Sharma Traders (3:30–4:00)

🏷 *ERPNext: Customer with default payment terms*

🖥 **Selling → Customer → New**

| Field | Value |
| --- | --- |
| Customer Name | Sharma Traders |
| Customer Group | Commercial |
| Default Payment Terms Template | Net 15 |

Save.

✅ Customer saved with Net 15.

🎙 "Now the customer: Sharma Traders. The important field here is Default Payment Terms Template. I select Net 15.

From now on, every quotation, order, and invoice for this customer will pick up these terms automatically. The terms are agreed once, at the customer level."

### T3 – Quotation: 20 Nos × ₹750 (4:00–4:45)

🏷 *ERPNext: Quotation (price and terms agreed upfront)*

🖥 **Selling → Quotation → New**

| Field | Value |
| --- | --- |
| Quotation To | Customer: Sharma Traders |
| Item Code | Steel Rod 10mm |
| Qty | 20 |
| Rate | 750 |
| Payment Terms Template | Net 15 (auto-filled) |

Point to the grand total: **₹15,000**. Save, then **Submit**.

✅ Quotation submitted, total ₹15,000.

🎙 "Now we make a quotation. Customer: Sharma Traders. Item: Steel Rod 10mm. Quantity 20, rate 750 rupees. The total is 15,000 rupees.

Look at the payment terms section: Net 15 is already there. So the customer sees the price and the payment terms together, before anything is delivered.

In India, you would add your GST taxes here. I'm skipping tax to keep the flow clear. Submit."

### T4 – Sales Order from Quotation (4:45–5:30)

🏷 *ERPNext: Sales Order (customer commitment)*

🖥 On the submitted Quotation: **Create → Sales Order**.
Set **Delivery Date** (a few days ahead). Check items, rate, and payment terms. Save, then **Submit**. Point to the status.

✅ Status: **To Deliver and Bill**.

🎙 "The customer agrees. From the quotation, I click Create, Sales Order. All the details come along, so there is no re-typing.

I set the delivery date and submit. Look at the status: To Deliver and Bill. ERPNext now knows two things are pending: delivery and billing.

The Sales Order is your customer's commitment, and it is the document that drives everything after it."

### T5 – Delivery Note from Sales Order (5:30–6:30)

🏷 *ERPNext: Delivery Note (stock goes out, status To Bill)*

🖥 On the Sales Order: **Create → Delivery Note**.

| Field | Value |
| --- | --- |
| Source Warehouse | Main Store - ABC |
| Qty | 20 |

Save, then **Submit**. Point to the status.

✅ Status: **To Bill**. Main Store stock reduced by 20 (63 → 43 if you continue from V01).

🎙 "Now we ship the goods. From the Sales Order, Create, Delivery Note. I select the source warehouse: Main Store. Quantity 20. Submit.

Two things happen. The stock reduces by 20 in Main Store, so your inventory is correct. And look at the status: To Bill.

This status is the answer to our hook. It means: goods are delivered, but the invoice is not raised yet. Remember this status. We will use it in the next step."

### T6 – Catch Unbilled Deliveries, Then Create the Invoice (6:30–8:00)

🏷 *Use case: delivered, invoice not raised → ERPNext: Delivery Note "To Bill" + Sales Invoice*

🖥 **Step A.** Go to the **Delivery Note list**. Filter **Status = To Bill**. Show the Sharma Traders row.

🎙 "Now, how do we make sure no delivery is forgotten? Open the Delivery Note list and filter by status To Bill. Every row here is a delivery that is not yet invoiced.

If your accounts team checks this list every morning, the situation in our hook, goods delivered 20 days ago and no invoice, cannot happen."

🖥 **Step B.** Open the Delivery Note → **Create → Sales Invoice**. Show the **Payment Schedule** section: Due Date = invoice date + 15 days, amount ₹15,000. Save, then **Submit**. Show the status: **Unpaid**.
Optional: **View → Accounting Ledger** (Debtors debit ₹15,000, Sales credit ₹15,000).

✅ Invoice submitted, due date shown, delivery note status now **Completed**.

🎙 "Now I open the Delivery Note and click Create, Sales Invoice. One click, and everything comes from the delivery: the customer, the items, the rates.

Look at the payment schedule. The due date is already calculated: 15 days after the invoice date, amount 15,000 rupees. Nobody typed this date. It came from the payment terms.

Submit. The status is Unpaid. And if I go back to the Delivery Note, it is now completed, so it disappears from the To Bill list.

In the accounting ledger, you can see the entry: Debtors debited 15,000, Sales credited 15,000. The invoice created the receivable automatically."

### T7 – Payment Entry: ₹10,000 Received (8:00–9:00)

🏷 *Use case: payment tracking → ERPNext: Payment Entry*

🖥 On the Sales Invoice: **Create → Payment**.

| Field | Value |
| --- | --- |
| Mode of Payment | Bank |
| Paid Amount | 10,000 |
| Reference No | Any bank reference |
| Reference Date | Today |

Check the **Payment References** table shows the invoice with allocated ₹10,000. Save, then **Submit**. Return to the Sales Invoice and show the status.

✅ Invoice status **Partly Paid**, outstanding **₹5,000**.

🎙 "The customer pays 10,000 rupees by bank transfer. From the invoice, I click Create, Payment.

Mode of payment: Bank. Paid amount: 10,000. I enter the bank reference number and the date.

Look at the payment references table. ERPNext has linked this payment to our invoice. Submit.

Now open the invoice again. The status is Partly Paid, and the outstanding amount is 5,000 rupees. You never need to calculate this yourself. The system always knows what is pending."

### T8 – Accounts Receivable Report (9:00–10:15)

🏷 *ERPNext: Accounts Receivable report = who owes you what*

🖥 **Accounts → Reports → Accounts Receivable**. Set **Company** and **Ageing Based On = Due Date**. Run the report. Point to: Sharma Traders ₹5,000 (not yet due), Patel Hardware ₹25,000 (15 days overdue). Point to the **Age (Days)** and the total outstanding row.

✅ Total outstanding **₹30,000**, with Patel Hardware's ₹25,000 clearly overdue.

🎙 "Now the most important report for your cash flow: Accounts Receivable.

Here you can see every customer who owes you money. Sharma Traders owes 5,000 rupees, and it is not yet due. Patel Hardware, our older customer, owes 25,000 rupees, and this invoice is 15 days overdue. The total receivable is 30,000 rupees.

Look at the age column. It shows exactly how many days each payment is late. The ageing is based on the due date, so you see real lateness, not just old invoices.

Your owner can open this report on Monday morning and know in one minute where the cash is stuck. And now we know who to follow up with: Patel Hardware."

### T9 – Dunning: Payment Reminder (10:15–11:15)

🏷 *Use case: nobody follows up → ERPNext: Dunning*

🖥 Open Patel Hardware's overdue Sales Invoice → **Create → Dunning**.

| Field | Value |
| --- | --- |
| Dunning Type | First Reminder |
| Overdue Days | 15 (auto-calculated) |
| Body text | Shown from the Dunning Type |

Show the **overdue payments** table, then **Save** and **Submit**. Open the email dialog and show the message.

✅ Dunning submitted with Patel Hardware's invoice and overdue days.

🎙 "Now we follow up. I open the overdue invoice from Patel Hardware and click Create, Dunning. A Dunning is a formal payment reminder.

I select the Dunning Type: First Reminder. ERPNext fills the overdue days: 15. It lists the overdue invoice and the amount, and prepares the message from the template.

You can add an interest rate or a late fee in the Dunning Type. We keep both at zero today, just a friendly reminder.

I submit it, and then send it to the customer by email. The reminder is professional, it is on record, and it takes under a minute. Your team no longer needs to call or message every customer separately."

### T10 (Optional) – Automatic Reminder Notification (11:15–11:45)

🏷 *ERPNext: Notification (automatic alert)*

🖥 **Notifications → Notification → New** (show only, don't build fully)

| Field | Value |
| --- | --- |
| Document Type | Sales Invoice |
| Send Alert On | Days After (Date Field: due date, 1 day) |
| Condition | Outstanding amount greater than 0 |
| Recipients | Customer email field |

🎙 "And if you want this to be fully automatic, you can set up a Notification on the Sales Invoice. One day after the due date, if the outstanding amount is greater than zero, ERPNext sends the reminder email by itself. I will cover Notifications in a separate video."

⚠️ *Dry-run note: the Notification option names and field names differ slightly by version. If it takes more than 30 seconds to show, drop this transaction and keep only the voiceover line.*

---

## Part 5 – Best Practices and How I Can Help (11:45–12:45)

🖥 Slide 1: three bullets. Slide 2: four bullets (Setup, Migration, Training, Custom Reports).

🎙 "Three tips that I use when implementing this for clients:

One. Fix the payment terms on the customer master. If terms are agreed once, every invoice gets the right due date.

Two. Check the Delivery Note list for To Bill every morning. Delivered but not billed is the most common leak in cash flow.

Three. Review the Accounts Receivable report every week, and send a reminder the day a payment becomes overdue. Early reminders get paid faster.

If your business has this problem, here is how I can help. I can set up your sales cycle, payment terms, and customer master. I can migrate your open invoices from Excel. I can train your sales and accounts team on this flow. And I can build custom receivable dashboards and automatic reminders, even on WhatsApp. Contact details are in the description."

---

## Part 6 – Summary and Closing (12:45–13:15)

🎙 "Quick recap. The use case: goods delivered, invoice not raised, payment late, and no follow-up.

The ERPNext solution: Payment Terms fixed on the customer, Quotation and Sales Order to agree everything upfront, Delivery Note with the To Bill status, Sales Invoice with an automatic due date, Payment Entry against the invoice, the Accounts Receivable report, and Dunning for reminders.

If this helped, please like and subscribe. Comment your industry and your biggest payment problem, and I'll make a video on it.

Next video: purchase control, how to stop uncontrolled buying with ERPNext approvals. See you there."

---

# PART C – UPLOAD PACKAGE

## Title
Late Payments Killing Your Cash Flow? ERPNext Sales Cycle Solution

## Thumbnail
- **Main text:** `LATE PAYMENTS? FIX CASH FLOW`
- **Layout idea:** left, a calendar with "20 DAYS" in red and a crossed-out invoice; right, your face and the ERPNext Accounts Receivable screen
- **Colors:** red for the problem, green for the solution, white bold text

## Description

```text
You delivered the goods 20 days ago, but the invoice is not even created. Sound familiar?

In this video, I explain a real business use case and show the complete ERPNext order-to-cash flow: quotation, sales order, delivery note, sales invoice with payment terms, payment entry, the Accounts Receivable report, and payment reminders.

ERPNext features covered:
- Payment Terms and Payment Terms Template
- Quotation and Sales Order
- Delivery Note status "To Bill"
- Sales Invoice created from Delivery Note
- Payment Entry and partly paid invoices
- Accounts Receivable report and ageing
- Dunning (payment reminders)

Chapters:
0:00 The problem
0:30 The use case
1:15 The ERPNext solution map
2:45 Demo: Payment terms and customer
4:00 Demo: Quotation and Sales Order
5:30 Demo: Delivery Note
6:30 Demo: Catch unbilled deliveries and create the invoice
8:00 Demo: Payment Entry
9:00 Demo: Accounts Receivable report
10:15 Demo: Payment reminder (Dunning)
11:45 Best practices and how I can help
12:45 Summary and next video

Need help implementing ERPNext for your business?
Contact: [your email / WhatsApp / LinkedIn]

Playlist: Business Problems Solved with ERPNext & Frappe

#ERPNext #SalesInvoice #CashFlow #AccountsReceivable #Frappe #ERP
```

## Tags
erpnext sales cycle, erpnext sales invoice, erpnext delivery note, erpnext payment terms, erpnext payment entry, erpnext accounts receivable report, erpnext dunning, order to cash erpnext, late payment solution, cash flow management, frappe erpnext tutorial, erpnext for beginners

## Pinned Comment

```text
What is your biggest payment problem: late invoices, late payments, or no follow-up? Comment your industry and I'll make a video on it. 👇
```

---

# PART D – SHORTS (Cut From This Video)

### Short 1 – Delivered but Not Billed (30 sec)
🎙 "Goods delivered, invoice forgotten. In ERPNext, open the Delivery Note list and filter by status To Bill. Every row is a delivery that is not yet invoiced. Check it every morning, and your cash flow improves immediately."

### Short 2 – Payment Terms (30 sec)
🎙 "Never calculate a due date by hand. Create a Payment Terms Template, like Net 15, and set it on the customer. Every quotation, order, and invoice gets the right due date automatically."

### Short 3 – Overdue Report (30 sec)
🎙 "Who owes you money, and for how many days? Open the Accounts Receivable report in ERPNext, set ageing based on due date, and you see every overdue customer on one screen."

---

# PART E – POST-RECORDING CHECKLIST

- [ ] Update the chapter timestamps from the final edit
- [ ] Add the 🏷 tags as lower-third text (use case → ERPNext feature)
- [ ] Zoom into: Payment Schedule due date (T6), Partly Paid status (T7), Age (Days) column (T8)
- [ ] Pause one second after each Submit so the status change is visible
- [ ] Add the end screen with the next video (V03) and the playlist
- [ ] Export 3 Shorts
- [ ] Verify against your ERPNext version: Payment Term fields, Dunning Type and Create → Dunning button, Accounts Receivable column names, and Notification field names
