# V01 – Stock Mismatch Problem? Fix It with ERPNext Stock Reconciliation

**Length:** ~14 minutes | **Demo company:** ABC Manufacturing Pvt. Ltd. | **Language:** Simple English (speak in Gujarati + English mix if you prefer; keep ERPNext terms in English)

**Format:** 🎙 = what you say | 🖥 = what you do on screen

---

## Before You Record

### Demo Data to Prepare

| Item | Value |
| --- | --- |
| Company | ABC Manufacturing Pvt. Ltd. |
| Warehouse | Main Store - ABC |
| Item | Steel Rod 10mm (Stock UOM: Nos) |
| Valuation rate | ₹500 per piece |
| Opening stock | 60 Nos (via Stock Reconciliation, purpose: Opening Stock) |
| Stock Entry (Material Receipt) | +40 Nos, so the system shows **100** |
| Physical count (story) | **80** |
| Expected difference | −20 Nos = −₹10,000 |
| Reorder Level / Qty | 50 / 100 (Main Store) |

### Setup Checklist

- [ ] Fresh site with ABC Manufacturing Pvt. Ltd. created
- [ ] Item and warehouse **not** created yet (you create them live)
- [ ] "Stock Adjustment" account exists (default in the chart of accounts)
- [ ] Excel screenshot of a messy stock sheet ready for the intro
- [ ] Browser zoom 110–125%, notifications off
- [ ] Do a dry run once so you know the menu names in your version

---

## Part 1 – Hook (0:00–0:30)

🖥 *Show a close-up of a stock sheet: system says 100, with a hand-written note "Physical: 80".*

🎙 "Your system says 100 items. But when you walk into the warehouse and count, there are only 80.

Where did the other 20 go? Who is responsible? And most importantly, how do you fix it, so it never surprises you again?

In this video, I'll show you exactly how ERPNext solves this problem, step by step."

---

## Part 2 – Introduction (0:30–1:30)

🖥 *Show your face or channel intro, then the title slide.*

🎙 "Hello everyone, welcome to my channel. In this series, I explain real business problems and show how to solve them using ERPNext and other Frappe products.

Today's problem: stock mismatch between your records and your warehouse.

By the end of this video, you will learn:
- Why stock mismatches happen
- How ERPNext tracks stock warehouse by warehouse
- How to correct the stock using Stock Reconciliation
- How to set a Reorder Level so you get alerted before stock runs out
- And how to read the Stock Ledger and Stock Balance reports

If you are a business owner, a store manager, or someone learning ERPNext, this video is for you. Let's start."

---

## Part 3 – The Business Story (1:30–3:00)

🖥 *Show the Excel sheet, a WhatsApp chat screenshot, and a paper register one after another.*

🎙 "Let me tell you a story. Imagine a company called ABC Manufacturing. They use steel rods in production.

The store keeper keeps stock in Excel. The purchase team gets the quantity on WhatsApp. The production team takes material and sometimes forgets to inform anyone.

Now, a customer order arrives. The sales team checks the sheet and says, 'We have 100 steel rods, no problem.' They promise delivery.

But when the production team goes to the shelf, only 80 are there. The order is delayed. The customer is unhappy. And the owner asks, 'Where did 20 rods go?'

This is not a rare problem. It happens in almost every business that does not control stock movements properly."

### Why Mismatches Happen

🎙 "There are five common reasons:
1. Material is issued but never recorded.
2. Material is received but entered late or entered twice.
3. Wrong quantity typed during entry.
4. Damage, theft, or wastage that nobody records.
5. Stock is moved between locations without any transfer entry.

The root cause is always the same: the physical movement and the system entry did not happen together."

---

## Part 4 – What the Solution Should Do (3:00–4:00)

🖥 *Show a simple diagram: Purchase → Warehouse → Production/Sales, with a "Stock Ledger" box in the middle.*

🎙 "So what should a good system do?

First, every stock movement must create a record, whether it is a purchase, a sale, a transfer, or a production use.

Second, stock must be tracked warehouse by warehouse, not just as one total number.

Third, when you count the stock physically and find a difference, there must be a proper way to correct it, with the value recorded in accounts.

And fourth, the system should warn you before the stock runs out.

ERPNext does all four. And for this, we use the Stock module of ERPNext."

---

## Part 5 – Which Frappe Product (4:00–5:00)

🖥 *Open ERPNext, go to the Stock workspace.*

🎙 "The product we will use today is ERPNext, specifically the Stock module.

Here in the Stock workspace you can see everything: Items, Stock Entry, Stock Reconciliation, Warehouses, and all the stock reports.

Behind all of this sits one important thing called the Stock Ledger. Every movement of stock, in or out, creates an entry in the Stock Ledger. This is the single source of truth.

Now let's see it in action."

---

## Part 6 – Live Demo (5:00–11:30)

### Step 1 – Create the Warehouse (5:00–5:45)

🖥 Go to **Stock → Warehouse → New**.
- Warehouse Name: `Main Store`
- Company: ABC Manufacturing Pvt. Ltd.
- Save.

🎙 "First, the warehouse. A warehouse in ERPNext is any location where you keep stock: a store, a rack, a factory floor, or even a branch.

I create a warehouse called Main Store under my company. Notice that ERPNext adds the company abbreviation at the end of the name. This helps when you have multiple companies."

### Step 2 – Create the Item (5:45–6:45)

🖥 Go to **Stock → Item → New**.
- Item Code: `Steel Rod 10mm`
- Item Group: Raw Material
- Unit of Measure: Nos
- Check **Maintain Stock**
- Valuation Rate: 500
- Save.

🎙 "Now the item. Item Code is Steel Rod 10mm. Item Group is Raw Material. Unit of Measure is Nos.

The most important checkbox here is Maintain Stock. If this is not checked, ERPNext will not track the quantity of this item. For anything you want to count in your warehouse, keep it checked.

I'm also adding a valuation rate of 500 rupees. ERPNext needs this to calculate the value of your stock."

### Step 3 – Add Opening Stock (6:45–7:45)

🖥 Go to **Stock → Stock Reconciliation → New**.
- Purpose: **Opening Stock**
- Item: Steel Rod 10mm, Warehouse: Main Store - ABC, Quantity: 60, Valuation Rate: 500
- Submit.

🎙 "Now I need to tell ERPNext how much stock I already have today. For this, I use Stock Reconciliation with the purpose Opening Stock.

I add my item, select Main Store, quantity 60, rate 500. Then I submit.

Remember this: nothing affects your stock until the document is submitted. Saving is not enough."

### Step 4 – Make a Stock Entry (7:45–8:45)

🖥 Go to **Stock → Stock Entry → New**.
- Stock Entry Type: **Material Receipt**
- Target Warehouse: Main Store - ABC
- Item: Steel Rod 10mm, Qty: 40, Basic Rate: 500
- Submit.
- Open the Item → show **Stock** dashboard showing 100.

🎙 "Now, let's say 40 more rods arrived from a supplier. I'll record it using a Stock Entry of type Material Receipt.

In practice, you would normally use Purchase Receipt for supplier purchases. But Stock Entry is the simplest way to show the movement in this demo.

After I submit, the item shows 100 pieces in Main Store. This is what the **system** says: 100.

Stock Entry also supports Material Issue to give material out, and Material Transfer to move between warehouses. Every one of these creates a Stock Ledger entry."

### Step 5 – The Problem: Physical Count Shows 80 (8:45–9:15)

🖥 *Cut to a photo or slide: "Physical count: 80".*

🎙 "Now the store manager does a physical count. He walks to the shelf, counts carefully, and finds only 80 pieces.

System: 100. Physical: 80. A difference of 20 pieces, which is worth 10,000 rupees at our rate.

Now we fix this the right way."

### Step 6 – Run Stock Reconciliation (9:15–10:30)

🖥 Go to **Stock → Stock Reconciliation → New**.
- Purpose: **Stock Reconciliation**
- Item: Steel Rod 10mm, Warehouse: Main Store - ABC
- Click the row; ERPNext shows **Current Qty: 100**
- Set **Quantity: 80**, keep Valuation Rate: 500
- Show **Difference Amount: −10,000**
- Check Difference Account (Stock Adjustment)
- Submit.
- Open **Accounting Ledger** from the submitted document (View → Stock Ledger / Accounting Ledger).

🎙 "I create a new Stock Reconciliation, this time with the purpose Stock Reconciliation, not Opening Stock.

I select the item and warehouse. Look here: ERPNext shows the current quantity, 100. In the quantity column I enter what I actually counted: 80.

Now see the difference amount at the bottom: minus 10,000 rupees. That's the value of the missing stock.

ERPNext posts this to the Stock Adjustment account. When I submit, two things happen. The stock becomes 80. And the accounts record a loss of 10,000.

This is important. Your stock and your finance are always connected. You cannot fix quantity without the value showing up in your books, and that is exactly how it should be.

Also, use Stock Reconciliation carefully. Do it only after a real physical count, and keep a record of who counted."

### Step 7 – Set the Reorder Level (10:30–11:30)

🖥 Open the Item → scroll to **Reorder** section → add row:
- Warehouse: Main Store - ABC
- Reorder Level: 50
- Reorder Qty: 100
- Material Request Type: Purchase
- Save.
- Then open **Stock → Stock Settings** and show **Auto Create Material Request**.

🎙 "Now let's make sure we never run out. Open the item and go to the Reorder section.

I add the warehouse, Main Store. Reorder Level: 50. Reorder Quantity: 100. And Material Request Type: Purchase.

This means: when stock in Main Store falls to 50 or below, ERPNext should raise a request to buy 100 more.

For this to happen automatically, go to Stock Settings and enable Auto Create Material Request. ERPNext then creates a draft Material Request through its scheduler, so your purchase team gets an automatic alert.

You can also see the shortage anytime from the Stock Projected Qty report."

---

## Part 7 – Reports (11:30–12:30)

### Stock Ledger (11:30–11:55)

🖥 Open **Stock → Reports → Stock Ledger**. Filter: Item = Steel Rod 10mm.

🎙 "Now the reports. First, Stock Ledger. This shows every movement of this item: the opening stock of 60, the receipt of 40, and the reconciliation that reduced 20.

You can see the date, the voucher type, the voucher number, and the balance after every entry. If anyone asks 'Why is the stock 80?', this report gives the full answer."

### Stock Balance (11:55–12:30)

🖥 Open **Stock → Reports → Stock Balance**. Filter by Warehouse.

🎙 "Next, Stock Balance. This gives you a snapshot: item by item, warehouse by warehouse, quantity and value.

This is the report your manager will open every week. Quantity: 80. Value: 40,000 rupees."

---

## Part 8 – Real-World Tips (12:30–13:15)

🖥 *Show a text slide with 4 bullets.*

🎙 "Before we finish, here are four tips that I follow when implementing this for clients:

One. Always record movements through documents. Never edit the stock directly.

Two. Do a cycle count regularly: count a few important items every week, instead of everything once a year.

Three. Keep Allow Negative Stock disabled in Stock Settings, so nobody can issue material that does not exist in the system.

And four. After every reconciliation, find out why the difference happened. Fixing the number is easy. Fixing the habit is what really protects your business."

---

## Part 9 – How I Can Help (13:15–14:00)

🖥 *Show a slide with 4 bullets: Setup, Migration, Training, Custom Reports.*

🎙 "If your company is facing this problem, here is how I can help:

- I can set up your items, warehouses, and stock structure in ERPNext.
- I can migrate your opening stock from Excel safely.
- I can train your store team so that every movement is recorded.
- And I can build custom reports and alerts, for example a daily low-stock email to your purchase manager.

Contact details are in the description."

---

## Part 10 – Summary and Closing (14:00–14:30)

🎙 "Let's quickly recap.

Stock mismatch happens when physical movement and system entry are not in sync.

In ERPNext, we create warehouses and items, record movements through Stock Entry, correct differences through Stock Reconciliation, set Reorder Levels for alerts, and verify everything through Stock Ledger and Stock Balance.

If this video helped you, please like it and subscribe to the channel. Comment below and tell me your industry and your biggest stock problem. I'll cover it in a coming video.

In the next video, we'll solve the problem of late invoices and late payments using the ERPNext sales cycle. See you there. Thank you."

---

## YouTube Upload Package

### Title
Stock Mismatch Problem? Fix It with ERPNext Stock Reconciliation

### Thumbnail
- **Main text:** `STOCK MISMATCH? FIXED`
- **Layout idea:** left side, a red "100" crossed out and a green "80"; right side, your face and the ERPNext screen
- **Colors:** red for problem, green for solution, white bold text

### Description

```text
Your system says 100 items, but the shelf has 80. Who is responsible and how do you fix it?

In this video, I explain how ERPNext tracks stock warehouse-wise, finds mismatches, and alerts you before stock runs out. We use a real business story and a complete live demo.

What you will learn:
- Why stock mismatches happen
- How to create Warehouses and Items in ERPNext
- How to add opening stock
- How to use Stock Entry
- How to correct stock using Stock Reconciliation
- How to set Reorder Level
- How to read Stock Ledger and Stock Balance reports

Chapters:
0:00 The problem
0:30 What you will learn
1:30 Business story
3:00 What the solution should do
4:00 ERPNext Stock module
5:00 Demo: Warehouse and Item
6:45 Demo: Opening stock
7:45 Demo: Stock Entry
9:15 Demo: Stock Reconciliation
10:30 Demo: Reorder Level
11:30 Stock Ledger and Stock Balance reports
12:30 Real-world tips
13:15 How I can help
14:00 Summary and next video

Need help implementing ERPNext for your business?
Contact: [your email / WhatsApp / LinkedIn]

Playlist: Business Problems Solved with ERPNext & Frappe

#ERPNext #StockManagement #Inventory #Warehouse #Frappe #ERP
```

### Tags (YouTube tag field)
erpnext stock reconciliation, erpnext stock management, erpnext inventory tutorial, stock mismatch, erpnext warehouse, erpnext reorder level, stock ledger erpnext, stock balance report, frappe erpnext tutorial, erpnext for beginners

### Pinned Comment

```text
What is your biggest stock problem: mismatch, theft, or late purchasing? Comment your industry and I'll make a video on it. 👇
```

---

## Shorts (Cut From This Video)

### Short 1 – "100 vs 80" (30 sec)
🎙 "System says 100. Shelf says 80. Don't edit the stock directly. In ERPNext, open Stock Reconciliation, enter the physical count, and submit. The stock is corrected, and the 10,000-rupee loss is posted to your books automatically."

### Short 2 – Reorder Level (30 sec)
🎙 "Never run out of stock again. Open your item, go to Reorder, set Reorder Level 50 and Reorder Quantity 100. Enable Auto Create Material Request in Stock Settings. ERPNext will now alert your purchase team before stock ends."

### Short 3 – Stock Ledger (30 sec)
🎙 "Who changed the stock? ERPNext's Stock Ledger shows every movement: date, document, quantity, and balance. Open it for any item and the full story is there."

---

## Post-Recording Checklist

- [ ] Add chapters to the description with the exact timestamps from the final edit
- [ ] Zoom into the screen during key clicks (Current Qty, Difference Amount)
- [ ] Add on-screen text for "Submit the document" and "Maintain Stock"
- [ ] Add the end screen with the next video (V02) and the playlist
- [ ] Export 3 Shorts
- [ ] Verify menu names and fields against your ERPNext version, since labels can differ slightly between versions
