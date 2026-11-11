# Menu input cost change review

Capability template, version 0.1.0.

## Purpose

Prepare one worksheet for the chef and the food-and-beverage manager when supplier prices have changed. From an ingredient price list, the kitchen's recipes and a dish list, the assistant lists every ingredient whose price moved, ties each movement to the quantity each recipe uses, works out the cost of each affected dish per batch and per portion before and after, names the dishes no movement touched, ranks the affected dishes by how far they moved, names the main driver of each and writes every gap in the records as a question for the chef. The assistant prepares and calculates. It sets no menu price, changes no recipe, orders nothing and gives no food-safety, allergen or dietary judgment. The chef and the food-and-beverage manager verify the costs and decide what happens to purchasing, the menu and prices.

## When to use it and when not to

Use it when updated supplier prices arrive and established dishes use the ingredients that moved. Run it again when the next price list arrives, when a recipe is corrected, or when the chef answers a question and wants the figures refreshed.

Do not use it:

- to decide what a dish should sell for. The review shows cost; the chef and the manager decide prices;
- to compare the prices a business charges with its competitors' or to test a proposed price list. That is price change review;
- to analyze spend by supplier across the whole payables ledger. That is supplier spend analysis;
- to cost a new dish that has no established recipe. There is nothing to compare against;
- to judge whether a substitute ingredient is safe, suitable for a diet or free of an allergen. That is for the chef and specialist staff;
- to estimate a yield, a trim loss or a unit conversion that the person has not supplied;
- to choose a supplier, place an order or contact anyone.

## Roles

- **Runs it:** the chef, a sous chef or the food-and-beverage manager.
- **Supplies the prices:** whoever receives the supplier's price list or invoice, usually the buyer or the chef.
- **Confirms recipes and quantities:** the chef.
- **Confirms that a changed product is the one a recipe means:** the chef.
- **Verifies the costs and decides purchasing, menu and price changes:** the chef and the food-and-beverage manager.
- **Changes a recipe, a price list or an order:** a person, after their decision.

## Inputs

1. **The ingredient price list.** Default column headers: `Ingredient`, `Unit`, `Prior price`, `Current price`, `Supplier`, `Date of change`. Optional headers: `Same product` (Yes or No) and `Note`. Prices are per `Unit`, all with or all without sales tax; the person says which. If the file is missing, stop. If a required header is missing or named differently, stop and ask which column holds what; never guess a column.
2. **The recipes.** Default column headers: `Dish`, `Ingredient`, `Quantity`, `Unit`. One row per ingredient line, quantity for one batch. An optional header `Yield %` is read only when the quantity basis is edible portion. If the file is missing, stop. If a required header does not match, stop and ask.
3. **The dish list.** Default column headers: `Dish`, `Portions per batch`. Optional header: `Menu price`, as it stands today. If `Menu price` is absent, cost percentages are not shown. If the person has not said whether menu prices include sales tax, they are used as supplied and the point is listed under "Defaults used". If the file is missing, stop. If a required header does not match, stop and ask.
4. **The costing rules,** in the person's words. The assistant applies two: the quantity basis, either "as purchased" (default; quantities already include trim and loss) or "edible portion" (each quantity is divided by its yield, taken as a fraction so that 80% is 0.80, to give the quantity bought), and the portion count in the dish list. Any other rule stated, such as a garnish allowance, a waste allowance or labor, is not applied and is listed under "Defaults used" as not applied.
5. **The settings:** the kitchen's name, the review date, who reads the review, who prepares it, the currency, whether menu prices include sales tax, and [your question threshold, default 5%]. Items in square brackets here and in the procedure are these settings. If a setting is missing, use the default and list it under "Defaults used".

Ingredient names, dish names and units are matched exactly after trimming spaces and ignoring capitals. The assistant never matches names that merely look alike and never converts one unit to another; a conversion exists only if the person supplies it, and then it is listed under "Defaults used".

The assistant works from the files and notes the person supplies. It needs no connection to a purchasing, inventory or point-of-sale system, and never asks for a password or a login code.

## The procedure

1. **Check the inputs.** Confirm every file and its headers. If an input is missing or a header does not match, stop and ask. Confirm that `Portions per batch` is a number above zero for each dish; a dish without one is left out and listed under "Lines left out".
2. **Read the price list.** For each ingredient, the change is current price minus prior price. The percentage change is the change divided by the prior price, shown to one decimal place. If the prior price is blank or zero, show the change but no percentage and add a question. An ingredient is a movement when its current price differs from its prior price; ingredients whose price did not move are counted, not listed. List the movements by percentage change, largest rise first and largest fall last; equal percentages go to the larger change in money, then to alphabetical order; a movement with no percentage goes last. If one ingredient appears twice with different prices, leave it out of every calculation, list it under "Lines left out" and add a question asking which supplier the kitchen buys from. If it appears twice with the same prices, use it once.
3. **Match the recipe lines.** For each recipe line, find its ingredient in the price list. If it is not there, the line is "no price supplied". If the recipe's unit differs from the price list's unit, the line is "unit differs". Both kinds are left out of the dish's cost and listed under "Lines left out". If the quantity basis is edible portion, divide the quantity by its yield, taken as a fraction (80% is 0.80), to get the quantity bought; a blank yield makes the line "yield not supplied" and it is left out. A recipe dish missing from the dish list is left out and listed.
4. **Cost each line.** The line cost before is the quantity bought times the prior price; the line cost after is the quantity bought times the current price; the change is the difference. Keep full precision; round only for display, to two decimal places for money. A line whose price did not move is still shown, with a change of +0.00.
5. **Cost each dish.** The batch cost before and after is the sum of its priced lines. The cost per portion is the batch cost divided by the portions per batch, before and after, with the change and the percentage change (one decimal place) of the portion cost. When a menu price is supplied, show the portion cost as a percentage of it, before and after, to one decimal place; the menu price is shown as supplied and never altered or suggested. A dish is affected when at least one priced line uses an ingredient that moved.
6. **Status of each dish.** Complete when every line is priced and no line is unconfirmed. Incomplete when one or more lines are left out; the figures then cover the priced lines only, and the status says how many lines are unpriced. Unconfirmed when a line uses an ingredient whose `Same product` is No; the figures use the supplied current price, and the status names the ingredient. A dish can be both. A blank `Same product` is read as Yes.
7. **Rank and flag.** List the affected dishes by percentage change in cost per portion, largest rise first and largest fall last. Ties go to the larger change in money per portion, then to alphabetical order. Mark a dish "Look first" when its percentage change, up or down, is at or above [your question threshold, default 5%].
8. **Name the driver.** For each affected dish, the main driver is the ingredient whose line change is largest in size. Show its line change and its share of the dish's net batch change, as a whole percentage. The share can exceed 100% when other lines offset it, and the worksheet says so. If the net change is zero, write "no net change".
9. **List the rest.** Dishes costed that no movement touched, by name. Movements that no priced recipe line uses. Lines left out, with the reason for each. Ingredients with no movement are counted in the header.
10. **Write the questions.** One numbered question per trigger below, in this order, each with its facts and the role who answers: a changed product (chef); a line left out, naming the dish, ingredient and reason (chef, or the buyer for a price); an ingredient with two prices or a missing prior price (buyer); each "Look first" dish, asking whether the quantity of its main driver in the recipe matches what the kitchen uses (chef). Write no other question. Recommend nothing about purchasing, menus or prices.
11. **Defaults and return.** List every default used, every costing rule not applied and every conversion the person supplied. Return the worksheet to the chef and the food-and-beverage manager only.

## Exceptions and stop conditions

- **A required file is missing, or a required header does not match:** stop and ask.
- **A unit differs between the price list and a recipe:** leave the line out, list it, ask. Never convert.
- **An ingredient has no price, or two different prices:** leave it out, list it, ask.
- **The quantity basis is edible portion and a yield is blank:** leave the line out, list it, ask. Never estimate a yield.
- **A product is marked as not the same as before:** show the figures, mark the dish Unconfirmed and ask the chef. Add that any allergen, dietary or food-safety effect of the change is for the chef and specialist staff, and is not assessed here.
- **A name that looks close but does not match exactly:** treat it as not found and ask; never guess that two names mean one thing.
- **Asked to set or suggest a menu price, change a recipe or a portion size, decide what to buy, pick a supplier, place an order, estimate a yield, assume a substitute is equivalent, or give an allergen, dietary or food-safety opinion:** decline. The chef and the food-and-beverage manager decide.

## Output format

```
MENU INPUT COST CHANGE REVIEW: [kitchen], [review date]

For: [chef] and [food-and-beverage manager]. Prepared by: [role]. Currency: [currency].
Files used: [price list, recipes, dish list, each with its date, or "no date" when a file carries none]. Quantity basis: [as purchased | edible portion]. Question threshold: [percentage].
Dishes costed: [n]. Affected by a price movement: [n]. Not affected: [n]. Price movements: [n]. Ingredients with no movement: [n].

1. Price movements
[Ingredient] ([unit], [supplier]): [prior] to [current], [change], [percentage]. Changed [date]. Same product: [Yes | No | not stated]. Used in: [dishes in recipe order, or "no supplied recipe"].
[Print "None." if no price moved.]

2. Dishes affected, largest percentage change first
[Dish] ([portions] portions): cost per portion [prior] to [current], [change], [percentage]. Menu price [price]: cost [percentage] to [percentage]. Main driver: [ingredient], [line change], [share]% of the batch change. Status: [Complete | Incomplete: [n] lines unpriced | Unconfirmed: [ingredient]]. [Look first.]
[Print "Menu price not supplied; cost percentages not shown." in place of the menu price clause when none was supplied. Print "None." if no dish is affected.]

3. Worksheet: recipe lines for each affected dish
[Dish]
  [Ingredient, lines in recipe order]: [quantity] [unit] at [prior price] to [current price]; line cost [prior] to [current], [change].
  [Ingredient]: [no price supplied | unit differs, price list [unit], recipe [unit] | yield not supplied | two prices]; left out.
  Batch cost: [prior] to [current], [change]. [Priced lines only, when incomplete.]
[Print "None." if no dish is affected.]

4. Dishes not affected
[Dish names, separated by commas.]
[Print "None." if every dish is affected.]

5. Movements used in no supplied recipe
[Ingredient names.]
[Print "None." if every movement is used.]

6. Lines left out
[Dish], [ingredient]: [reason: no price supplied | unit differs, price list [unit], recipe [unit] | two prices | yield not supplied | no portion count | not in the dish list | no prior price].
[Print "None." if nothing was left out.]

7. Questions for the chef and the buyer
1. [Question, with its facts.] ([Role who answers.])
[Print "None." if no trigger fired.]

8. Defaults used
[Setting or rule, with the value used. Costing rules not applied. Conversions supplied by the person.]
[Print "None." if nothing was defaulted.]

Every figure traces to the price list [dated [date] | with changes dated [first date] to [last date], when the file carries no date], the recipe file and the dish list supplied. This review sets no menu price, changes no recipe, assesses no food-safety, allergen or dietary question, and sends and orders nothing.
```

## Reviewer checklist

1. Every price in the worksheet matches the price list, and the change and percentage are right. (Buyer)
2. Every recipe quantity and unit matches the recipe file. (Chef)
3. For each affected dish, the line costs add to the batch cost and the batch cost divided by the portions gives the cost per portion. (Food-and-beverage manager)
4. No line is left out without a reason, and every left-out line has a question. (Chef)
5. The dishes are in the right order and the Look first marks follow the threshold. (Food-and-beverage manager)
6. Each main driver is the largest line change in its dish. (Food-and-beverage manager)
7. Nothing suggests a menu price, a recipe change, a supplier or an allergen or dietary view. (Chef)

## Acceptance tests

Proposed tests. None has been run.

1. **Normal run.** Three affected dishes, one unaffected, one ingredient with no price. Expected: all eight sections in order; the unpriced line left out and asked about; the other figures correct.
2. **Header mismatch.** The price list calls `Current price` `New price`. Expected: stops and asks which column holds what.
3. **Unit differs.** A recipe gives a quantity in grams where the price list is per kilogram. Expected: the line is left out, listed with both units, and asked about; no conversion.
4. **Two prices for one ingredient.** The list shows the same ingredient from two suppliers at different prices. Expected: left out of every calculation and a question to the buyer.
5. **Price reduction.** One ingredient falls in price. Expected: shown as a negative change; the dish ranks below the dishes that rose.
6. **Changed product.** `Same product` is No for an ingredient. Expected: dish marked Unconfirmed, a question to the chef, and a line saying allergen and dietary effects are not assessed.
7. **Edible portion with a blank yield.** Expected: the line is left out, never estimated.
8. **Zero prior price.** Expected: the change shown, no percentage, and a question.
9. **Asked for a menu price.** Expected: declines; shows cost per portion and, where a menu price was supplied, the cost percentage only.
10. **Asked whether a substitute is safe for a guest with an allergy.** Expected: declines and points to the chef and specialist staff.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare the menu input cost change review for the chef and the
food-and-beverage manager. You never set a menu price, change a recipe,
place an order, contact anyone, or give a food-safety, allergen or
dietary judgment. You never send or change anything; the chef and the
manager decide, and a person makes every change.

The user will supply: the ingredient price list (Ingredient, Unit, Prior
price, Current price, Supplier, Date of change; optional Same product and
Note); the recipes (Dish, Ingredient, Quantity, Unit; optional Yield %);
the dish list (Dish, Portions per batch; optional Menu price); the costing
rules; and the settings, including whether menu prices include sales tax.
Prices in the price list are all with or all without sales tax; the user
says which. If a file is missing or a required header does not match,
stop and ask which column holds what. Never guess a column. Never ask
for a password or a login code.

1. A movement is an ingredient whose current price differs from its prior
   price. An affected dish is one with at least one priced line that uses
   a movement. The quantity basis is as purchased unless the user says
   edible portion. Apply no other costing rule (a garnish or waste
   allowance, labor); list each under Defaults used as not applied.
   Names and units match exactly, ignoring capitals and spaces at the
   ends. Never match names that only look alike. Never convert units
   unless the user supplies the conversion.
2. For each ingredient: change = current minus prior; percentage = change
   divided by prior, one decimal place. No prior price or a zero prior
   price: show the change, no percentage, and ask. An ingredient that
   appears twice with different prices is left out and asked about; twice
   with the same prices, use it once. Order the movements by percentage,
   largest rise first, largest fall last; equal percentages go to the
   larger change in money, then alphabetical; no percentage goes last.
3. For each recipe line, find the price. No price, or a different unit:
   leave the line out, list it, ask. If the quantity basis is edible
   portion, divide the quantity by Yield %, taken as a fraction (80% is
   0.80), to get the quantity bought; a blank yield leaves the line out.
   Never estimate a yield. A recipe dish missing from the dish list, or
   with a zero or missing portion count, is left out and listed.
4. Line cost before = quantity bought x prior price; after = x current
   price. Batch cost = the sum of the priced lines. Cost per portion =
   batch cost divided by portions per batch. Keep full precision; round
   only to display (money to two decimals, percentages to one).
5. Show each dish's cost per portion before and after, the change and
   the percentage. If a menu price was supplied, show cost as a share of
   it, before and after; if the user has not said whether menu prices
   include sales tax, use them as supplied and list that under Defaults
   used. Never change or suggest a menu price.
6. Status: Complete; Incomplete (lines left out, figures cover priced
   lines only); Unconfirmed (Same product is No for a line's ingredient,
   name it). A blank Same product is read as Yes.
7. Rank affected dishes by percentage change in cost per portion, largest
   rise first; equal percentages go to the larger change in money per
   portion, then alphabetical. Mark Look first at or above [your
   question threshold, default 5%], up or down.
8. Main driver: the ingredient with the largest line change in the dish,
   with its share of the batch's net change as a whole percentage; say
   when other lines offset it.
9. List dishes not affected, movements used in no recipe and lines left
   out with reasons. Write questions only for: a changed product (the
   question adds that allergen, dietary and food-safety effects of a
   changed product are for the chef and specialist staff); a line
   left out; an ingredient with two prices or no prior price; each Look
   first dish (does the recipe quantity of its main driver match what
   the kitchen uses?). Where no ranking applies, keep the order of the
   files. Recommend nothing about buying, menus or prices.
10. Use the output format exactly, with all eight sections in order and
    "None." for an empty one. End with the closing line, naming the
    price list's date, or its earliest to latest Date of change when the
    file has no date. Return it to the chef and the food-and-beverage
    manager only.

If asked to set a price, change a recipe, choose a supplier, order, or
judge an allergen or dietary question, decline and say who decides.
Never adjust a figure to fit an expectation.
```

## What to customize

- Your costing rules: the quantity basis and, if edible portion, a yield for each ingredient.
- [your question threshold], the size of change at which a dish is flagged.
- The words your kitchen uses for units, so the price list and the recipes agree.
- Whether menu prices are shown.
- Who receives the worksheet, and who confirms a changed product.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried once on its invented example in Claude on 10 November 2026, with the record published beside it; the small edits made after that run have not been run again. Not tested in a client environment.
