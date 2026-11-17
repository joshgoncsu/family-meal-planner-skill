# Household

*Fill in during first-time setup. Keep it to what the planner needs.*

## People

*One row per person who eats at home. Ages help set portions.*

| Name | Age | Eats at home | Notes |
| --- | --- | --- | --- |
| `<name>` | `<age>` | `<yes / no / sometimes>` | `<notes, e.g. picky eater, allergies>` |

## Servings to plan

*Number of dinner servings to plan, and why.*

- Servings: `<number>`
- Reason: `<e.g. one extra serving for leftover lunches>`

## Freezer and storage

*Decides how much extra to buy on a Stock up deal and whether family packs make sense.*

- Freezer space: `<e.g. fridge freezer only / one chest freezer>`
- Vacuum sealer: `<yes / no>`

## Shared page

*Skip this if the family doesn't use one. Name the address here and nowhere else; everything else refers to it. If the page is replaced, update every scheduled task prompt and runbook the same day.*

- Address: `<address>`

## Stores

*Role is core, planned stops only, or deals only. See references/stores.md.*

| Store | Location | Role core/planned/deals only | Loyalty or membership | Ad cycle |
| --- | --- | --- | --- | --- |
| `<store>` | `<city or area>` | `<core / planned / deals only>` | `<none / card / paid membership>` | `<weekday to weekday; preview day>` |

## Budget

*Monthly target for groceries plus household essentials. Non-essential spending is tracked separately.*

- Monthly target: `$<amount>`

*Holiday and hosting lines, agreed in advance. Write "show only" for a line with no target and no warning.*

| Month | Amount | Notes |
| --- | --- | --- |
| `<month>` | `$<amount, or show only>` | `<notes>` |

## Rhythm

*The sale report and receipts follow the calendar. Planning and cooked checks follow the meals, not a day: plan, shop, check meals off, and plan again when they run out. Note the days the family usually plans and shops, as an example only.*

| When | What happens: sale report, planning, shopping, cooked check |
| --- | --- |
| `<day or trigger>` | `<step>` |

## Family input rules

*Do suggestions need approval? Who can veto?*

- Suggestions need approval: `<yes / no>`
- Who can veto: `<names>`. A parent's veto always wins.

## Worth-the-drive threshold

*Savings needed before a store outside the core set is worth a trip.*

- Threshold: `$10` in the week's savings at that store (default)

## Pace warning thresholds

*Points over pace before a warning shows.*

- Watch (yellow): more than `5` points over pace (default)
- Over pace (red): more than `10` points over pace, or `90%` of the month spent (default)
