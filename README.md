# Family Meal Planner skill

A Claude skill that turns a family's grocery routine into one weekly loop: rate this week's meat sales, plan the week's meals, build one grocery list split by store, shop once, then log what was cooked and what was spent. Once a month it reviews spending against a budget and recommends at most one change, backed by evidence.

It works best for families who shop at several stores, buy online often, and want to spend less without tracking every detail by hand.

## What it does

- **Weekly meal plans:** dinners, breakfasts, school and work lunches, with at least one kid-approved side every night.
- **Store-split grocery lists:** each item goes to its cheapest regular store. A worth-the-drive rule keeps one-item detours off the route.
- **Meat sale reports:** weekly ads rated against Stock up / Good / Normal / Skip price tiers built from USDA weekly retail ad surveys.
- **Receipt tracking:** every line sorted into groceries, household essentials or non-essential, with snacks tracked separately. A price book is built from what you actually paid.
- **Budget pace warnings** before the month runs over, with separate holiday lines.
- **Monthly one-page summary:** recommendations only after about four weeks of data.
- **Pantry photo to meal ideas.**

It never places orders, checks out, or connects to bank, card or store accounts.

## Install

1. Download this repository as a ZIP, or clone it.
2. Zip the `family-meal-planner` folder. The folder name must match the skill name.
3. In Claude, go to **Customize → Skills**, choose **Upload a skill**, and select the ZIP.

For Claude Code, copy the folder to `~/.claude/skills/family-meal-planner/`.

## Get started

Ask Claude something like "Help me set up weekly meal planning for my family." The skill walks through a short setup and fills in the files in `family-meal-planner/templates/`:

| File | What goes in it |
| --- | --- |
| `household.md` | People, servings, stores, budget, weekly rhythm |
| `meals.md` | Dinner rotation and side list |
| `staples.md` | Breakfasts, lunches, snacks |
| `stock-up.md` | Monthly household and paper goods |
| `price-tiers.md` | Tracked cuts and tier prices |
| `price-book.md` | Prices paid, from receipts |
| `decisions.md` | Recommendations and outcomes |

Keep your filled-in files somewhere private, such as a Claude Project or a private folder. Don't commit them to a public repository. See `family-meal-planner/examples/` for a filled-in fictional family.

## Repository layout

```
family-meal-planner/
  SKILL.md               The method: weekly loop, planning rules, list, budget, guardrails
  references/
    price-tiers.md       Building tiers from USDA ad surveys and receipts
    receipts.md          Reading receipts and order histories, the price book
    stores.md            Store profiles, ad cycles, picking core stores
    reviews.md           Budgets, the monthly summary, recommendation rules
  templates/             Blank family files
  examples/              A fictional family and an example week
```

## Optional tools

- **Flipp** (iOS, Android, web) collects weekly ads from many stores in one place. It's handy for a manual cross-check of the sale report.
- **Store apps** with saved or reorder lists (warehouse clubs, big-box stores) make repeat orders quick. You always place the order yourself.

## Privacy

This repo contains no real family data and must stay that way. A [gitleaks](https://github.com/gitleaks/gitleaks) pre-commit check blocks secrets, phone numbers, email addresses, street addresses and card-like numbers:

```
pip install pre-commit
pre-commit install
```

## Credits

Several ideas are adapted, with thanks, from the MIT-licensed **Parent Helper** skill by rdmgator12:
- Flagging a store that wins only one or two items, the basis of the worth-the-drive rule.
- Store profile fields.
- A list split by store with subtotals.
- Never checking out on someone's behalf.
- Letting a parent's preferences and vetoes always win.
- A fill-in-the-blank family profile with an example.

Price tier data comes from the USDA Agricultural Marketing Service weekly retail feature activity reports. Budget benchmarks come from the USDA Food Plans.

## Contributing

Improvements that help any family are welcome. Never include real names, addresses, receipts or prices you paid in an issue or pull request.

## License

MIT. See [LICENSE](LICENSE).
