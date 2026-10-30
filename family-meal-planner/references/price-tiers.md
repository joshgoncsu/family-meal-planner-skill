# Price tiers for meat and seafood

Use price tiers to say quickly whether this week's advertised price is worth acting on. Each tracked cut gets three boundaries; Normal is anything between Good and Skip.

| Tier | Meaning | Family action |
| --- | --- | --- |
| Stock up | At or below the lowest sale prices seen in the region | Buy extra and freeze |
| Good | A typical sale price | Buy what the week needs |
| Normal | Ordinary shelf price | Buy only if already planned |
| Skip | Above normal shelf price | Swap the meal |

## Where the numbers come from

### 1. USDA weekly retail feature reports (US families)

The USDA Agricultural Marketing Service publishes weekly surveys of prices advertised in grocery circulars and digital promotions. Each report has a national table (this week, last week, last year) and regional tables with price ranges and weighted averages, all per pound.

| Report | URL |
| --- | --- |
| Beef | https://www.ams.usda.gov/mnreports/AMS_3228.pdf |
| Pork | https://www.ams.usda.gov/mnreports/AMS_2868.pdf |
| Chicken | https://www.ams.usda.gov/mnreports/AMS_2756.pdf |

Historical issues are listed on USDA's ESMIS site and My Market News (https://mymarketnews.ams.usda.gov/).

Past issues may not be reachable for Claude: often only the current PDF at the URLs above loads. Two ways to get a multi-week baseline:

- **Build it forward (no extra work).** Each week's sale report saves that week's regional rows (date, cut, low, high, weighted average) to a small observations file. After about 12 weeks, rebuild the tiers from it. Until then, use one-week tiers labeled as such.
- **Download past issues.** The person downloads about 12 weekly PDFs per protein from My Market News and attaches them.

Regions: Northeast (CT, DE, MA, MD, ME, NH, NJ, NY, PA, RI, VT), Southeast, Midwest, South Central, Southwest, Northwest, Alaska, Hawaii. Use the family's region; fall back to the national table when a cut isn't listed regionally.

Rows are split by quality grade (Choice, Prime, branded, ungraded), pack size (regular vs value pack) and production claim (conventional, antibiotic-free, organic). Compare like with like: a family buying conventional Choice steak should use those rows.

**Pack size matters.** Regular and value/family pack averages can differ a lot (often 30% or more for boneless chicken, and ground beef in 1–2 lb vs 2–4 lb packs). Each tier names the pack size it assumes, and the weekly report says which pack an ad price is for, so a regular-pack price isn't judged against value-pack tiers.

Judge pack size case by case: compare the price per pound and whether the pack fits the family's servings. If the family has freezer space, and especially a vacuum sealer (see the household file), a big pack at a Stock up price can still win: plan what the week needs and freeze the rest in meal-sized portions. Without freezer space, a cheaper per-pound family pack that won't be used in time is not a deal.

### 2. Setting the boundaries

Use about 12 weeks of reports when you can; a single week is a rough first pass and should be labeled that way.

- **Stock up**: near the low end of the regional advertised price range across the weeks (roughly the lowest fifth of observations).
- **Good**: around the regional weighted average of advertised prices. These are already sale prices.
- **Skip**: about 25 to 35% above the Good line, near or above typical regular shelf price.

Round to store-style prices ($x.49, $x.99) so the table is easy to read in an aisle.

For cuts that are rarely advertised in the region (tri-tip in the Northeast, for example), use national rows and mark the tier low confidence.

Some cuts may have no regional row at all, or only a different form. Seen in Northeast reports:

| Cut | No regional row? | Proxy |
| --- | --- | --- |
| Flank steak | Often missing | National row; low confidence |
| Tri-tip | Often missing | National row; low confidence |
| Brisket, whole packer | Often missing | National row; Stock up only |
| Whole pork loin | Missing | Boneless pork loin roast row |
| Split chicken breast | Only antibiotic-free rows | Use them and say so, or national conventional row |

### 3. Seafood and items USDA doesn't track

USDA's feature reports don't cover shrimp or salmon. Start from current regular prices at the family's stores (warehouse club and discount grocer pages), set Good slightly below the cheapest regular price and Stock up at a clear sale level, and mark the tier low confidence. Track size and form: shrimp by count per pound (16/20 is colossal), raw vs cooked, shell-on vs peeled; salmon by species and skin-on vs skinless.

### 4. Recalibrating from receipts

After a month of receipts, compare prices actually paid with the tiers. Move a boundary when the family regularly sees prices outside it. Record each change with a date and reason in the tier file.

## Tier file format

```
| Cut | Grade / form | Stock up ≤ | Good ≤ | Skip > | Source | Confidence | Updated |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Ribeye, boneless | USDA Choice | $11.99 | $14.99 | $18.99 | USDA NE, 12 wk | High | 2026-10-29 |
```

Cuts that are flagged only at Stock up (an expensive brisket, for instance) keep the Good column blank and say so in the notes.

## Reading a weekly ad against tiers

1. Match the ad item to a tracked cut, grade and form. If the grade isn't stated, treat it as ungraded and say so.
2. Use the price per pound. Convert package prices with the package weight; skip items with no weight.
3. Note conditions: loyalty card, digital coupon, quantity limits, "buy 2", family-pack only.
4. Rate it and give the store's ad dates.
