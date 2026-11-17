---
name: family-meal-planner
description: Plan a family's meals and turn them into one store-split grocery list, track meat sales against price tiers, read grocery receipts into a spending log and price book, and run weekly and monthly budget reviews. Use this skill whenever someone wants to plan dinners, school lunches or breakfasts, build or split a grocery list across stores, decide whether a meat sale is a good deal, log or categorize grocery receipts or Amazon orders, check grocery spending against a budget, cut grocery or snack costs, or get meal ideas from a pantry photo, even if they don't say "meal plan".
metadata:
  version: 0.1.5
---

# Family Meal Planner

Most families overspend on groceries through frequency, not prices: many small trips across many stores, plus near-daily online orders. This skill replaces that with one loop:

1. **Sales in.** Rate this week's meat sales against the family's price tiers.
2. **Plan.** Plan a set of meals.
3. **List.** Turn the plan into one list, split by store.
4. **Shop once.** One planned shop; any extra trip is logged as an exception.
5. **Check and log.** Check meals off as they are cooked, skipped or tossed, and read the receipts.
6. **New plan.** When the meals run out, clear the plan and make a new one.

Once a month, review: compare spending to the budget, look for trends, and recommend at most one change, backed by evidence.

Planning is not tied to a day. The plan runs out when the meals do, and that sets when the next one starts. The sale report, receipts and budget follow the calendar. A family might plan on Saturday evening and shop on Sunday; that is one example rhythm, not a rule.

The family decides; you bring evidence and recommendations. Never place orders, check out, or log into bank, card or store accounts.

## Where the family's data lives

This skill holds the method only. Each family's details live in their own files, kept wherever they work with Claude (a Claude Project, a folder, or a shared page's storage). Start from the blank files in `templates/`:

| File | Holds |
| --- | --- |
| `household.md` | People and ages, portion size, stores and loyalty cards, budget, rhythm, shared page address |
| `meals.md` | Dinner rotation, ingredients and amounts, side list with kid-approved flags, and the shared recipe book |
| `staples.md` | Breakfasts, lunches, snacks, default store per item |
| `household-list.md` | Monthly household list: household and paper goods |
| `category-map.md` | Product → category answers from receipt review, so each product is asked about once |
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

## Recipes: two places, one owner each

Keep each recipe in two places so nothing is edited twice.

- **Ingredients and amounts** live with whatever builds the grocery list (`meals.md`, or the planner's own data). Side amounts are per serving. Claude owns these.
- **Steps, source link, prep time and notes** live in one shared recipe book, with one section per main and per cooked side. Both parents can edit it.

Each meal and side links to its recipe book section. For a new recipe, Claude drafts the steps and the family corrects them. Boxed products (boxed mac and cheese, rice mixes) and plain fruit or snacks get no recipe.

**Auto-fill.** When a meal is added with a recipe link and no ingredients, a scheduled background run reads the recipe and fills in:

- ingredients sized to the household's servings. Pantry staples get the recipe's amount (2 tbsp); everything else gets a buy-sized amount;
- the prep time;
- a draft of the steps, in your own words.

Never overwrite anything a family member entered. If a site blocks reading, mark the meal "couldn't read the link" and ask the family to paste the ingredients. Don't work around a block. Run this as a scheduled run, not from a button (see "Shared page and buttons").

## First-time setup

Collect the essentials in a short conversation, then fill in the templates:

1. Household: who eats at home, kids' ages, and how many servings to plan. Many families plan one or two extra servings for leftover lunches.
2. Dinners the whole family already likes, with their usual sides. Mark which sides the kids reliably eat.
3. Breakfasts, school and work lunches, and snacks bought every week.
4. Stores they use, which they'd rather use, and loyalty cards or memberships. Help them pick two or three core stores (usually one warehouse club and one discount grocer). Use `references/stores.md` to write each store's profile.
5. Monthly budget for groceries plus household essentials. Suggest a starting target from current spending and the USDA food plans (see `references/reviews.md`).
6. Rhythm: when weekly ads come out, and the days the family usually plans and shops, if they have any. These are an example rhythm, not a rule.
7. Room-by-room household survey (kitchen, bathrooms, laundry, cleaning, kids) for the monthly household list.
8. Proteins they grill, smoke or cook often, for the price tiers (see `references/price-tiers.md`).
9. Freezer space and whether they have a vacuum sealer. This decides how much extra a Stock up deal is worth buying and whether a big family pack makes sense.
10. For each staple and monthly household list item, whether it is **brand-locked** or **interchangeable**. Brand-locked items are personal preferences (deodorant, toothpaste, a cereal a child insists on). For interchangeable items, the product the family buys now is the quality benchmark.

11. If the family uses a shared page, record its address in `household.md` (see "Shared page and buttons").

Don't ask everything at once if the person is busy. Get enough to plan the first week, then fill the gaps over the next sessions.

## The loop

The steps below match the numbered loop at the top.

### 1. Sale report (the day the new weekly ads are posted)

Check each store's weekly ad for the tracked cuts and rate each price with `references/price-tiers.md`:

- **Stock up:** at or below the region's lowest sale prices. Buy extra and freeze it.
- **Good:** a typical sale price. Buy what the week needs.
- **Normal:** regular shelf price. Buy only if the meal is already planned.
- **Skip:** above normal. Swap the meal.

Report rules:

- Mark each store **confirmed** or **not posted yet**. Never show last week's price as current.
- Use the ad that will be in effect on the day the family expects to shop. Stores reset ads on different days. If a store's new ad starts before that day, use its preview. If a sale ends before that day, say so ("ends Thursday; buy on the way home Wednesday or skip"). Don't present it as available on shopping day.
- When the person just mentions a price in chat, rate it inline with its tier. A full report isn't needed.
- Label grade and size where they matter (USDA Choice vs ungraded steak, shrimp count per pound, skin-on vs skinless salmon). That way a cheaper, lower-grade item isn't mistaken for a deal.
- Flag prices that need a loyalty card or a clipped digital coupon.
- Apply the worth-the-drive rule (step 3) before recommending a store outside the core set.
- End with suggested meals that use the best deals, with sides from the family's side list. If a plan is already underway, say which deals can wait for the next plan.

### 2. Plan a set of meals

Plan dinners first, then breakfasts, lunches and snacks from the staples list.

- **How many meals.** Plan the number of dinners the family wants before the next shop, and note any nights that need a quick meal. A leftover night is fine and counts toward savings. When there are more candidate meals than dinners, keep family suggestions and the meals built on this week's best deals, and drop repeats of meals cooked recently.
- **Every dinner gets a protein, a starch and a vegetable.** For informal meals (breakfast-for-dinner, snack plates), cover the same ground loosely: eggs or sausage as the protein, fruit or a raw veggie as the vegetable. Include at least one side the kids reliably eat, then add adult sides on top. Picky kids eating plain rice or raw peppers with ranch is a win. A plan the family won't eat wastes money.
- **Portions.** Plan the agreed number of servings. Leftovers become lunches, so count them as planned meals, not waste.
- **Build around the sale report.** A Stock up or Good protein should drive at least one dinner. At Stock up, list the extra to freeze as its own line ("+5 lb to freeze") and plan it into the next two or three weeks. If the rotation's recipe for it is out of season (a grilled dish in winter), use the same meal with an oven or stovetop method rather than dropping the deal.
- **Share perishables across the plan.** If tomatoes, onions and cilantro are bought for tacos, use them in a salad or pico later in the week. Put fast-spoiling ingredients (cilantro, berries, fish) early in the week.
- **Match the side to the cooking method.** Grill or cast-iron sides on grill nights, oven sides on oven nights.
- **Rotate seasonal sides** in and out.
- **Flag prep-ahead meals** (marinades, thawing, slow cooker). Prep can only start after the ingredients are bought, so a meal needing an overnight marinade can't be the first dinner after the shop. Note the reminder for the night before.
- **Fill the sides.** When a meal goes into the plan, fill its side slots from the meal's saved usual sides. Editing the meal's sides later doesn't change dinners already planned.
- **Use family input.** Add meal suggestions from family members unless the household profile says they need approval. A parent's veto always wins. Show each suggestion's status: planned for a day, waiting for a parent's OK, saved for a lower-cost week, or needs recipe details.
- **Check the budget.** Estimate the plan's cost from the price book. If the month is running over pace, lean on cheaper meals and on what's already in the house.
- **Use what's left over.** The last plan's cooked-check log shows what went unused or was tossed. Plan around leftovers and adjust portions for meals that are often tossed.

### 3. Build the list and split it by store

1. Collect every ingredient from the plan, merge duplicates, and scale to the portions.
2. Add staples marked "weekly" in `staples.md`, plus "we're out of" requests and anything marked low. "When low" staples, spices and pantry items go on the list only after someone marks them low. Merge an out-of request with the same weekly staple instead of listing it twice.
3. Assign each item to its default store from `staples.md`. Change a default only when the price book shows a lower unit price elsewhere for the same product.
4. **Worth-the-drive rule.** Add a stop at a store outside the core set only when the savings there clear the family's threshold (start at $10 in the week's savings at that store) or the store is already on the route. Measure savings against the core store's regular price (from the price book, or the tier's Good line when there is no price book). A store that wins only one or two small items is shown as optional, not added to the trip. A stop that clears the threshold goes on the list as its own store section with the sale's end date.
5. Group by store, then by aisle in walking order (use category order until the family gives a store's aisle order). Show each store's estimated subtotal and the week's total against the weekly budget.
6. Mark items that need a loyalty card or a clipped coupon.
7. Show each saved item by its short display name ("Trash bags", "Toothpaste"). The full product name with brand stays as the saved item, because pricing and receipt matching use it.

Compare household items by unit price (per sheet, per load, per ounce), not by package price.

#### Importing a voice-assistant list

Many families already keep a running shopping list in a voice assistant. Import it from screenshots or a paste so there is one list, not two. Check each item against recent receipts, what's at home and the current list. Treat anything added in the last day as a real need. Flag an item only when it was added before the last matching purchase, since it may already be bought.

**Brand-locked vs interchangeable.** Never swap a brand-locked product; only point out a cheaper store or a sale for that same product. For an interchangeable item, suggest a lower-cost alternative only when its quality matches the family's benchmark product (for example, no single-ply toilet paper against a premium two-ply), and say in one line why it compares. The family decides; record a switch only after they accept it.

#### At-home list

Keep one combined list of what's in the house, not separate pantry and fridge lists.

- Each item has one line and one status: **Have** or **Low**.
- Group by household shelf, not store aisle: fridge and freezer, spices, oils and sauces, baking and broth, snacks and drinks, paper and wraps, cleaning and laundry, bathroom and kids' care.
- Show shelves closed. Put "Running low" on top, always open.
- A Low item goes on the next shopping list. Buying it sets it back to Have.
- Staples never hide from the grocery list on their own. The planner tracks no quantities at home, so only someone marking an item Low or Have changes it.
- When adding an item, let the person pick the shelf, prefilled with your guess. Derive the store aisle from the shelf; don't ask for an aisle.
- Use short display names here too (see step 3, item 7).

### 4. Shop once

The goal is one planned shop per plan. Extra trips aren't forbidden, but log each one as an exception with its receipt. The monthly review shows how often they happen and what they were for. If the family has the fridge space, recommend buying longer-lasting produce (apples, citrus, carrots) for the end of the plan.

Hand the family a list per store. If a store's app has saved or reorder lists, you may point them out for the family to use. You never sign in to, open or fill a cart in a store account, and you never check out. The family builds the cart, reviews it and places the order.

### 5. Cooked check and receipts

- Check each dinner off as it is cooked, skipped or tossed, when it happens or at the next check-in. After a new meal is cooked, ask whether it's a keeper and add it to the rotation if so.
- Read receipts with `references/receipts.md`: every line gets one category (groceries, household essentials, non-essential), groceries get subcategories such as snacks, and each line is marked planned or unplanned. Each line updates the price book.
- Claude pre-fills only lines it is fairly sure of, or that are already in `category-map.md`, and asks about the rest. The family reviews line by line and marks the receipt reviewed. The budget counts a receipt only after that. Every fix is saved to the category map.

### 6. New plan when the meals run out

A plan is finished when every dinner is cooked, skipped or carried over. A plan never clears on its own. When every dinner is checked off, ask whether to start a new one. Either parent can start it, after a warning that the current plan clears. Past plans stay as history for variety checks and staples.

The new plan begins empty. Two things carry over from the old plan's uncooked dinners:

- **Bought dinners come along automatically.** A dinner counts as bought when every meat ingredient is still on hand, plus at least 2 other key ingredients (produce, dairy, bread, frozen; pantry staples don't count), or all of them if the meal has fewer. A meatless meal needs 3. Ingredients of a carried dinner that are still on hand are marked "already have", so they aren't bought again.
- **Dinners not shopped for are offered once** as optional picks, leaning toward clearing them. If the family skips them, drop them.

Then go back to step 2.

## Budget and pace warnings

The budget covers groceries plus household essentials. Non-essential items on the same receipts (clothes, toys, school supplies) are tracked on their own line and don't count against it.

Pace compares month-to-date spending with the share of the month that has passed. Count days through today: on day 17 of a 30-day month, pace is 57%, and $1,050 spent of $1,800 is 58%, about 1 point over. The weekly budget is the monthly target × 12 ÷ 52. A plan that spans two months is split by days. Budget weeks and months are calendar weeks and months, whatever day the family plans. Totals come from reviewed receipts (see `references/reviews.md`).

| Status | Trigger | Action |
| --- | --- | --- |
| On track | At or under pace + 5 points | Nothing |
| Watch | More than 5 points over pace | Yellow warning; next plan leans on cheaper meals |
| Over pace | More than 10 points over pace, or 90% of the month spent | Red warning; next plan is a use-what-we-have week |

Holidays and hosting get separate budget lines agreed in advance, so a Thanksgiving dinner doesn't trigger warnings or distort trends (see `references/reviews.md`). Tune the thresholds after the first month.

## Monthly review

On the first weekend of the month, follow `references/reviews.md` to produce the one-page monthly summary. Make a recommendation only when it's backed by enough data. The key rule: never recommend cutting a category (snacks, a store, a habit) until there are about four weeks of data showing the trend. When you do, give the numbers, and record the family's decision in `decisions.md` so next month can check whether it worked.

## Pantry photo

When someone sends a photo of their pantry, fridge or freezer, name what you can identify. Suggest one or two meals that use the items taking up the most room or closest to expiring, drawing on the family's rotation and side list where you can, and add anything still missing to the list.

## Output formats

**Plan**

```
Plan started <date> · <n> dinners · est. $<total> · weekly budget $<weekly budget> · month: <status>
1  <dinner> — <protein> · <starch> · <veg> (kids: <side>)   [prep: <note>]
...
Lunches: <per person or per child>
Breakfasts: <list>
Notes: <leftovers, suggestions and their status, vetoes honored, Stock up buys to freeze>
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

## Shared page and buttons

Some families keep the plan, list and logs on a shared web page.

- **One address.** Name the page's address in one place, in `household.md`, and refer to it from there. If the page is ever replaced, update every scheduled task prompt and runbook the same day, and retire the old page so nothing can write to it.
- **Buttons queue requests.** A button on a shared page can't start a run that needs the owner's computer. A run started from the cloud has no local browser, and many stores refuse cloud lookups. Design such a button as a queued request that the next run on the owner's computer picks up, and say so on the page.

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
| `references/receipts.md` | Reading and reviewing receipts or order histories, the category map, planned vs unplanned, the price book |
| `references/stores.md` | Adding a store, ad cycles, loyalty pricing |
| `references/reviews.md` | Setting a budget, the monthly summary, recommendations |
