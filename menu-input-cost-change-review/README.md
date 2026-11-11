# Menu input cost change review

When supplier prices change, the chef and food-and-beverage manager get one worksheet: each price movement tied to the quantities in the supplied recipes, the cost per portion of every affected dish before and after, and questions for the chef. It sets no menu price.

*Capability template · Hospitality · Finance and accounting · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/menu-input-cost-change-review/)*

## The outcome

A delivery arrives at a new price and the question every kitchen asks follows: which of our dishes just got more expensive, and by how much? This capability answers it from your own records instead of from memory. Each ingredient whose price moved is listed with its old price, new price and change. Beside it sit the dishes that use it and the quantity each recipe calls for, so the movement turns into money per batch and then per portion.

The dishes come back ranked by how far their cost per portion moved, with the ingredient doing most of the work named for each. Where the records do not settle something, the worksheet says so and asks: an ingredient with no price, a unit that does not match, a product the supplier has changed, a recipe quantity worth checking against what the kitchen actually uses.

The review sets no menu price, changes no recipe, places no order and makes no judgment about food safety, allergens or diets. The chef and the food-and-beverage manager verify the costs and decide what to do about purchasing, the menu and prices.

## Who starts the work, and when

The chef, a sous chef or the food-and-beverage manager runs it when updated supplier prices arrive and established dishes use the ingredients that moved: a new price list, a changed invoice price, a supplier's notice. Run it again when the next price list lands or when a recipe is corrected. The chef reads the questions first, because the answers decide whether the figures can be relied on.

## What they supply

- **The ingredient price list.** One row per ingredient with its unit, prior price, current price and supplier, the date of the change and, if known, whether it is the same product as before.
- **The recipes.** One row per ingredient line: the dish, the ingredient, the quantity and the unit.
- **The dish list.** One row per dish: the portions a batch makes and, if you want cost shown as a share, the menu price as it stands today.
- **Your costing rules** in a few lines, such as whether recipe quantities are as purchased or edible portion.
- **The settings:** the review date, who reads it, the currency, whether your menu prices include sales tax and the size of change at which you want a dish flagged for a first look.

Each file comes with set column headings. If a heading does not match, the work stops and asks rather than guessing.

## What comes out

One worksheet in a fixed order. The price movements. The affected dishes with cost per portion before and after, ranked, each with its main driver and its status. Recipe line by recipe line, what each movement did to the batch. The dishes the movements did not touch. Movements that no supplied recipe uses. Lines left out and why. Numbered questions for the chef, each with its facts. The defaults used.

A good worksheet can be checked against the three files with a calculator, and the chef recognizes every dish and quantity on it.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/), where cost of sales is watched and a movement in input costs should reach the numbers before the month closes.
- [Procurement and suppliers](https://fullypowered.ai/functions/procurement-and-suppliers/), where the buyer needs to see which price changes matter to the kitchen and which do not.
- [Hospitality](https://fullypowered.ai/industries/hospitality/), where the dishes are established, the margin is thin and the supplier's price list changes more often than the menu.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where recipes and costing rules sit in the chef's head and a few files, and belong on a page.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more dishes, more sites or more suppliers make doing it by hand too slow.

It starts from supplier prices and recipes, and its question is what a dish costs now. [Price change review](https://fullypowered.ai/capabilities/price-change-review/) starts from the prices a business charges and tests proposed changes to them. [Supplier spend analysis](https://fullypowered.ai/capabilities/supplier-spend-analysis/) starts from payables and looks at where the money goes by supplier. [Budget versus actual variance commentary](https://fullypowered.ai/capabilities/budget-versus-actual-variance-commentary/) explains a month's gap to budget in the ledger.

## What has to change for your company

Write down your costing rules in the plain form the template reads: whether recipe quantities are as purchased or edible portion and, if edible portion, the yield for each ingredient. Settle the units once, so that the price list and the recipes use the same word for the same thing. Choose the size of change at which a dish is flagged. Decide whether menu prices are shown. Name who confirms that a changed product is the one the recipe means, because the template never assumes it. It runs in ChatGPT, Claude, Copilot or Gemini from files you supply, with no connection to your purchasing or point-of-sale systems.

## What has been checked

Fully Powered AI wrote this capability template from its own published map of the work. It was editorially reviewed on 10 November 2026. It was tried once on its invented example in Claude on 10 November 2026, and the record is published with it; small edits made afterward, the latest of which clarify its rules, have not been run again. It has not yet been tested in a client environment. It has not been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini. It gives no food-safety, allergen or dietary judgment.

Testing in your environment means running it on a past price change the chef remembers well, plus hard cases written in advance, each with its expected behavior: a renamed column, a unit in grams against a recipe in kilograms, an ingredient with no price, two prices for one ingredient, a changed product, a blank yield. The chef checks every dish against the files before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete capability template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the capability drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related capabilities

- [Price change review](https://fullypowered.ai/capabilities/price-change-review/)
- [Supplier spend analysis](https://fullypowered.ai/capabilities/supplier-spend-analysis/)
- [Budget-versus-actual variance commentary](https://fullypowered.ai/capabilities/budget-versus-actual-variance-commentary/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
