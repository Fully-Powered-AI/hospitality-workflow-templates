# Menu input cost change review: a trial on its invented example

- **Product:** Claude, run in Claude Code

Model: Claude Sonnet 5.5 (model ID claude-sonnet-5-5). Date: 2026-11-10.

The inputs are the invented example for this workflow template (Larkfield Table, four dishes, eight ingredients). No client data was used. The inputs used are the five inputs listed under "The inputs" in `public/example.md`: the ingredient price list, the recipes, the dish list, the costing rules (as purchased) and the settings (review date 10 November 2026, no question threshold given).

## How the run was done

The assistant read the template, followed the instruction block and the output format, and worked the figures from the inputs. One thing weakens the test: the example file was read in a single step, so its output was already on screen before the worksheet was produced. The figures were still recomputed from the inputs, and a separate arithmetic check was run afterwards, but this run is not a fully blind one.

## What came out

All eight sections were produced, in order, with the closing line. The figures were:

- Six price movements: Butter +16.7%, Olive oil +11.8%, Salmon fillet +10.0%, Chicken thigh +8.3%, Potato +8.3%, Lemon -6.7%. Two ingredients (Cream, Tomato) did not move.
- Seared salmon: cost per portion 4.91 to 5.40, +0.49, +10.0%; cost 16.9% to 18.6% of the 29.00 menu price; main driver Salmon fillet, +4.40, 90% of the batch change; Unconfirmed (Salmon fillet); Look first.
- Roast chicken thigh: 3.02 to 3.27, +0.25, +8.3%; 13.7% to 14.9% of 22.00; main driver Chicken thigh, +2.10, 84%; Complete; Look first.
- Potato gratin: 1.46 to 1.53, +0.07, +4.8%; 16.2% to 17.0% of 9.00; main driver Potato, +0.40, 57%; Incomplete, 1 line unpriced (Parsley has no price); below the 5% threshold, so not marked Look first.
- Tomato soup: not affected.
- No movement was unused by the recipes. One line was left out (Parsley, no price supplied).
- Four questions: the changed salmon product (chef), the missing Parsley price (buyer), and the main-driver quantities for the two Look first dishes (chef).
- Defaults used: threshold 5% (default); no costing rules beyond the supplied quantity basis.

## What was observed

- Every required part was produced. The assistant was not told to stop for anything: all headers matched, all units matched, no ingredient had two prices, and no yield was needed.
- The figures match the published example in every number, order and question. The only wording differences were small choices of phrasing. That agreement is weak evidence, for the reason given above.
- No fact appears in either output that is not in the inputs, with one exception noted next. The closing line says the price list is "dated 4 November 2026" (this wording was later changed; see "Edits made after this run"). The price list has no file date; that date is the latest "Date of change" in it. The template does not say what to do when the files carry no date, so this was a guess, and the example made the same one.
- Where the instructions were ambiguous or the assistant had to choose:
  1. The fenced instruction block says to use "the output format exactly" but does not contain the format. It sits in a separate section. A user who pastes only the fenced block into a product would not give the assistant the format.
  2. Two movements tie at +8.3% (Chicken thigh, Potato). The procedure gives a tie rule for dishes but none for movements. Price list order was used.
  3. The order of dishes within "Used in", and of recipe lines within the worksheet, is not stated. Recipe order was used.
  4. "Files used" asks for the files' dates, but the recipe file and dish list in the example carry none.
  5. The instruction block says to add the allergen, dietary and food-safety line to the dish status; the procedure and exceptions section put it with the question. It was placed in the question.
  6. A recipe ingredient absent from the price list (Parsley) is not a price movement, yet it appears under "Lines left out", whose format slot says "Dish or ingredient". This worked, but the slot could say "Dish and ingredient".
  7. Percentages are shown to one decimal place, but the example's 4.8% (from an unrounded 4.79%) and 10.0% (from 9.98%) depend on rounding the unrounded value; the template says this ("keep full precision") and it worked.
  8. Whether menu prices include sales tax is not asked for, though the template says price list prices are all with or all without tax.
- The instruction block is shorter than the procedure: it leaves out the duplicate-ingredient rule when prices are equal, the rule for a recipe dish missing from the dish list, the ordering of movements, and the tie rule for dishes. This run did not need them.
- The acceptance tests in the template are still proposed; this run covers only a normal run with one unpriced line, one changed product and one dish below the threshold. It did not exercise the stop conditions.

## Edits made after this run

After the run above, small wording edits were made to the template and the example, and they have not been run again: a line telling the reader to paste the output format with the instruction block; a tie rule for movements and the dish and movement ordering, the missing-dish, equal-price and blank "Same product" rules added to the instruction block; the allergen line moved in the block to the changed-product question; the closing line now uses the price list's range of dates of change when the file has no date; "no date" for files without one; the section 7 title; the "Lines left out" slot; and the Defaults line of the example (the quantity basis was supplied, not defaulted; the line above in "What came out" was corrected to match). A further round of small edits followed the independent review: the cost per portion is described as covering affected dishes only; a movement, an affected dish and the default quantity basis are defined in the instruction block, which now also says that other costing rules are not applied and are listed under Defaults used; a yield percentage is taken as a fraction (80% is 0.80); the worksheet section shows a pattern for every kind of left-out line; the settings now ask whether menu prices include sales tax, with the example's Defaults line saying it was not stated (which answers observation 8 above); the Parsley line in the example no longer carries a quantity; and the instruction block was re-wrapped. None of this was run again, and none changes a figure in the worksheet. The observations above describe the earlier wording.
