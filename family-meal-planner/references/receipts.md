# Receipts, order histories and the price book

Read every receipt line by line. Each line gets one category, groceries get a subcategory, and each priced line updates the price book. This is what makes the budget and the monthly trends work, so accuracy matters more than speed.

## Inputs

| Source | Typical form |
| --- | --- |
| Paper receipt | Photo, sometimes creased or cut off |
| Warehouse club or big-box app | Screenshot of the digital receipt |
| Online grocery order | Order confirmation or screenshot |
| Amazon | Monthly paste of order history (each adult's account) |

Record per receipt: store, location if shown, date, subtotal, tax, total, whether it was a planned shop or an exception, and the line items.

## Reading line items

- Receipts abbreviate. Expand codes to a plain product name ("GV WHL MLK GAL" → Great Value whole milk, 1 gal). When unsure, write the raw text and mark it unclear.
- Weighed items: record weight and price per pound.
- Discounts, coupons and loyalty savings: attach to the line they reduce, so unit prices stay true.
- Deposits, bag fees and tax: record separately; don't spread them into item prices.
- Returns and refunds: negative lines in the same category as the original.
- If a photo is unreadable, say which part and ask for a retake rather than guessing totals.

## Categories

| Category | Includes | Counts toward budget |
| --- | --- | --- |
| Groceries | All food and drinks | Yes |
| Household essentials | Paper goods, cleaners, laundry, dish soap, trash bags, toiletries, basic medicine cabinet items | Yes |
| Non-essential | Clothes, toys, school and office supplies, gifts, décor, electronics, anything else | No (own line) |

Grocery subcategories (track at least these): snacks, school lunch items, work lunch items, beverages, meat and seafood, produce, dairy, bakery, frozen, pantry. Families can add their own (for example, a parent's snack-style lunch items, so they aren't counted as kids' snacks).

When a line is ambiguous (a "kitchen" item that could be a gadget or a cleaner), ask once, then store the answer in a category map so the same product is never asked about again.

**Snacks**: chips, crackers, cookies, fruit snacks, granola and protein bars, single-serve packs, candy, and convenience-store snack runs. Count lunchbox snacks as snacks, and record whether they were bulk or single-serve; that split is usually where the savings are.

## Amazon order histories

1. Ask each adult to paste their order history for the month (the list view with item names, dates and prices).
2. Split multi-item orders into items.
3. Categorize each item the same way as a receipt.
4. Count orders per month and per week for the review, and note which household items were also on the warehouse-club list.

## Price book

Each priced grocery or household line adds a record:

```
| Date | Store | Product | Size | Price | Unit price | Unit | On sale? |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2026-11-02 | Discount grocer | Whole milk | 1 gal | $3.19 | $3.19 | gal | No |
```

Use the price paid in the store. Delivery-app prices are often higher than shelf prices and shouldn't set store defaults.

The price book powers:
- Store defaults: the store with the lowest regular unit price for a product.
- Price creep: a staple up 10% or more over its 8-week average is reported.
- Tier recalibration (see `price-tiers.md`).
- Weekly cost estimates for the plan.

## Privacy

Never record payment card digits, loyalty numbers, names or addresses printed on receipts. Keep only store, date, items, prices and totals.
