# V01 (Revised) – Stock Mismatch Problem? Fix It with ERPNext Stock Reconciliation

**Length:** ~13 minutes | **Demo company:** ABC Manufacturing Pvt. Ltd. | **Style:** Use case → ERPNext solution → live demo (story kept to under 1 minute)

**Format:** 🎙 = what you say | 🖥 = what you do on screen | 🏷 = on-screen tag

**Retention rule for this version:** every demo step is tied back to the use case with a small on-screen tag (🏷 *Use case: 12 pieces issued, no entry* → *ERPNext: Material Issue*). The viewer always knows which problem the feature is solving.

---

## Before You Record

### Use Case Summary

**Company:** ABC Manufacturing Pvt. Ltd. uses Steel Rod 10mm in production.
**Problem:** The record says 100 pieces, but the shelf has 80. The 20 missing pieces came from three unrecorded movements:

| Cause | Pieces | ERPNext document that prevents it |
| --- | --- | --- |
| Issued to production, no entry | 12 | Stock Entry: Material Issue |
| Damaged, never recorded | 5 | Stock Entry: Material Issue (with reason) |
| Moved to another rack, no transfer | 3 | Stock Entry: Material Transfer |

### Demo Data

| Item | Value |
| --- | --- |
| Warehouses | Main Store - ABC, Rack B - ABC |
| Item | Steel Rod 10mm (Nos, Maintain Stock on) |
| Valuation rate | ₹500 per piece |
| Opening stock | 60 Nos (Stock Reconciliation → Opening Stock) |
| Material Receipt | +40 Nos → system shows **100** |
| Physical count | **80** → difference −20 = −₹10,000 |
| Prevention demo (new movements) | Issue 10 to production, Issue 2 damaged, Transfer 5 to Rack B |
| Result after prevention demo | Main Store **68**, Rack B **5** (total 73 = ₹36,500) |
| Reorder Level / Qty | 50 / 100 (Main Store) |

### Setup Checklist

- [ ] Fresh site with ABC Manufacturing Pvt. Ltd. created
- [ ] Item and both warehouses **not** created yet (create live; or create Rack B beforehand to save time)
- [ ] Stock Adjustment account available (default in the chart of accounts)
- [ ] Solution-map slide ready (see Part 3)
- [ ] The hook diagram ready (100 vs 80, with the three causes)
- [ ] Browser zoom 110–125%, notifications off
- [ ] Dry run once to confirm menu names and expense account on your version

---

## Part 1 – Hook (0:00–0:30)

🖥 Hook diagram, revealed in steps: "System says 100" and "Shelf has 80" → red "20 missing, ₹10,000" → three red boxes → "Fix: Stock Reconciliation".

🎙 "Your system says 100 items. But when you count the shelf, there are only 80.

Twenty pieces, worth ten thousand rupees, and nobody knows where they went.

Material issued, damaged, or moved without any entry. This happens in almost every manufacturing and trading business.

In this video, I'll show you how ERPNext fixes the gap, and how to make sure it never happens again."

---

## Part 2 – The Use Case in 45 Seconds (0:30–1:15)

🖥 Show a short slide: company name, item, and a table with the three causes.

🎙 "Welcome to the channel. In this series, I take a real business problem and solve it with ERPNext and other Frappe products.

Today's use case: ABC Manufacturing uses steel rods in production. Their record says 100, but the shelf has 80.

When we look at what happened, there are three causes. Twelve pieces went to production, with no entry. Five were damaged, and nobody recorded it. And three were moved to another rack, without a transfer entry.

So the problem is not the rods. The problem is that the stock movement and the system entry did not happen together.

Now let's see what ERPNext gives us to solve this."

---

## Part 3 – The ERPNext Solution Map (1:15–2:45)

🖥 Show the solution-map slide. Reveal one row at a time while you speak.

| Business need | ERPNext feature | Where |
| --- | --- | --- |
| Record every movement | Stock Entry (Material Receipt / Issue / Transfer) | Stock → Stock Entry |
| Track stock location-wise | Warehouse | Stock → Warehouse |
| Correct stock after a physical count, with accounting impact | Stock Reconciliation | Stock → Stock Reconciliation |
| Alert before stock runs out | Reorder Level + Auto Material Request | Item → Reorder, Stock Settings |
| Prove what happened | Stock Ledger, Stock Balance | Stock → Reports |

🎙 "Here is the complete solution in one slide. ERPNext solves this problem with five features.

One: Stock Entry. Every movement, whether it is a receipt, an issue, or a transfer, must be a document. This directly solves our twelve, five, and three pieces.

Two: Warehouses. ERPNext tracks stock location by location, so Rack B is separate from Main Store.

Three: Stock Reconciliation. When the physical count differs from the system, you correct it through a document, and the value goes into your accounts automatically.

Four: Reorder Level. ERPNext warns you before the stock ends.

And five: the Stock Ledger and Stock Balance reports. These give you proof for every movement.

Behind all of this sits one thing: the Stock Ledger. Every stock movement creates an entry there. It is the single source of truth.

Let's build this from scratch in ERPNext."

---

## Part 4 – Live Demo (2:45–11:45)

### Step 1 – Warehouses and Item (2:45–4:00)

🏷 *ERPNext: Warehouse + Item (Maintain Stock)*

🖥 **Stock → Warehouse → New**: `Main Store`, company ABC Manufacturing Pvt. Ltd. → Save. Repeat for `Rack B`.
🖥 **Stock → Item → New**: Item Code `Steel Rod 10mm`, Item Group Raw Material, UOM Nos, check **Maintain Stock**, Valuation Rate 500 → Save.

🎙 "First, two warehouses: Main Store and Rack B. A warehouse in ERPNext is any location where you keep stock: a store, a rack, a factory floor, or a branch.

Now the item: Steel Rod 10mm, Item Group Raw Material, unit Nos. The key checkbox is Maintain Stock. If it is off, ERPNext will not track quantity. And I add a valuation rate of 500 rupees, so ERPNext can calculate the stock value."

### Step 2 – Opening Stock and Receipt: System Shows 100 (4:00–5:00)

🏷 *ERPNext: Stock Reconciliation (Opening Stock) + Stock Entry (Material Receipt)*

🖥 **Stock → Stock Reconciliation → New**: Purpose **Opening Stock**, Steel Rod 10mm, Main Store - ABC, Qty 60, Rate 500 → **Submit**.
🖥 **Stock → Stock Entry → New**: type **Material Receipt**, target Main Store - ABC, Qty 40, Basic Rate 500 → **Submit**. Open the item's Stock dashboard: **100**.

🎙 "I add 60 pieces as opening stock, using Stock Reconciliation with the purpose Opening Stock. Then 40 pieces arrive, and I record them with a Stock Entry of type Material Receipt. In real life, supplier purchases go through Purchase Receipt, but this is the quickest way to show the movement.

Remember: nothing changes until the document is submitted. Saving is not enough.

Now the system shows 100 pieces in Main Store."

### Step 3 – The Gap Is Found (5:00–5:20)

🏷 *Use case: physical count = 80*

🖥 Slide: "System 100 | Physical 80 | Difference −20 = −₹10,000".

🎙 "The store manager counts the shelf: 80. The system says 100. A difference of 20 pieces, worth 10,000 rupees. Let's fix it the right way."

### Step 4 – Fix It: Stock Reconciliation (5:20–7:00)

🏷 *ERPNext: Stock Reconciliation → corrects stock and accounts together*

🖥 **Stock Reconciliation → New**: Purpose **Stock Reconciliation**. Add item and warehouse; ERPNext shows **Current Qty 100**. Enter **Quantity 80**, Valuation Rate 500. Show **Difference Amount −10,000** and the Difference Account (Stock Adjustment) → **Submit**. Open the ledgers from the submitted document.

🎙 "I create a new Stock Reconciliation, this time with the purpose Stock Reconciliation, not Opening Stock.

I select the item and warehouse. ERPNext shows the current quantity: 100. I enter the counted quantity: 80.

Look at the difference amount: minus 10,000 rupees. That is the value of the missing stock. And look at the Difference Account: Stock Adjustment.

When I submit, two things happen together. The stock becomes 80. And the accounts record a 10,000-rupee loss in Stock Adjustment.

This is the real strength of ERPNext. Stock and accounts are connected. You cannot fix the quantity without the value showing up in your books.

One rule: use Stock Reconciliation only after a real physical count, and keep a record of who counted."

### Step 5 – Prevent It: The Three Stock Entries (7:00–9:30)

🏷 *Now we prevent the same problem. Each cause has its own ERPNext document.*

🎙 "Fixing the number is only half of the solution. Now let's make sure it does not happen again. Remember our three causes? Each one has its own ERPNext document. Let's do all three."

#### 5A – Issued to Production → Material Issue (7:00–7:45)

🏷 *Cause: material issued, no entry → ERPNext: Material Issue*

🖥 **Stock Entry → New**: type **Material Issue**, source warehouse Main Store - ABC, Steel Rod 10mm, Qty **10** → Submit. Stock: 70.

🎙 "Cause one: material goes to production with no entry. Now the store keeper makes a Stock Entry of type Material Issue. Source warehouse Main Store, quantity 10. Submit. Stock is 70.

If you run manufacturing in ERPNext, this same movement is done through a Work Order and Material Transfer for Manufacturing, so the issue is linked to a production order. We will cover that in the manufacturing series."

#### 5B – Damaged Material → Material Issue with Reason (7:45–8:30)

🏷 *Cause: damaged, never recorded → ERPNext: Material Issue + reason*

🖥 **Stock Entry → New**: type **Material Issue**, Main Store - ABC, Qty **2**, expense account Stock Adjustment (or your damage/wastage account), remarks "Damaged during handling" → Submit. Stock: 68.

🎙 "Cause two: damaged material. Same Material Issue, quantity 2, and I write the reason in the remarks: damaged during handling. The cost goes to an expense account, so management can see how much money is lost to damage every month.

Now damage is no longer invisible. It is a number in your reports."

#### 5C – Moved to Another Rack → Material Transfer (8:30–9:30)

🏷 *Cause: moved, no transfer entry → ERPNext: Material Transfer*

🖥 **Stock Entry → New**: type **Material Transfer**, source Main Store - ABC, target Rack B - ABC, Qty **5** → Submit. Main Store 68, Rack B 5.

🎙 "Cause three: material moved to another rack. We use Stock Entry of type Material Transfer. Source: Main Store. Target: Rack B. Quantity 5.

Look at the result. Main Store has 68. Rack B has 5. The total is 73, and nothing was lost. The material just moved, and ERPNext knows exactly where it is.

This is the principle: every physical movement gets a document. If the box moves, the entry moves with it."

### Step 6 – Reorder Level: Alert Before Stock Ends (9:30–10:30)

🏷 *ERPNext: Reorder Level + Auto Material Request*

🖥 Open the Item → **Reorder** section → add row: Warehouse Main Store - ABC, Reorder Level 50, Reorder Qty 100, Material Request Type Purchase → Save. Open **Stock → Stock Settings** and show **Auto Create Material Request**. Optionally show **Stock Projected Qty**.

🎙 "Now, the alert. Open the item and go to the Reorder section. Warehouse: Main Store. Reorder Level: 50. Reorder Quantity: 100. Type: Purchase.

It means: when stock in Main Store falls to 50 or below, ERPNext should raise a request to buy 100 more.

For automatic requests, enable Auto Create Material Request in Stock Settings. ERPNext's scheduler then creates a draft Material Request for your purchase team.

You can also check the shortage anytime in the Stock Projected Qty report."

### Step 7 – Proof: Stock Ledger and Stock Balance (10:30–11:45)

🏷 *ERPNext: Stock Ledger + Stock Balance*

🖥 **Stock → Reports → Stock Ledger**, filter Item = Steel Rod 10mm. Then **Stock Balance**, filter by warehouse.

🎙 "Finally, the proof. In the Stock Ledger, filter the item. You can see every movement: opening stock 60, receipt 40, the reconciliation minus 20, the issue of 10, the damage of 2, and the transfer of 5. Each line shows the date, document number, and the balance after it.

If the owner asks, 'Why is the stock 68?', this report answers in ten seconds.

Now the Stock Balance. Main Store: 68 pieces, 34,000 rupees. Rack B: 5 pieces, 2,500 rupees. Total: 73 pieces, 36,500 rupees. This is the report your manager can open every week."

---

## Part 5 – Best Practices and How I Can Help (11:45–12:45)

🖥 Slide 1: three bullets. Slide 2: four bullets (Setup, Migration, Training, Custom Reports).

🎙 "Three tips that I use when implementing this for clients:

One. Never edit stock directly. Every movement must be a document.

Two. Do cycle counts: count a few important items every week instead of the whole warehouse once a year. And keep Allow Negative Stock off in Stock Settings, so nobody can issue material that is not in the system.

Three. After every reconciliation, find out why the difference happened. Fixing the number is easy. Fixing the habit protects your business.

If your company has this problem, here is how I can help. I can set up your items, warehouses, and stock structure. I can migrate your opening stock from Excel safely. I can train your store team on Stock Entry and Reconciliation. And I can build custom alerts, like a daily low-stock email to your purchase manager. Contact details are in the description."

---

## Part 6 – Summary and Closing (12:45–13:15)

🎙 "Quick recap. The use case: record 100, shelf 80, caused by three unrecorded movements.

The ERPNext solution: Stock Entry for every movement, Warehouses for locations, Stock Reconciliation to correct after a count, Reorder Level for alerts, and Stock Ledger and Stock Balance for proof.

If this helped, please like and subscribe. Comment your industry and your biggest stock problem, and I'll make a video on it.

Next video: late invoices and late payments, solved with the ERPNext sales cycle. See you there."

---

## YouTube Upload Package

### Title
Stock Mismatch Problem? Fix It with ERPNext Stock Reconciliation

### Thumbnail
- **Main text:** `STOCK MISMATCH? FIXED`
- **Layout idea:** left, a red crossed-out "100" and a green "80"; right, your face and the ERPNext screen
- **Colors:** red for problem, green for solution, white bold text

### Description

```text
Your system says 100 items, but the shelf has 80. Twenty pieces are missing. Who is responsible and how do you fix it?

In this video, I explain a real manufacturing use case and show the complete ERPNext solution: how to record every stock movement, correct stock after a physical count, set reorder alerts, and prove every movement with reports.

ERPNext features covered:
- Warehouse and Item (Maintain Stock)
- Stock Reconciliation (opening stock and physical count correction)
- Stock Entry: Material Receipt, Material Issue, Material Transfer
- Reorder Level and Auto Create Material Request
- Stock Ledger, Stock Balance, and Stock Projected Qty reports

Chapters:
0:00 The problem: 100 vs 80
0:30 The use case
1:15 The ERPNext solution map
2:45 Demo: Warehouses and Item
4:00 Demo: Opening stock and receipt
5:20 Demo: Fix with Stock Reconciliation
7:00 Demo: Prevent with Stock Entry (Issue, Damage, Transfer)
9:30 Demo: Reorder Level
10:30 Stock Ledger and Stock Balance
11:45 Best practices and how I can help
12:45 Summary and next video

Need help implementing ERPNext for your business?
Contact: [your email / WhatsApp / LinkedIn]

Playlist: Business Problems Solved with ERPNext & Frappe

#ERPNext #StockManagement #Inventory #Warehouse #Frappe #ERP
```

### Tags
erpnext stock reconciliation, erpnext stock management, erpnext inventory tutorial, erpnext stock entry, erpnext material transfer, erpnext material issue, stock mismatch, erpnext reorder level, stock ledger erpnext, frappe erpnext tutorial, erpnext for beginners

### Pinned Comment

```text
What is your biggest stock problem: mismatch, damage, or late purchasing? Comment your industry and I'll make a video on it. 👇
```

---

## Shorts (Cut From This Video)

### Short 1 – "100 vs 80" (30 sec)
🎙 "System says 100. Shelf says 80. Don't edit the stock directly. In ERPNext, open Stock Reconciliation, enter the physical count, and submit. The stock is corrected, and the 10,000-rupee loss is posted to your books automatically."

### Short 2 – Three Causes, Three Documents (30 sec)
🎙 "Material to production: Material Issue. Damaged material: Material Issue with a reason. Moved to another rack: Material Transfer. Three causes of stock mismatch, three ERPNext Stock Entries."

### Short 3 – Reorder Level (30 sec)
🎙 "Never run out of stock. Open your item, go to Reorder, set Reorder Level 50 and Reorder Quantity 100. Enable Auto Create Material Request in Stock Settings. ERPNext alerts your purchase team before stock ends."

---

## Post-Recording Checklist

- [ ] Update chapter timestamps from the final edit
- [ ] Add the 🏷 tags as lower-third text in the editor (use case → ERPNext feature)
- [ ] Zoom into the screen at key moments (Current Qty, Difference Amount, Stock Ledger)
- [ ] Add the end screen with the next video (V02) and the playlist
- [ ] Export 3 Shorts
- [ ] Verify menu names, fields, and the expense account on Material Issue against your ERPNext version
