# Changelog

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
