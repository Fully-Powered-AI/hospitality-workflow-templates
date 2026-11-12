# Menu input cost change review: an invented example

*Illustrative example with invented data.* The restaurant, the suppliers, the dishes, the prices and the quantities below are all invented. Larkfield Table is an invented restaurant with four established dishes. Its suppliers are called Supplier A, B and C. First come the inputs the chef supplied, in full, then the worksheet the workflow template returned.

## The inputs

### 1. Ingredient price list (prices per unit, without sales tax)

```
Ingredient,Unit,Prior price,Current price,Supplier,Date of change,Same product,Note
Butter,kg,9.00,10.50,Supplier A,2026-11-02,Yes,
Chicken thigh,kg,7.20,7.80,Supplier B,2026-11-04,Yes,
Cream,L,4.00,4.00,Supplier A,2026-11-02,Yes,
Lemon,kg,3.00,2.80,Supplier C,2026-11-03,Yes,
Olive oil,L,8.50,9.50,Supplier C,2026-11-03,Yes,
Potato,kg,1.20,1.30,Supplier C,2026-11-03,Yes,
Salmon fillet,kg,22.00,24.20,Supplier B,2026-11-04,No,Supplier B offers a different origin in place of the usual one
Tomato,kg,2.40,2.40,Supplier C,2026-11-03,Yes,
```

### 2. Recipes (one batch each)

```
Dish,Ingredient,Quantity,Unit
Roast chicken thigh,Chicken thigh,3.5,kg
Roast chicken thigh,Olive oil,0.2,L
Roast chicken thigh,Lemon,0.5,kg
Roast chicken thigh,Butter,0.2,kg
Seared salmon,Salmon fillet,2.0,kg
Seared salmon,Butter,0.4,kg
Seared salmon,Lemon,0.5,kg
Potato gratin,Potato,4.0,kg
Potato gratin,Cream,2.0,L
Potato gratin,Butter,0.2,kg
Potato gratin,Parsley,0.05,kg
Tomato soup,Tomato,5.0,kg
Tomato soup,Cream,1.0,L
```

### 3. Dish list

```
Dish,Portions per batch,Menu price
Roast chicken thigh,10,22.00
Seared salmon,10,29.00
Potato gratin,10,9.00
Tomato soup,20,8.00
```

### 4. Costing rules

Quantities in the recipes are as purchased. No other rule is stated.

### 5. Settings

Kitchen: Larkfield Table. Review date: 10 November 2026. For: the chef and the food-and-beverage manager. Prepared by: the food-and-beverage manager. Currency: dollars. No question threshold given. Whether the menu prices include sales tax: not stated.

## The worksheet

```
MENU INPUT COST CHANGE REVIEW: Larkfield Table, 10 November 2026

For: the chef and the food-and-beverage manager. Prepared by: the food-and-beverage manager. Currency: dollars.
Files used: ingredient price list (no date; changes dated 2 to 4 November 2026), recipes (no date), dish list (no date). Quantity basis: as purchased. Question threshold: 5%.
Dishes costed: 4. Affected by a price movement: 3. Not affected: 1. Price movements: 6. Ingredients with no movement: 2.

1. Price movements
Butter (kg, Supplier A): 9.00 to 10.50, +1.50, +16.7%. Changed 2026-11-02. Same product: Yes. Used in: Roast chicken thigh, Seared salmon, Potato gratin.
Olive oil (L, Supplier C): 8.50 to 9.50, +1.00, +11.8%. Changed 2026-11-03. Same product: Yes. Used in: Roast chicken thigh.
Salmon fillet (kg, Supplier B): 22.00 to 24.20, +2.20, +10.0%. Changed 2026-11-04. Same product: No. Used in: Seared salmon.
Chicken thigh (kg, Supplier B): 7.20 to 7.80, +0.60, +8.3%. Changed 2026-11-04. Same product: Yes. Used in: Roast chicken thigh.
Potato (kg, Supplier C): 1.20 to 1.30, +0.10, +8.3%. Changed 2026-11-03. Same product: Yes. Used in: Potato gratin.
Lemon (kg, Supplier C): 3.00 to 2.80, -0.20, -6.7%. Changed 2026-11-03. Same product: Yes. Used in: Roast chicken thigh, Seared salmon.

2. Dishes affected, largest percentage change first
Seared salmon (10 portions): cost per portion 4.91 to 5.40, +0.49, +10.0%. Menu price 29.00: cost 16.9% to 18.6%. Main driver: Salmon fillet, +4.40, 90% of the batch change. Status: Unconfirmed: Salmon fillet. Look first.
Roast chicken thigh (10 portions): cost per portion 3.02 to 3.27, +0.25, +8.3%. Menu price 22.00: cost 13.7% to 14.9%. Main driver: Chicken thigh, +2.10, 84% of the batch change. Status: Complete. Look first.
Potato gratin (10 portions): cost per portion 1.46 to 1.53, +0.07, +4.8%. Menu price 9.00: cost 16.2% to 17.0%. Main driver: Potato, +0.40, 57% of the batch change. Status: Incomplete: 1 line unpriced.

3. Worksheet: recipe lines for each affected dish
Seared salmon
  Salmon fillet: 2.0 kg at 22.00 to 24.20; line cost 44.00 to 48.40, +4.40.
  Butter: 0.4 kg at 9.00 to 10.50; line cost 3.60 to 4.20, +0.60.
  Lemon: 0.5 kg at 3.00 to 2.80; line cost 1.50 to 1.40, -0.10.
  Batch cost: 49.10 to 54.00, +4.90.
Roast chicken thigh
  Chicken thigh: 3.5 kg at 7.20 to 7.80; line cost 25.20 to 27.30, +2.10.
  Olive oil: 0.2 L at 8.50 to 9.50; line cost 1.70 to 1.90, +0.20.
  Lemon: 0.5 kg at 3.00 to 2.80; line cost 1.50 to 1.40, -0.10.
  Butter: 0.2 kg at 9.00 to 10.50; line cost 1.80 to 2.10, +0.30.
  Batch cost: 30.20 to 32.70, +2.50.
Potato gratin
  Potato: 4.0 kg at 1.20 to 1.30; line cost 4.80 to 5.20, +0.40.
  Cream: 2.0 L at 4.00 to 4.00; line cost 8.00 to 8.00, +0.00.
  Butter: 0.2 kg at 9.00 to 10.50; line cost 1.80 to 2.10, +0.30.
  Parsley: no price supplied; left out.
  Batch cost: 14.60 to 15.30, +0.70. Priced lines only.

4. Dishes not affected
Tomato soup.

5. Movements used in no supplied recipe
None.

6. Lines left out
Potato gratin, Parsley: no price supplied.

7. Questions for the chef and the buyer
1. Seared salmon: the price list marks Salmon fillet as not the same product as before, with the note "Supplier B offers a different origin in place of the usual one". The figures use 24.20 per kg. Is this the fillet the recipe is costed on, and will the kitchen buy it? Any allergen, dietary or food-safety effect of a changed product is for the chef and specialist staff and is not assessed here. (Chef)
2. Potato gratin: Parsley, 0.05 kg per batch, has no price in the price list, so the cost per portion of 1.46 to 1.53 covers the other three lines only. What is Parsley's price per kg? (Buyer)
3. Seared salmon: Salmon fillet is 90% of the batch change. Does 2.0 kg per 10 portions match what the kitchen uses? (Chef)
4. Roast chicken thigh: Chicken thigh is 84% of the batch change. Does 3.5 kg per 10 portions match what the kitchen uses? (Chef)

8. Defaults used
Question threshold: 5% (default). Whether the menu prices include sales tax was not stated; cost as a share of the menu price uses them as supplied. No costing rules were stated beyond the quantity basis.

Every figure traces to the price list with changes dated 2 to 4 November 2026, the recipe file and the dish list supplied. This review sets no menu price, changes no recipe, assesses no food-safety, allergen or dietary question, and sends and orders nothing.
```

The worksheet changes no file, orders nothing and sets no price. The chef and the food-and-beverage manager verify the costs and decide what to do about purchasing, the menu and prices.
