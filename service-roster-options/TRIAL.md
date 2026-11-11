# Service roster options: tried once on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (settings, demand forecast, staffing rules and availability for an invented restaurant floor). No client data was used. I did not write the template. I read the template and the inputs first and followed the fenced instruction block and the output format. I then compared the result with the example's output and the reviewer checklist.

One limit on this trial: the example's output was printed on my screen in the same command as the template and the inputs, so I had seen it before I produced my own. I worked every figure out from the inputs and the rules, but I was not blind to the published answer.

## What came out

**SERVICE ROSTER OPTIONS: Restaurant floor, Friday 20 to Sunday 22 November 2026**

For: Restaurant manager. HR sees any option that relies on pending staff or shows a rule flag. Prepared Tuesday 10 November 2026 from the settings, the demand forecast (5 rows), the staffing rules (3 rows) and the availability file (10 staff).

Assumptions as supplied. Shift length: Dinner 6 hours, Lunch 5 hours. Rates: Server 16.00, Host 15.00. On-cost: 12 percent on every role. Rules checked: A (no person works more than 3 shifts in the window). Rules not checked here: B (closers do not open the next morning). No other pool was supplied, so there are two options.

Need by role and period.
- Fri 20 Nov Dinner: Server 4 (70 covers at 20 each, 3.5 rounded up). Host 2 (70 covers at 60 each, 1.17 rounded up).
- Sat 21 Nov Lunch: Server 3 (45 covers, 2.25 rounded up). Host 1.
- Sat 21 Nov Dinner: Server 8 (5 for 95 covers plus 3 for 36 event guests). Host 2 (95 covers).
- Sun 22 Nov Lunch: Server 3 (60 covers). Host 1.

Availability counts (confirmed / pending / unavailable / unknown).
- Server: Fri Dinner 4 / 1 / 1 / 1. Sat Lunch 5 / 1 / 1 / 0. Sat Dinner 4 / 2 / 0 / 1. Sun Lunch 4 / 1 / 1 / 1.
- Host: Fri Dinner 2 / 1 / 0 / 0. Sat Lunch 1 / 0 / 1 / 1. Sat Dinner 2 / 1 / 0 / 0. Sun Lunch 1 / 1 / 1 / 0.

Option 1: confirmed staff only.
- Server (staffed / uncovered / spare): Fri Dinner 4 / 0 / 0. Sat Lunch 3 / 0 / 2. Sat Dinner 4 / 4 / 0. Sun Lunch 3 / 0 / 1.
- Host: Fri Dinner 2 / 0 / 0. Sat Lunch 1 / 0 / 0. Sat Dinner 2 / 0 / 0. Sun Lunch 1 / 0 / 0.
- Pending staff needed: none.
- Rule A, checked as capacity: Server, 17 against 14 staffed, no flag. Host, FLAG: capacity 5 (H01 3, H02 2) against 6 staffed, a gap of 1. Headcounts left as they are.
- Cost: 112 staffed hours (Server 78, Host 34). Wages 1,758.00; with on-cost 1,968.96. Uncovered: 4 server places on Sat Dinner, 24 hours.

Option 2: confirmed and pending staff.
- Server: Fri Dinner 4 / 0 / 1. Sat Lunch 3 / 0 / 3. Sat Dinner 6 / 2 / 0. Sun Lunch 3 / 0 / 2.
- Host: Fri Dinner 2 / 0 / 1. Sat Lunch 1 / 0 / 0. Sat Dinner 2 / 0 / 1. Sun Lunch 1 / 0 / 1.
- Pending staff needed, at least 3 shifts: Server 2 (Sat Dinner, positive staffed minus confirmed; the cap adds nothing as 16 is below 17). Host 1 (periods add nothing; staffed 6 minus confirmed capacity 5).
- Rule A, checked as capacity: Server 21 against 16, Host 8 against 6, no flag.
- Cost: 124 staffed hours (Server 90, Host 34). Wages 1,950.00; with on-cost 2,184.00. Uncovered: 2 server places on Sat Dinner, 12 hours.

Option 3: not supplied (no other pool).

Comparison.
- Option 1: 20 shifts staffed, 4 uncovered (24 hours), no pending shifts, one rule flag (Host), 1,968.96 with on-cost.
- Option 2: 22 shifts staffed, 2 uncovered (12 hours), at least 3 pending shifts, no rule flag, 2,184.00 with on-cost.
- Difference: Option 2 staffs 2 more places for 215.04 more.
- For reference, filling every need would cost 2,399.04 with on-cost (wages 2,142.00; 136 hours, Server 102 and Host 34).

Unknowns that remain. S07 on Fri Dinner, H03 on Sat Lunch, S05 on Sat Dinner, S04 on Sun Lunch. Counted as unknown in every option.

Questions for the restaurant manager.
1. Sat Dinner is short in both options (4 places, or 2 with both pending servers). How do you want to handle the shortfall, and will you ask S05 for availability?
2. Option 1 breaks Rule A for hosts by one shift. Will you accept that, or work from Option 2?
3. Option 2 depends on at least 3 pending shifts (two servers on Sat Dinner, one host). Who will ask for those confirmations?
4. Rule B was not checked here. Will you check it when you name people?
5. HR sees both options, as Option 1 has a rule flag and Option 2 relies on pending staff. Which do you take to them?

Every figure traces to the 5 demand rows, the 3 staffing rules, the 10 availability rows and the settings above. The page names no one to work a shift, ranks no one, and sends and publishes nothing.

## What was observed

- Every required part was produced. Nothing in the inputs made the template stop, so no stop condition was exercised.
- Every figure matched the published example: needs, availability counts, staffing, capacity, hours, wages, on-cost and the reference cost. I recomputed them by hand from the inputs.
- Differences from the example, all small: I printed an "Option 3: not supplied" line, because the format says never to drop a section (the example omits it); I gave the working for rounded needs on more lines; I ordered the unknowns by staff code; and I worded the questions a little differently. The example's list of five questions and mine cover the same points.
- Facts not in the inputs: the manager's title ("Restaurant manager") is not in the settings; the template's format asks for a manager role, so both outputs supply one. The example's introduction also mentions a 60-seat dining room and a rehearsal dinner, which are not in the inputs, though its output does not rely on them.
- Where the instructions were ambiguous and I had to guess:
  - No staffing rule exists for hosts and event guests. The template only stops when a measure has no rule at all. I treated hosts as not needed for event guests. A one-line rule for this case is missing.
  - Option 3 handling: the format says never to drop a section, but step 6 says to give two options when no pool is supplied.
  - The cap rule counts "periods where that person is in the pool", which for Option 1 means confirmed only. That is only implied.
  - Whether a cap-driven pending shift is tied to a period. The template gives only a count, so the Host shift in Option 2 has no period.
  - The hours of uncovered places are not defined in the steps. I used uncovered places times period hours.
  - The questions: one for each uncovered period, flag, pending dependence, unchecked rule and the HR step. Whether blank cells need their own questions is not said; I folded S05 into the Sat Dinner question.
  - The input section says "three files" but there are settings plus three files.
- After the trial: the example's introduction was trimmed (it no longer mentions a 60-seat dining room or a rehearsal dinner), the example's need lines were given their working on every period, and the template was clarified on the two ambiguities above (a role with no rule for a measure; questions for blank cells). None of this was run again.
- The cap check does what it says, but its reading is heavy for a person: capacity is a count over people, not a check of a particular rota.
- Nothing was sent, no one was named for a shift, and no legal judgment was made. The acceptance tests in the template were not run as a set; only the ordinary window, rounding, minimum-free rounding, blank availability, a mixed-measure period and a strained cap occurred in this example.
