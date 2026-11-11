# Group room block pickup review: trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (Hotel A, Group G, block BLK-A1, run date 2027-02-01). No client data was used. The five inputs were the settings, the block export, the booking pickup, the approved agreement summary and the room inventory, all as listed in that file. The assistant followed the instruction block and the output format in `member/template.md`.

## First run: what came out

A complete brief with every section of the output format: the header, pickup at a glance, the night and room type breakdown, counts that do not reconcile, outside the block, seven numbered questions for the account owner, two decisions, the three check lines and the closing line. The main figures:

- Blocked 101 room nights, confirmed in the block 62 (61.4%), 8.6 points below the stated minimum of 70%.
- Unfilled 39. The 15 unfilled on 2027-03-11 King are marked not settled.
- Tentative 8, not counted. If all were confirmed, unfilled would be 31.
- Cancelled 2, ignored. Rows of another block ignored: 1 in each file.
- Nights: 2027-03-09 76.0% (6 unfilled), 2027-03-10 73.8% (11), 2027-03-11 35.3% (22). Unfilled as a share of inventory: 6.7%, 12.2%, 24.4%.
- Two counts listed as unresolved: the export reports 10 for 2027-03-11 King against 9 confirmed in the bookings, and 2027-03-09 Twin has 6 confirmed against 5 blocked.
- Two reservations outside the block, R901 (night not in the block) and R902 (room type not in the block), counted nowhere.
- Check lines tied: 101 - 62 = 39; 63 = 62 + 1; 25 + 42 + 34 = 101; 19 + 31 + 12 = 62; 6 + 11 + 22 = 39.

## First run: what was observed

- Every required part was produced. Nothing in the inputs triggered a stop condition, so no stop was exercised.
- The figures matched the published example on every number, every question and both decisions. The only differences were in wording, such as how the facts in question 4 were phrased.
- No fact in either output is missing from the inputs. The 90-room inventory figures are sums of the inventory rows.
- A limit of this trial: the published example's output was displayed in the same file listing as its inputs, so it was seen before the inputs were worked. The figures were nevertheless worked from the rows, and the match is not a strong independent test.
- Only one input set was tried. Stops, the disputed-terms path, a missing summary, a passed release date and a failed tie-out were not exercised.

Places where the instructions were ambiguous and a judgement was needed:

1. A row above the block (2027-03-09 Twin) is called unreconciled in the exceptions section and in the instruction block, but steps 6 and 7 of the procedure define unreconciled only for a reported-pickup difference or an inventory shortfall. The output format has an "Unreconciled." marker for such a row. It was listed under "Counts that do not reconcile" and asked about, but the template does not say whether to put the "Unreconciled." marker on the room type line or whether the row's unfilled figure is "not settled". Here the unfilled figure is 0, so it did not matter.
2. Question (d) says "each night that has tentative rooms and unfilled rooms". It is not stated whether to ask per night or per room type row. One question per night was written.
3. The check line "Confirmed in block rows" is ambiguous. It was read as the total of confirmed room counts in the booking rows (63), which is 62 plus 1 above the block.
4. The template does not say whether a cancelled booking outside the block counts in "Cancelled room nights ignored". There was none here.
5. The file names in the "Inputs:" line are not defined. The names block.csv, pickup.csv, agreement.csv and inventory.csv were taken from the example.
6. The closing line and header use the titles from the settings exactly as given, so "Brief for the Revenue manager and Group-sales owner" is capitalised oddly. It follows the format.
7. Step 5 of the instruction block says "the block" for the pickup percent; the procedure's step 5 works the percent from confirmed in block over blocked. They agree.

Note added after the first run, 10 November 2026: the record above is unchanged. After an independent review the template's wording was edited: ambiguities 1, 2, 3, 4, 5 and 6 above are now settled in the text, and the instruction block was made to carry the file headers, the question order and the procedure's stops. That edit was run again; see the second run below.

## Second run, on the edited text

Later on 10 November 2026 a second independent review asked for further small edits, and the template was run again on its current text and the same invented example, with one change to the example's inputs: the three titles in the settings are now written in lower case ("revenue manager", "group-sales owner", "account owner for Group G"). The other inputs are unchanged.

What came out: a complete brief with every section, the same figures as before (blocked 101, confirmed in the block 62, 61.4%, 8.6 points below the stated minimum; unfilled 39 with the 15 on 2027-03-11 King marked not settled; tentative 8; unfilled 31 if all were confirmed; cancelled 2; one room above the block on 2027-03-09 Twin; two reservations outside the block; check lines tied). The room rows were also worked by a short script from the input rows and agreed. Differences from the first run, all in wording and following the edits:

- The titles are printed as supplied, in lower case, in the "For:" line and the closing line.
- Questions 4 and 5 set each room type's tentative rooms against that room type's own unfilled figure (King 2 against 8 on 2027-03-10; King 4 against 15, not settled, and Twin 2 against 7 on 2027-03-11).
- No date had passed, so the optional line "The brief cannot show whether rooms were released." was not printed.

What was observed:

- The run was done by the same assistant that edited the template, in the same session, and after the example's output had been seen, so it is weaker evidence than a run by a separate person or session. It shows the edited text is consistent with the example, not that it works on other data.
- Still only one input set. These edited paths were not exercised: the inventory shortfall referral, a blank release date or minimum, a one-night block, a passed date, a stop, the disputed-terms path and a missing summary.
- No ambiguity needed a judgement on this run beyond choosing the wording of question 5 to mark the unsettled figure.
