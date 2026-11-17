# Changelog

## 0.1.5 — 2026-11-16

- Planning is no longer tied to a day. The loop is: plan a set of meals, shop, check meals off as cooked, and when they run out, clear the plan and make a new one. The sale report, receipts and budget keep their calendar timing. Saturday plan and Sunday shop remain as an example rhythm only. The numbered loop at the top of SKILL.md now matches the section order. The example family's plan and rhythm match.
- Recipe auto-fill: a meal added with a link and no ingredients is filled in by a scheduled run (ingredients sized to the household, prep time, draft steps). It never overwrites family entries, and a blocked site is marked "couldn't read the link".
- Planning fills a meal's side slots from its saved usual sides. Later edits don't change dinners already planned.
- Importing a voice-assistant shopping list: items are checked against receipts, what's at home and the current list. Items added in the last day count as real needs.
- At-home list: the person picks the shelf and the store aisle is derived from it.
- Shared page: its address lives in one place (`household.md`). Buttons that need the owner's computer are queued requests. If the page is replaced, update every scheduled task and runbook the same day and retire the old page.
- Receipts: long receipts are read in small groups, retried once on a service error, and checked against the printed subtotal.
- Reviews: budget totals are computed live from reviewed receipts by receipt date, with no separate stored history total. Holiday lines can be show-only, with no target and no warning.
- "Shop once" no longer allows filling a cart. The planner hands the family a list per store and never signs in to a store account or checks out.
- Renamed the monthly list to "monthly household list" (`templates/household-list.md`, was `stock-up.md`), so "Stock up" means only the price tier.
- SKILL.md frontmatter has a version field.
- Privacy scan now runs on every push and pull request through GitHub Actions.
## 0.1.4 — 2026-11-09

- Receipts: every line is marked planned or unplanned, including non-essential and holiday lines. The budget view shows the unplanned share, and the monthly summary tracks it with its trend. No recommendation before four weeks of data.
- Recipes: each recipe is kept in two places. Ingredients and amounts live with the grocery list (side amounts per serving). Steps, source link, prep time and notes live in one shared recipe book both parents can edit. Boxed products and plain fruit or snacks get no recipe.
- Receipt review: Claude pre-fills a line only when fairly sure or when the product is in the category map, and asks about the rest, unsure lines first. The family reviews line by line, and the budget counts a receipt only after it is reviewed. Every fix is saved to the map, and a map entry beats Claude's guess. Long app orders can be several screenshots on one receipt. New `templates/category-map.md`.
- New week: it starts empty, with past weeks kept as history. Last week's uncooked dinners that were bought and are still in the house carry over, with "already have" marks. Dinners not shopped for are offered once as optional picks. Either parent can start the week, with a warning that the plan clears; otherwise the planner moves on by itself.
- Short display names: the full branded product name stays as the saved item for pricing and receipt matching. Long or branded items get a short name for lists. Staples and stock-up templates have a short name column.
- At-home list: one combined list with a Have / Low status per item, one line each, grouped by household shelf with "Running low" on top. A Low item goes on the week's list, and buying it sets it back to Have. Staples never auto-hide from the grocery list. Staples template has a shelf column.

## 0.1.3 — 2026-11-01

- Receipts: record size and unit price only when the receipt shows them; paper receipts often don't, and no extra photos are needed.
- Price book: new Regular price and Deal columns beside Price paid, so sale prices aren't mistaken for normal prices when spotting price creep.

## 0.1.2 — 2026-10-29

- Setup asks which items are brand-locked (personal preference) and which are interchangeable.
- Interchangeable items use the family's current product as the quality benchmark; cheaper alternatives are suggested only at comparable quality, with the reason.
- Staples and stock-up templates mark brand-locked items with [locked].
- SKILL.md worth-the-drive wording now matches the household template (the week's savings at that store).

## 0.1.1 — 2026-10-29

- Price tiers: pack size (regular vs value/family pack) is named on each tier and in the weekly report.
- Price tiers: how to build a 12-week baseline when past USDA issues can't be fetched (save each week's rows going forward, or download past PDFs).
- Price tiers: proxies for cuts that have no regional USDA row.
- Household template: the worth-the-drive threshold is the week's savings at that store, matching the method.
- Setup asks about freezer space and a vacuum sealer; the household template records them; pack size is judged case by case using them.

## 0.1.0 — 2026-10-29

- Meal-planning skill (`family-meal-planner/SKILL.md`): weekly loop of sale report, planning, store-split list, cooked check and monthly review.
- Four reference files: price tiers, receipts and the price book, store profiles, and budgets and reviews.
- Seven blank templates: household, meals, staples, stock-up, price tiers, price book and decisions.
- Fictional example family (the Riveras, Springfield) with a filled-in sample week.
- Privacy scan: gitleaks pre-commit hook with custom rules for phone numbers, email addresses, street addresses and card-like numbers.
