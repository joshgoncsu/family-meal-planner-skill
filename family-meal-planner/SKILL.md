---
name: family-meal-planner
description: Plan a family's weekly meals and turn them into one store-split grocery list, track meat sales against price tiers, read grocery receipts into a spending log and price book, and run weekly and monthly budget reviews. Use this skill whenever someone wants to plan the week's dinners, school lunches or breakfasts, build or split a grocery list across stores, decide whether a meat sale is a good deal, log or categorize grocery receipts or Amazon orders, check grocery spending against a budget, cut grocery or snack costs, or get meal ideas from a pantry photo, even if they don't say "meal plan".
---

# Family Meal Planner

Most families overspend on groceries through frequency, not prices: many small trips across many stores, plus near-daily online orders. This skill replaces that with one weekly loop:

1. **Sales in.** Rate this week's meat sales against the family's price tiers.
2. **Plan out.** Plan the week's meals and turn them into one list, split by store.
3. **Shop once.** One planned shop; any extra trip is logged as an exception.
4. **Check and log.** Record what was cooked, skipped or tossed, and read the receipts.
5. **Review monthly.** Compare spending to the budget, look for trends, and recommend at most one change, backed by evidence.

The family decides; you bring evidence and recommendations. Never place orders, check out, or log into bank, card or store accounts.

## Where the family's data lives

This skill holds the method only. Each family's details live in their own files, kept wherever they work with Claude (a Claude Project, a folder, or a shared page's storage). Start from the blank files in `templates/`:

| File | Holds |
| --- | --- |
| `household.md` | People and ages, portion size, stores and loyalty cards, budget, weekly rhythm |
| `meals.md` | Dinner rotation, recipes and links, side list with kid-approved flags |
| `staples.md` | Breakfasts, lunches, snacks, default store per item |
| `stock-up.md` | Monthly household and paper goods list |
| `price-tiers.md` | Tracked meat and seafood cuts with tier prices |
| `price-book.md` | Prices actually paid, from receipts |
| `decisions.md` | Recommendations made, the family's answer, and the result |

If these files don't exist yet, run first-time setup (below) before planning. Read the files at the start of each session instead of relying on memory, and write changes back to them. See `examples/` for a filled-in fictional family.

**When some files are missing or thin, plan anyway.** A family in its first weeks won't have a price book, and may not have tiers. Don't stop to ask; fill the gaps and say what you did:

- **No price tiers:** rate prices with the method in `references/price-tiers.md` (USDA regional ad prices), and label each rating "provisional."
- **No price book:** estimate costs from typical regular prices and mark each estimate with `~`.
- **Item not in `staples.md`:** use the store roles in `household.md` (bulk and proteins at the warehouse club, produce, dairy and weekly items at the discount grocer). Add the item to `staples.md` after the shop.
- **Same price at several stores:** pick the core store already on the route.

Never copy a family's names, address, receipts or prices paid into this skill's own folder or any public repository.

## First-time setup

Collect the essentials in a short conversation, then fill in the templates:

1. Household: who eats at home, kids' ages, and how many servings to plan. Many families plan one or two extra servings for leftover lunches.
2. Dinners the whole family already likes, with their usual sides. Mark which sides the kids reliably eat.
3. Breakfasts, school and work lunches, and snacks bought every week.
4. Stores they use, which they'd rather use, and loyalty cards or memberships. Help them pick two or three core stores (usually one warehouse club and one discount grocer). Use `references/stores.md` to write each store's profile.
5. Monthly budget for groceries plus household essentials. Suggest a starting target from current spending and the USDA food plans (see `references/reviews.md`).
6. Weekly rhythm: planning day, shopping day, and when weekly ads come out.
7. Room-by-room household survey (kitchen, bathrooms, laundry, cleaning, kids) for the monthly stock-up list.
8. Proteins they grill, smoke or cook often, for the price tiers (see `references/price-tiers.md`).

Don't ask everything at once if the person is busy. Get enough to plan the first week, then fill the gaps over the next sessions.

## Weekly cycle

### 1. Sale report (the day the new weekly ads are posted)

Check each store's weekly ad for the tracked cuts and rate each price with `references/price-tiers.md`:

- **Stock up:** at or below the region's lowest sale prices. Buy extra and freeze it.
- **Good:** a typical sale price. Buy what the week needs.
- **Normal:** regular shelf price. Buy only if the meal is already planned.
- **Skip:** above normal. Swap the meal.

Report rules:

- Mark each store **confirmed** or **not posted yet**. Never show last week's price as current.
- Use the ad that will be in effect on the family's shopping day. Stores reset ads on different days. If a store's new ad starts before the shopping day, use its preview. If a sale ends before the shopping day, say so ("ends Thursday; buy on the way home Wednesday or skip"). Don't present it as available on shopping day.
- When the person just mentions a price in chat, rate it inline with its tier. A full report isn't needed.
- Label grade and size where they matter (USDA Choice vs ungraded steak, shrimp count per pound, skin-on vs skinless salmon). That way a cheaper, lower-grade item isn't mistaken for a deal.
- Flag prices that need a loyalty card or a clipped digital coupon.
- Apply the worth-the-drive rule (step 3) before recommending a store outside the core set.
- End with suggested weekend or grill meals that use the best deals, with sides from the family's side list.

### 2. Plan the week

Plan dinners first, then breakfasts, lunches and snacks from the staples list.

- **Which nights.** Plan the nights named in the household's weekly rhythm. A leftover night is fine and counts toward savings. When there are more candidate meals than nights, keep family suggestions and the meals built on this week's best deals, and drop repeats of meals cooked recently.
- **Every dinner gets a protein, a starch and a vegetable.** For informal meals (breakfast-for-dinner, snack plates), cover the same ground loosely: eggs or sausage as the protein, fruit or a raw veggie as the vegetable. Include at least one side the kids reliably eat, then add adult sides on top. Picky kids eating plain rice or raw peppers with ranch is a win. A plan the family won't eat wastes money.
- **Portions.** Plan the agreed number of servings. Leftovers become lunches, so count them as planned meals, not waste.
- **Build around the sale report.** A Stock up or Good protein should drive at least one dinner. At Stock up, list the extra to freeze as its own line ("+5 lb to freeze") and plan it into the next two or three weeks. If the rotation's recipe for it is out of season (a grilled dish in winter), use the same meal with an oven or stovetop method rather than dropping the deal.
- **Share perishables across the week.** If tomatoes, onions and cilantro are bought for tacos, use them in a salad or pico later in the week. Put fast-spoiling ingredients (cilantro, berries, fish) early in the week.
- **Match the side to the cooking method.** Grill or cast-iron sides on grill nights, oven sides on oven nights.
- **Rotate seasonal sides** in and out.
- **Flag prep-ahead meals** (marinades, thawing, slow cooker). Prep can only start after the ingredients are bought, so a meal needing an overnight marinade can't be the first night after the shop. Note the reminder for the night before.
- **Use family input.** Add meal suggestions from family members unless the household profile says they need approval. A parent's veto always wins. Show each suggestion's status: planned for a day, waiting for a parent's OK, saved for a lower-cost week, or needs recipe details.
- **Check the budget.** Estimate the week's cost from the price book. If the month is running over pace, lean on cheaper meals and on what's already in the house.
- **Use what's left over.** Last week's cooked-check log shows what went unused or was tossed. Plan around leftovers and adjust portions for meals that are often tossed.

### 3. Build the list and split it by store

1. Collect every ingredient from the plan, merge duplicates, and scale to the portions.
2. Add staples marked "weekly" in `staples.md`, plus "we're out of" requests and anything marked low. "When low" staples, spices and pantry items go on the list only after someone marks them low. Merge an out-of request with the same weekly staple instead of listing it twice.
3. Assign each item to its default store from `staples.md`. Change a default only when the price book shows a lower unit price elsewhere for the same product.
4. **Worth-the-drive rule.** Add a stop at a store outside the core set only when the savings there clear the family's threshold (start at $10 a trip) or the store is already on the route. Measure savings against the core store's regular price (from the price book, or the tier's Good line when there is no price book). A store that wins only one or two small items is shown as optional, not added to the trip. A stop that clears the threshold goes on the list as its own store section with the sale's end date.
5. Group by store, then by aisle in walking order (use category order until the family gives a store's aisle order). Show each store's estimated subtotal and the week's total against the weekly budget.
6. Mark items that need a loyalty card or a clipped coupon.

Compare household items by unit price (per sheet, per load, per ounce), not by package price.

### 4. Shop once

The goal is one planned shop a week. Midweek trips aren't forbidden, but log each one as an exception with its receipt. The monthly review shows how often they happen and what they were for. If the family has the fridge space, recommend buying longer-lasting produce (apples, citrus, carrots) for the end of the week.

If the family wants carts filled online, use the store's saved lists or reorder lists, or fill the cart in their own logged-in browser. Always stop before checkout: the family reviews the cart and places the order.

### 5. Cooked check and receipts

- At the end of the week, record each planned dinner as cooked, skipped or tossed. After a new meal is cooked, ask whether it's a keeper and add it to the rotation if so.
- Read receipts with `references/receipts.md`: every line gets one category (groceries, household essentials, non-essential), groceries get subcategories such as snacks, and each line updates the price book.

## Budget and pace warnings

The budget covers groceries plus household essentials. Non-essential items on the same receipts (clothes, toys, school supplies) are tracked on their own line and don't count against it.

Pace compares month-to-date spending with the share of the month that has passed. Count days through today: on day 17 of a 30-day month, pace is 57%, and $1,050 spent of $1,800 is 58%, about 1 point over. The weekly budget is the monthly target × 12 ÷ 52. A planned week that crosses into a new month is split by days.

| Status | Trigger | Action |
| --- | --- | --- |
| On track | At or under pace + 5 points | Nothing |
| Watch | More than 5 points over pace | Yellow warning; next plan leans on cheaper meals |
| Over pace | More than 10 points over pace, or 90% of the month spent | Red warning; next plan is a use-what-we-have week |

Holidays and hosting get separate budget lines agreed in advance, so a Thanksgiving dinner doesn't trigger warnings or distort trends. Tune the thresholds after the first month.

## Monthly review

On the first weekend of the month, follow `references/reviews.md` to produce the one-page monthly summary. Make a recommendation only when it's backed by enough data. The key rule: never recommend cutting a category (snacks, a store, a habit) until there are about four weeks of data showing the trend. When you do, give the numbers, and record the family's decision in `decisions.md` so next month can check whether it worked.

## Pantry photo

When someone sends a photo of their pantry, fridge or freezer, name what you can identify. Suggest one or two meals that use the items taking up the most room or closest to expiring, drawing on the family's rotation and side list where you can, and add anything still missing to the list.

## Output formats

**Weekly plan**

```
Week of <date> · est. $<total> of $<weekly budget> · month: <status>
Mon  <dinner> — <protein> · <starch> · <veg> (kids: <side>)   [prep: <note>]
...
Lunches: <per person or per child>
Breakfasts: <list>
Notes: <leftovers, suggestions and their status, vetoes honored, stock-up items to freeze>
```

Use `~` before an estimate that isn't from the price book.

**Store-split list**

```
<STORE> — est. $<subtotal>
  <aisle>: <item> (<qty>)  [card / coupon flag] [+<qty> to freeze]
...
Optional: <store> saves $<x> on <items> (below the trip threshold)
Reminders: <prep the night before, sale end dates>
```

**Sale report:** a table of cut · store · price per lb · tier · notes, with store statuses on top and suggested meals at the end.

## Guardrails

- Never place an order, check out, or access bank, card or store accounts. Spending data comes only from receipts and order histories the family shares.
- Never store payment card numbers or loyalty numbers from receipts.
- Recommend; don't decide. The family's choices and vetoes win.
- Be careful with young children: flag common choking hazards for small kids (whole grapes, nuts, popcorn, hot dog rounds) when they appear in meals planned for them.
- Keep upkeep low. If the family keeps skipping a step (receipts, cooked checks), simplify that step instead of nagging.
- Keep each family's data out of this skill and out of any public repository.

## Reference files

| File | Read when |
| --- | --- |
| `references/price-tiers.md` | Building or updating tiers, writing the sale report |
| `references/receipts.md` | Reading receipts or order histories, the price book |
| `references/stores.md` | Adding a store, ad cycles, loyalty pricing |
| `references/reviews.md` | Setting a budget, the monthly summary, recommendations |
