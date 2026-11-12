# Service roster options

Workflow template, version 0.1.0.

## Purpose

Prepare two or three roster options for one service window, from the department manager's own forecast, staffing rules, availability and rates. For every role and period, each option shows the need, the number staffed, the number left uncovered and the number spare, then the cost at the rates and on-cost the manager supplied, any supplied rule it strains, and the staff it can only fill with people whose availability is still pending. The options are headcounts. The assistant prepares and compares; it never names who works, ranks or compares individuals, judges any working-time or employment-law limit, contacts staff, publishes a rota or changes a record.

## When to use it and when not to

Use it when expected occupancy, covers or event demand differs from the standing rota, before the week is committed, or again when availability or an event order changes.

Do not use it:

- to plan roles and budget for a year. That is the headcount plan;
- to check hours already worked or prepare pay. That is payroll preparation and timesheet review;
- to design the run of show for an event. That is the event plan;
- to decide whether a rota meets any law or agreement, to choose which person works, or to write a message to staff. Those stay with the manager and HR;
- when no forecast or no staffing rule exists. The manager supplies the ratios; the assistant does not invent them.

## Roles

- **Runs it and verifies the figures:** the department manager.
- **Approves the chosen roster:** the department manager, with HR where the property's process requires it.
- **Supplies availability:** the manager or supervisor who holds it, using staff reference codes.
- **Supplies forecasts and event orders:** reservations, food-and-beverage operations or the event manager.
- **Names who works each shift and publishes the rota:** the manager, outside this workflow template.

## Inputs

The assistant works from files and notes the person supplies. It needs no connection to a scheduling, payroll or booking system, and never asks for a password or a login code. Staff appear as reference codes (S01, H02); real names are not needed and should be left out.

1. **Settings** (notes): the department, the manager's role (for example "Restaurant manager"), the window, the periods and how long a shift is in each, the hourly rate for each role, the on-cost percentage, the rules to check, the rules not checked here, when HR sees an option, and today's date. If the window or the periods are missing, stop and ask. If a rate is missing, show that role's cost as "rate not supplied". If the on-cost is missing, show wages only and say so.
2. **Demand forecast.** Default headers: `date,period,measure,expected`. The measure is rooms occupied, covers or event guests, as the manager names it. One row for each period and measure. A period with no row is treated as not open and is not rostered.
3. **Staffing rules.** Default headers: `role,measure,per_staff,minimum_per_period`. One row for each role and measure: how many of that measure one person handles, and the fewest people the role needs in any open period. Repeat the minimum on every row of a role; if a role's rows disagree, stop and ask.
4. **Availability.** Default headers: `staff_ref,role`, then one column for each period, named `YYYY-MM-DD Period` exactly as in the demand forecast. Each cell is `confirmed`, `pending` or `unavailable`. A blank cell is unknown.
5. **Another pool,** optional. Default headers: `pool,role,date,period,count,hourly_rate`, for cover a lending department has confirmed. It is the only thing that makes a third option.
6. **Supplied rules.** A rule the assistant can check is a cap on shifts per person in the window. Any other rule is listed as not checked and left to the manager.

If a header does not match the defaults, or a period column does not match a period in the demand forecast, do not guess: stop, list the headers found and the headers expected, and ask which is which. A role is staffed only from the measures it has a rule for; a measure with no rule for a role adds nothing to that role, and the line says so. If a demand measure has no staffing rule for any role, stop and ask; never supply a ratio. If a qualification matters, such as a role that needs a certificate, the manager supplies it as a separate role (for example "Bar, licensed"); the assistant does not check qualifications otherwise.

## The procedure

1. **Check the inputs.** Confirm one window, the periods, the settings, the demand forecast, the staffing rules and the availability file, and the other pool if one was supplied. Count rows and staff, and report the counts in the header. Stop on any mismatch described under Inputs.
2. **Work out the need.** For each open period and role, add up, over the role's measures, the expected number divided by `per_staff`, each rounded up to a whole person. If the total is below the role's minimum, use the minimum. Show the working in the line ("5 for 95 covers plus 3 for 36 event guests").
3. **Count availability.** For each role and period, count confirmed, pending, unavailable and unknown. Unknown is never counted as available in any option.
4. **Build Option 1, confirmed staff only.** Staffed is the smaller of the need and the confirmed count. Uncovered is the need minus staffed. Spare is the confirmed count minus staffed.
5. **Build Option 2, confirmed and pending.** The pool is confirmed plus pending. Staffed is the smaller of the need and the pool. Uncovered and spare follow in the same way against the pool. Pending shifts needed, at least, is for each role the larger of two numbers: the periods' staffed minus confirmed, summed, where positive; and, when a cap applies, the staffed shifts minus the confirmed capacity from step 7. A shift a cap forces is counted as a total only and belongs to no period; say so.
6. **Build Option 3 only when another pool is supplied.** Add the pool's counts to Option 2's pool for the periods it names, at the pool's own rate, and label the pool in the option. With no pool supplied, print the Option 3 heading with "not supplied (no other pool)" and give two options. Never invent a lever, a swap or an agency.
7. **Check the supplied cap.** For each role and option, take each person in the option's pool and count the periods where that person is in the pool; the most shifts that person can work under the cap is the smaller of the cap and that count. The role's capacity is the sum over the people. In plain words: a cap limits how many shifts each person can take, so the people in the pool can only cover so many shifts in total, however many places are open. If capacity is below the shifts staffed, flag the role with the numbers and the gap. Leave the headcounts as they are; the manager decides. Name staff codes only to show a count, never to suggest who should or should not work.
8. **Price each option.** Staffed hours for a role and period is staffed times the period's hours. Wages are hours times the role's rate. With on-cost: wages times one plus the percentage. Round only at the end, to two decimals. Hours of uncovered places are the uncovered places times the period's hours, added up. Also show the cost of filling every need at the same rates, once, for reference.
9. **List the unknowns.** Every blank availability cell, by staff code and period. Say they are counted as unknown in every option.
10. **Write the questions.** One numbered question for each uncovered period, each rule flag, each pending dependence, each unchecked rule and the HR step, as the settings define it. A blank availability cell gets a question only when its period is short in some option; any other blank cell is listed under Unknowns and needs no question. Recommend no option unless the manager asks, and then only compare them again, with the same facts.
11. **Return the draft** to the manager. Nothing is sent to staff, HR or any system.

## Exceptions and stop conditions

- **A header or period column does not match:** stop and ask, as described under Inputs.
- **A demand measure has no staffing rule for any role, or a role's minimums disagree:** stop and ask. A measure that some roles have a rule for and others do not is not a stop; the roles without a rule add nothing for it.
- **Availability file lists a role with no staffing rule:** list the role as "no rule supplied" and leave it out of the options.
- **Every cell for a period is unknown or unavailable:** show the full need as uncovered in every option; do not invent staff.
- **Asked to name who should work, rank people, say who is best or worst, or compare individuals:** decline. The options are headcounts; the manager names people.
- **Asked whether a rota satisfies a working-time, break, minor-worker or employment-law limit, or a contract:** decline. The assistant applies only the rules supplied, as arithmetic, and says it makes no judgment on whether they are enough. Refer the question to HR.
- **Asked to send, post or publish the rota, contact staff, or change a record in a scheduling or payroll system:** decline and name the manager.
- **Asked to adjust a figure so an option looks better, or to raise the demand to match a hunch:** decline; show the supplied figures.
- **The files contain a real name next to a personal detail, a health note, a password or a login code:** do not repeat it; tell the person to replace it with a code or remove it.

## Output format

```
SERVICE ROSTER OPTIONS: [department], [window]

For: [manager role]. [HR rule from the settings]. Prepared [weekday date] from the settings, the demand forecast ([n] rows), the staffing rules ([n] rows) and the availability file ([n] staff).

Assumptions as supplied. Shift length: [period hours]. Rates: [role, rate]. On-cost: [percent / not supplied]. Rules checked: [list / none]. Rules not checked here: [list / none]. [Another pool: ... / No other pool was supplied, so there are two options.]

Need by role and period.
- [weekday date] [period]: [Role] [n] ([working]). [Role] [n].

Availability counts (confirmed / pending / unavailable / unknown).
- [Role]: [period] [n / n / n / n]. ...

Option 1: confirmed staff only.
- [Role] (staffed / uncovered / spare): [period] [n / n / n]. ...
- Pending staff needed: [none / ...].
- Rule [letter], checked as capacity: [role, capacity against staffed, no flag / FLAG and the gap]. [None supplied.]
- Cost: [n] staffed hours ([role n]). Wages [amount]; with on-cost [amount]. Uncovered: [places and periods], [n] hours.

Option 2: confirmed and pending staff.
- [same lines as Option 1]

Option 3: [pool name] / not supplied (no other pool).
- [same lines as Option 1]

Comparison.
- Option [n]: [n] shifts staffed, [n] uncovered ([n] hours), [pending shifts], [rule flags], [cost with on-cost].
- Difference: [plain statement of the added staffing and added cost].
- For reference, filling every need would cost [amount] with on-cost ([wages], [hours]).

Unknowns that remain. [Staff code and period for each blank cell / none].

Questions for the [manager role].
1. [Question.]

Every figure traces to the [n] demand rows, the [n] staffing rules, the [n] availability rows and the settings above. The page names no one to work a shift, ranks no one, and sends and publishes nothing.
```

Where a section has nothing to report, print the heading and "none" or "not supplied", as the format shows. Never drop a section, Option 3 included: with no other pool, print "Option 3: not supplied (no other pool)." and nothing under it.

## Reviewer checklist

1. Each need equals the rounded-up working shown, and no minimum has been skipped. (Manager)
2. The availability counts match the file, and blank cells appear only as unknown. (Manager or supervisor)
3. Staffed, uncovered and spare reconcile with need and the pool in every line. (Manager)
4. Wages, on-cost and the reference cost recompute from the hours and the supplied rates. (Manager, with finance if costs are reviewed there)
5. Every rule flag shows its capacity and staffed numbers, and rules not checked are listed. (Manager)
6. No person is named as the one to work, ranked or compared. (HR, where it is involved)
7. No judgment on any legal limit appears anywhere. (HR)
8. The manager has checked the rota, once people are named, against the rules that were not checked here. (Manager)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary window.** Complete files, all availability confirmed, no cap. Expected: two options with identical staffing, no uncovered places, costs recomputed.
2. **Rounding.** 70 covers at 20 per person. Expected: 4, shown as rounded up from 3.5.
3. **Minimum.** A quiet period whose need rounds to 1 against a minimum of 2. Expected: 2, with the minimum named.
4. **Blank availability.** Expected: counted as unknown in every option, listed under Unknowns, never as spare.
5. **Event measure added.** Covers plus event guests in one period. Expected: both parts shown and added for the same role.
6. **Cap strained.** Fewer confirmed hosts than shifts needed under the cap. Expected: a flag with capacity against staffed, headcounts unchanged, a question for the manager.
7. **Rule outside the checkable kind.** "Closers do not open the next morning." Expected: listed as not checked, with a question; no judgment.
8. **Header mismatch.** `Date` in place of `date`, or a period column that matches no period. Expected: stop; list headers found and expected.
9. **No staffing rule for a measure.** Expected: stop and ask; no ratio supplied.
10. **Another pool supplied.** Expected: a third option at the pool's rate, labeled.
11. **Asked who should work.** Expected: declines; headcounts only.
12. **Asked whether the rota is lawful.** Expected: declines, refers to HR, says only supplied rules were applied.
13. **Asked to send the rota.** Expected: declines; names the manager.
14. **A role with no availability rows.** Expected: full need uncovered in every option; no staff invented.

## Instructions for the AI assistant

```
You prepare roster options for a department manager from the figures
the manager supplies. You compare; the manager decides. You never name
who should work a shift, rank or compare individuals, judge whether a
rota meets any working-time or employment-law limit, contact staff,
publish a rota, send anything or change any record. You never ask for a
password or a login code and need no access to any system. Staff appear
as reference codes only.

The user will supply: settings (department, window, periods and shift
hours, hourly rates, on-cost percentage, rules to check, rules not to
check here, when HR sees an option, today's date, the manager's role);
a demand forecast (date, period, measure, expected); staffing rules (role, measure,
per_staff, minimum_per_period); availability (staff_ref, role, then one
column per period named "YYYY-MM-DD Period" with confirmed, pending or
unavailable; blank is unknown); optionally another pool (pool, role,
date, period, count, hourly_rate). If a header or period column does not
match, if a measure has no staffing rule for any role, or if a role's
minimums disagree, stop, say exactly what you found and what you
expected, and ask. A role is staffed only from the measures it has a
rule for; a measure with no rule for that role adds nothing to it, and
you say so in the line. Never supply a ratio, a rate or a rule.

1. Need: for each open period and role, add expected / per_staff
   rounded up, over the role's measures; if below the minimum, use the
   minimum. Show the working.
2. Count confirmed, pending, unavailable and unknown for each role and
   period. Unknown is never available.
3. Option 1, confirmed only: staffed = min(need, confirmed); uncovered =
   need - staffed; spare = confirmed - staffed.
4. Option 2, confirmed and pending: the same against confirmed plus
   pending. State the pending shifts needed, at least: per role, the
   larger of the sum of positive (staffed - confirmed) and, when a cap
   applies, staffed shifts - confirmed capacity. A cap-forced shift is a
   total only and belongs to no period; say so.
5. Option 3 only if another pool is supplied: add it at its own rate and
   label it. Otherwise print "Option 3: not supplied (no other pool)."
   Invent no lever.
6. Cap check, per role and option: each person's most shifts = min(cap,
   periods where that person is in the pool); capacity = the sum. If it
   is below the staffed shifts, flag it with both numbers. Say in plain
   words that a cap limits each person's shifts, so the pool covers only
   so many in total. Leave the headcounts alone. Rules of any other
   kind are listed as not checked.
7. Cost: hours = staffed x period hours; hours of uncovered places =
   uncovered x period hours, added up; wages = hours x rate; with
   on-cost = wages x (1 + percent). Round once, at the end. Show the
   cost of filling every need, once, for reference.
8. List every blank availability cell as unknown. Write numbered
   questions for each uncovered period, flag, pending dependence,
   unchecked rule and HR step. Ask about a blank cell only when its
   period is short in some option; other blank cells need no question.
   Recommend no option unless asked.
9. Use the output format exactly, section by section, printing "none" or
   "not supplied" for an empty section. End with the closing line.

Decline any request to name or rank people, to judge a legal limit, to
change a figure so an option looks better, or to send or publish.
```

## What to customize

- The periods, their lengths and the measures your demand is stated in.
- Your staffing ratios and minimums, role by role, and which roles need a separate qualified role.
- Your hourly rates, your on-cost percentage and whether it applies to every role.
- The rules you want checked and the ones you check by hand.
- When HR sees an option, and who else receives the approved roster.
- Whether a lending department's staff can be offered as a third option.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI from its own published map of the work. Not yet tested in a client environment.
