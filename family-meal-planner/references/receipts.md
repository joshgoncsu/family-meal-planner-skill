# Receipts, order histories and the price book

Read every receipt line by line. Each line gets one category, groceries get a subcategory, every line is marked planned or unplanned, and each priced line updates the price book. This is what makes the budget and the monthly trends work, so accuracy matters more than speed.

## Inputs

| Source | Typical form |
| --- | --- |
| Paper receipt | Photo, sometimes creased or cut off |
| Warehouse club or big-box app | Screenshot of the digital receipt |
| Online grocery order | Order confirmation or screenshot |
| Amazon | Monthly paste of order history (each adult's account) |

A long app order can be several screenshots. Attach them all to one receipt, but read them in small groups (see "Long receipts").

Record per receipt: store, location if shown, date, subtotal, tax, total, whether it was a planned shop or an exception, and the line items.

## Reading line items

- Receipts abbreviate. Expand codes to a plain product name ("GV WHL MLK GAL" → Great Value whole milk, 1 gal). When unsure, write the raw text and mark it unclear.
- Weighed items: record weight and price per pound.
- Discounts, coupons and loyalty savings: attach to the line they reduce, so unit prices stay true.
- Deposits, bag fees and tax: record separately; don't spread them into item prices.
- Returns and refunds: negative lines in the same category as the original.
- If a photo is unreadable, say which part and ask for a retake rather than guessing totals.

## Long receipts

Sending every photo or screenshot in one request can fail. Instead:

1. Read the images in small groups, a few at a time.
2. Tell each later group which lines were already copied, so they aren't read twice.
3. If a group fails with a service error, retry it once.
4. When all groups are read, check that the lines add up to the printed subtotal. Drop lines repeated where two photos overlap.

## Categories

| Category | Includes | Counts toward budget |
| --- | --- | --- |
| Groceries | All food and drinks | Yes |
| Household essentials | Paper goods, cleaners, laundry, dish soap, trash bags, toiletries, basic medicine cabinet items | Yes |
| Non-essential | Clothes, toys, school and office supplies, gifts, décor, electronics, anything else | No (own line) |

Grocery subcategories (track at least these): snacks, school lunch items, work lunch items, beverages, meat and seafood, produce, dairy, bakery, frozen, pantry. Families can add their own (for example, a parent's snack-style lunch items, so they aren't counted as kids' snacks).

## Planned or unplanned

Mark every line **planned** (on that week's list, or a known monthly household list item) or **unplanned**, alongside its category. Unplanned covers all spending, including non-essential and holiday lines. Categories alone don't show impulse or off-list buying; this does.

## Review and the category map

1. **Pre-fill carefully.** Pre-fill a line's category and planned/unplanned only when you're fairly confident or the product is already in the category map (`templates/category-map.md`). Otherwise leave the line blank with a short question. List the unsure lines first.
2. **The family reviews.** They go line by line, fix anything wrong, and mark the receipt reviewed. The budget counts a receipt only after it's reviewed.
3. **Save every fix.** Each correction goes into the category map as product → category, so each product is asked about once and pre-filled the same way later. A map entry always beats your own guess.

When a line is ambiguous (a "kitchen" item that could be a gadget or a cleaner), ask once. The answer goes in the map.

**Snacks**: chips, crackers, cookies, fruit snacks, granola and protein bars, single-serve packs, candy, and convenience-store snack runs. Count lunchbox snacks as snacks, and record whether they were bulk or single-serve; that split is usually where the savings are.

## Amazon order histories

1. Ask each adult to paste their order history for the month (the list view with item names, dates and prices).
2. Split multi-item orders into items.
3. Categorize each item the same way as a receipt.
4. Count orders per month and per week for the review, and note which household items were also on the warehouse-club list.

## Price book

Each priced grocery or household line adds a record:

```
| Date | Store | Product | Size | Regular price | Price paid | Deal | Unit price | Unit |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2026-11-02 | Discount grocer | Whole milk | 1 gal | $3.49 | $3.19 | Store sale | $3.19 | gal |
```

Use the price paid in the store. Delivery-app prices are often higher than shelf prices and shouldn't set store defaults.

Fill in the columns this way:

- **Size, unit price and unit**: record them only when the receipt shows them. Digital receipts from apps and online orders usually do. Paper receipts often don't, and that's fine. Don't ask the family for extra photos of labels or packages.
- **Regular price**: the shelf price before any sale or loyalty savings. Use it only when the receipt or the store shows it. If neither does, leave it blank rather than guessing.
- **Price paid**: what was paid after all savings.
- **Deal**: the discount type. Use one of: loyalty card, digital coupon, store sale, rollback, instant savings, or none.

Record the regular price and the deal type beside the price paid. A sale price on its own can look like the normal price, and that hides price creep when the sale ends.

Unit price matters before buying, when choosing a store for an item. It matters less after the trip, so don't work it out for logging alone. For a store-brand item, look up its size once on the store's product page when a comparison needs it.

The price book powers:
- Store defaults: the store with the lowest regular unit price for a product.
- Price creep: a staple up 10% or more over its 8-week average is reported.
- Tier recalibration (see `price-tiers.md`).
- Weekly cost estimates for the plan.

## Privacy

Never record payment card digits, authorization or register numbers, loyalty numbers, names or addresses printed on receipts. Keep only store, date, items, prices and totals.
