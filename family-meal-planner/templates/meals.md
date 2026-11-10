# Meals

*Dinner rotation and side list. Every dinner needs a protein, a starch and a vegetable, plus a kid-approved side.*

## Dinner rotation

*Add a row each time a new meal is cooked and the family says it's a keeper.*

| Meal | Protein | Usual sides | Kid-approved side | Prep ahead | Recipe book | Season |
| --- | --- | --- | --- | --- | --- | --- |
| `<meal>` | `<protein>` | `<sides>` | `<side the kids eat>` | `<e.g. marinate the night before>` | `<link to its recipe book section>` | `<all year / summer / winter>` |

## Ingredients

*Ingredients and amounts for each meal, used to build the grocery list. Claude owns this. Steps, source link, prep time and notes live in the shared recipe book, not here. Boxed products and plain fruit or snacks get no recipe.*

| Meal | Ingredient | Amount (for the planned servings) | Kind (meat / produce / dairy / bread / frozen / pantry) |
| --- | --- | --- | --- |
| `<meal>` | `<ingredient>` | `<amount>` | `<kind>` |

## Side list

*Type is starch, vegetable, salad or topping. Method is oven, grill, stovetop, cast iron or raw.*

| Side | Type (starch/vegetable/salad/topping) | Kid-approved (Y/N) | Method (oven/grill/stovetop/cast iron/raw) | Season | Amount per serving | Recipe book |
| --- | --- | --- | --- | --- | --- | --- |
| `<side>` | `<type>` | `<Y / N>` | `<method>` | `<season>` | `<amount>` | `<link, or none for raw and boxed sides>` |

## Recipe book

*One shared document, one section per main and per cooked side, that both parents can edit. Claude drafts the steps for a new recipe and the family corrects them.*

```
## <meal or side>
Source: <link>
Prep time: <minutes>
Steps: <numbered steps>
Notes: <what the family changed, what the kids think>
```
