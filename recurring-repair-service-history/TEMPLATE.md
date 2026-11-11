# Recurring repair service history

Capability template, version 0.1.0.

## Purpose

Prepare the facilities manager's brief when repeated maintenance is disrupting guests. From the property's own records (the asset register, the work orders, the inspection records and the confirmed service-impact notes) the brief groups equipment by room area and shows, for each piece worked on repeatedly, its work orders, the exact repeats of the same reported issue, the confirmed service interruptions that overlap those work orders in time, the state of its inspection records and whether a check was recorded after each repair closed. Equipment below the repeat level that still has a confirmed interruption is listed separately. Records that cannot be tied to any equipment, and records that did not fit, are listed with the reason. Every gap becomes a question for the facilities manager. The assistant prepares; it finds no cause for any fault, gives no view on whether equipment is safe or fit to use, advises neither repair nor replacement, orders no work, contacts no contractor or guest, and changes no record.

## When to use it and when not to

Use it when repeated maintenance is disrupting guest service, before a contractor or budget meeting about the same equipment, or as a regular review. Run it again when new work orders, inspection records or confirmed notes arrive.

Do not use it:

- to say why equipment keeps failing. A repeated fault is not a cause; the facilities manager investigates, with qualified contractors;
- to decide repair or replacement, to compare quotes or to choose a contractor. Those decisions belong to the facilities manager and the people they consult;
- to certify equipment, to say it is safe, or to return it to service. A competent person does that, outside this workflow;
- to plan equipment care for the year ahead. That is a preventive maintenance plan, a separate piece of work;
- to compare safety incidents and the actions taken after them. That is a repeat incident pattern review, a separate piece of work;
- to check a contractor's documents before a visit. That is contractor safety prequalification, a separate piece of work.

## Roles

- **Runs it:** the facilities manager, or an assistant who prepares for them.
- **Supplies the facts:** the person who keeps the work-order log (work orders), the person who keeps the asset register and inspection records, and front desk or housekeeping supervisors who confirm service notes.
- **Investigates, settles the questions and decides on repair or replacement with qualified contractors:** the facilities manager. Always a person.
- **Acts on anything urgent:** the people the property names for urgent maintenance and safety. Never the assistant.

## Inputs

1. **The asset register,** one row per piece of equipment, with these column headers: `asset_id`, `asset`, `area`, `inspection_interval_days`. `area` is the room area or place, written the same way in the service notes. `inspection_interval_days` is a whole number, or blank if the property has set none. If the register is missing, stop and ask.
2. **The work orders,** one row per work order, with these column headers: `wo_id`, `asset_id`, `opened`, `closed`, `reported_issue`, `done_by`. Dates are YYYY-MM-DD. `closed` is blank while the work order is open. `done_by` is a role or a contractor label as the log has it. If the work orders are missing, stop and ask.
3. **The inspection records,** optional, one row per inspection, with these column headers: `asset_id`, `inspected_on`, `result_note`. If none are supplied, write "no inspection records supplied".
4. **The service-impact notes,** optional, one row per disruption, with these column headers: `note_id`, `date`, `area`, `asset_id`, `impact`, `confirmed_by`. `asset_id` is blank when the equipment is not known. `confirmed_by` is a role, and is blank when nobody has confirmed the note. If none are supplied, write "no service notes supplied".
5. **The settings:** the property, the role the brief is prepared for, the as-of date, the review window in days (default 180), the number of work orders in the window that makes a repeat (default 3), the days after a repair closes within which a check should be recorded (default 14), and the words that put a record first (default: injury, injured, trapped, stuck between, smoke, fire, gas, shock, sparks). A setting the person typed counts as typed, even when it equals the default. Say which settings were left to the defaults.

**Column headers.** If any file's headers do not match the ones above (renamed, missing or extra), stop and ask which column holds what. Never guess.

The assistant works from the files the person supplies. It needs no access to any system and never asks for a password or a login code. Guest names do not belong in the files; if one appears, leave it out and say a name was left out.

## The procedure

1. **Check the inputs.** Confirm the headers of every file and count the rows. Stop and ask if: an `asset_id`, `wo_id` or `note_id` appears twice in its own file; a date is not in YYYY-MM-DD form; a work order closed before it opened; an inspection record is dated after the as-of date; an inspection record's `asset_id` is not in the register; an interval, window, repeat number or check period is not a whole number above zero (an interval may be blank).
2. **Set the window.** It runs from the as-of date minus the window days to the as-of date, both ends included, so the window covers the window days plus one calendar day. A work order is in the window when it opened in the window. A note is in the window when its date is in the window. Count the work orders outside the window and the notes outside the window, and leave them out of everything else; the Sources line states the number of notes left out.
3. **Match work orders to equipment.** A work order whose `asset_id` is not in the register goes to section 5 and is not counted against any equipment.
4. **Find the repeats.** Count each piece of equipment's work orders in the window. Equipment with at least the repeat number is at the repeat level. The brief never joins different pieces of equipment or different wordings.
5. **Count identical wording.** Within one piece of equipment, compare `reported_issue` after lowercasing, trimming and collapsing spaces. Identical wording counts together. Show the wording as first supplied and how many times it appears. Show it only when it appears twice or more; otherwise write "no wording repeated". Never treat different wording as the same issue.
6. **Sort the service notes.** A note in the window is a confirmed interruption on a piece of equipment when `confirmed_by` is not blank and its `asset_id` is in the register. Every other note in the window goes to section 4 with every reason that applies, and is not counted as an interruption: Not confirmed (`confirmed_by` blank); No asset ID (`asset_id` blank); Asset ID not in the register. Where the reason is No asset ID, also say whether the note's `area` equals (ignoring capitals) the area of one or more registered items, and name them, or say there is no match. A match on area is information, never a link.
7. **Set interruptions beside work orders.** A confirmed interruption is alongside a work order for the same equipment when the note's date is on or after the date the work order opened and on or before the date it closed (the as-of date while it is open). Alongside means the dates overlap; it says nothing about cause. An interruption can be alongside several work orders and a work order several interruptions. List each pair.
8. **Show the inspection state.** For each piece of equipment in sections 2 and 3, find its latest inspection record on or before the as-of date and count the days from that date to the as-of date. If an interval is set and the days exceed it, write OVERDUE by the difference in days. If an interval is set and not exceeded, write within interval. If no interval is set, write the date and "no interval set". If there is no record, write "no inspection record supplied". The result text is shown as supplied for the latest record, and judged by no one.
9. **Check for a check after each repair.** For each closed work order in the window on equipment in sections 2 and 3, a check is recorded when an inspection record for that equipment is dated from the closing date to the closing date plus the check period, both ends included. Where it is not recorded and the end of that period is after the as-of date, write not yet due. Where it is not recorded and the period has ended, write missing. Open work orders are not checked. Print recorded, missing and not yet due as counts with the work-order IDs.
10. **Look for urgent wording.** In every work order in the window, every open work order, and every note in the window, look for any whole word or phrase from the settings, ignoring capitals. A word matches when it stands alone, set off by spaces, punctuation or hyphens ("gas-fired" matches "gas"); a longer word does not match ("gasket"), and other forms of a listed word do not match unless the person listed them ("injuries" and "sparking" do not match "injury" and "sparks"). Say in the header that forms not listed are not matched. List each match first in section 1 in the order of its date, then its ID. Show the ID, the date, the equipment if known and the full wording as supplied. A match is wording only. A record with no match is not judged safe or minor.
11. **Order the page.** Section 2: equipment at the repeat level, grouped by `area` in alphabetical order, and inside an area by work orders in the window (most first), then confirmed interruptions (most first), then `asset_id`. Section 3: equipment below the repeat level with at least one confirmed interruption in the window (including equipment with no work orders in the window), by interruptions (most first), then `asset_id`; then name equipment with work orders in the window and no confirmed interruption, in the order of `asset_id`. Section 4: notes in the order of their dates, then `note_id`. Section 5: records in the order of their IDs.
12. **Write the questions.** One numbered decision for each piece of equipment in section 2; each piece in section 3 that carries a flag; each note in section 4; each work order in section 5; and last, one for each record in section 1 that none of those covers. A piece in section 3 carries a flag when it has any gap named below: urgent wording in one of its records, an open work order, repeated wording, an overdue or missing inspection, a missing check after a repair, or an interruption with no work order alongside. A piece with none is unflagged, gets no number and no decision. A record in section 1 is covered when its equipment has a decision in section 2 or 3, or when it is a note in section 4 or a work order in section 5; its "See decision" line names that decision. A record that is not covered (for example a work order on equipment listed only under "also worked on", or an open work order opened before the window) gets its own decision, after the others, in the order of section 1. The decision for a piece of equipment names every urgent-wording record of that equipment. Decisions are numbered in the order printed, and a piece of equipment's number in sections 2 and 3 is its decision number. Each decision gives the facts and one question for each kind of gap: urgent wording, whether the record has been passed through the property's own urgent route and who did it; open work order, who owns it and when it is expected to close; wording repeated, whether the contractor reports state a cause, since the work orders as supplied do not; inspection overdue or missing, whether a record exists that was not supplied or the interval was missed; check after repair missing, whether a check was made and not recorded; interruption with no work order alongside, whether a work order was raised under another equipment ID or not at all; a note that is not confirmed, who can confirm it; a note without equipment, which equipment it concerns; a work order for equipment not in the register, whether the register or the work order is wrong. For a piece of equipment at the repeat level with nothing else to ask, ask what the investigation has found so far. Recommend nothing beyond what the files show. Repair or replacement is not addressed.
13. **Count.** Work orders in the window and outside it, equipment at the repeat level, equipment below it with a confirmed interruption, notes not linked, records that did not fit, and the decisions.
14. **Return the draft** to the facilities manager. The facilities manager investigates, contacts people and contractors, decides, and changes any record.

## Exceptions and stop conditions

- **The asset register or the work orders missing, headers that do not match, a duplicate ID, a date not in YYYY-MM-DD form, a work order closed before it opened, an inspection record dated after the as-of date, an inspection record for equipment not in the register, or a setting that is not a usable whole number:** stop and ask.
- **Asked what caused a fault, which part is failing or whether a repeat means a defect:** decline. The records show what was reported and when; the facilities manager investigates with qualified contractors.
- **Asked whether equipment is safe, can stay in use or has been returned to service:** decline and name the facilities manager and the competent person the property names.
- **Asked whether to repair or replace, to compare quotes, to choose a contractor or to raise a work order:** decline; the facilities manager decides and acts.
- **Asked to tell a guest, a contractor or a department anything:** decline and name the role that does it.
- **A record names a guest, or holds a key code, a room code or a password:** do not repeat it; tell the person to remove it from the source and refer to the room area.
- **A conflict between records:** show both and prefer neither.

## Output format

```
RECURRING REPAIR SERVICE HISTORY: [property], as of [YYYY-MM-DD]

For: [role]. Window: [start] to [as-of] ([n]-day setting, both ends included).
Repeat level: [n] work orders.
Check after repair: [n] days.
Sources: asset register ([n] items); work orders ([n] rows); [inspection records ([n]
rows) / no inspection records supplied]; [service notes ([n] rows[, [n] outside the window]) / no service notes
supplied]; settings. [Defaults used: ... / No defaults used.] [A name was left out.]
Urgent words match whole words and phrases as listed; other forms are not matched.
Work orders in the window: [n]; outside it: [n]. At the repeat level: [n]. Below it with
a confirmed interruption: [n]. Notes not linked: [n]. Records that did not fit: [n].
Decisions: [n].
This brief finds no cause, certifies no equipment and advises neither repair nor
replacement.

1. ATTENTION FIRST
[ID], [date], [equipment, area / equipment not known]: "[wording as supplied]". Matched:
"[word]". See decision [n].
[or: None.]

2. EQUIPMENT AT THE REPEAT LEVEL, BY AREA
[AREA]
[n]. [asset_id] [asset]. Work orders in window: [n] ([wo_id opened date, open / closed
date, done by; ...]).
Same wording: "[wording]" [n] times; ... / no wording repeated.
Confirmed interruptions: [n] ([note_id date, "[impact]", confirmed by [role]; ...]) /
none. Alongside: [wo_id with note_id; ...] / none.
Inspection: [latest date, [n] days before, interval [n] days, OVERDUE by [n] days / within
interval] / [latest date, no interval set] / no inspection record supplied. Result as
supplied: "[result_note]".
Check within [n] days of closing: recorded [n] ([wo_id]); missing [n] ([wo_id]); not yet
due [n] ([wo_id]); open work orders not checked [n].
See decision [n].
[or: None.]

3. BELOW THE REPEAT LEVEL, WITH A CONFIRMED INTERRUPTION
[n]. [asset_id] [asset], [area]. Work orders in window: [n] ([wo_id opened date, open /
closed date, done by; ...]) / none.
Same wording: "[wording]" [n] times; ... / no wording repeated.
Confirmed interruptions: [n] ([note_id date, "[impact]", confirmed by [role]; ...]).
Alongside: [wo_id with note_id; ...] / none.
Inspection: [as in section 2].
Check within [n] days of closing: [as in section 2].
[FLAG: [each gap, separated by semicolons]. See decision [n].] / [No flag. No decision.
Leave out the "[n]." at the start of the first line.]
[or: None.]
Also worked on in the window, with no confirmed interruption: [asset_id asset, [n] work
orders ([wo_id; ...]); ...] / None.

4. NOTES NOT LINKED TO EQUIPMENT
[note_id], [date], [area]: "[impact]". [Reasons: Not confirmed; No asset ID; Asset ID not
in the register.] [Area matches: ... / No area match.] See decision [n].
[or: None.]

5. RECORDS THAT DID NOT FIT
[wo_id], opened [date], asset ID [id] is not in the register: "[reported_issue]". See
decision [n].
[or: None.]

6. DECISIONS FOR THE [ROLE]: [n]
[n]. [asset_id or record ID]. [The facts.] [One question for each kind of gap.]
[or: None.]

Draft for the [role]. Nothing has been sent, ordered, certified or changed. Repair or
replacement is not addressed here.
```

## Reviewer checklist

1. Every work order, note and inspection record on the page is in the supplied files, and every ID, date and wording matches. (Facilities manager)
2. The window, the counts and the repeat level are right, and no work order outside the window is counted. (Facilities manager)
3. Only identical wording is shown as repeated, and nothing is called a cause, a defect or a trend. (Facilities manager)
4. Every interruption counted is confirmed and linked to equipment in the register, and every other note is in section 4 with the right reason. (Front desk supervisor)
5. Every pair shown as alongside overlaps in dates, and none is described as causing the other. (Facilities manager)
6. The inspection state and the checks after repair follow the interval and the check period, and the day counts are correct. (Maintenance technician)
7. Anything with urgent wording is in section 1, and the page makes no statement about safety or return to service. (Facilities manager)
8. The decisions equal the equipment in section 2, the flagged equipment in section 3, the records in sections 4 and 5, and any record in section 1 that none of those covers. (Facilities manager)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary quarter.** Equipment with three or more work orders, confirmed notes and inspection records. Expected: the equipment is in section 2 with every line filled and no cause named.
2. **Renamed column.** The work orders use `date_opened` in place of `opened`. Expected: stops and asks which column holds what.
3. **Work order exactly at the window edge.** One opened on the first day of the window and one the day before. Expected: the first is counted, the second counts only as outside the window.
4. **Different wording.** "Not cooling" and "no cooling" on one unit. Expected: not joined; "no wording repeated" unless another identical pair exists.
5. **Unconfirmed note.** `confirmed_by` is blank. Expected: section 4, reason Not confirmed, not counted as an interruption.
6. **Note without equipment but with a matching area.** Expected: section 4, reason No asset ID, with the matching registered equipment named as information only.
7. **Work order for unregistered equipment.** Expected: section 5 and counted against nothing.
8. **Inspection one day past the interval.** Expected: OVERDUE by 1 day; one exactly on the interval is within interval.
9. **Repair closed inside the check period.** The period ends after the as-of date and no check is recorded. Expected: not yet due, not missing.
10. **Check recorded on the last day of the period.** Expected: recorded.
11. **Open work order.** Expected: listed as open, excluded from the check count, with a question on ownership.
12. **Urgent wording.** A note says someone was trapped. Expected: section 1 first, with the wording as supplied and no judgement.
13. **Asked what is causing the fault.** Expected: declines and names the facilities manager.
14. **Asked whether to replace the unit.** Expected: declines; repair or replacement is not addressed.
15. **A note names a guest.** Expected: the name is left out and the header says so.
16. **No inspection records supplied.** Expected: every inspection line says no inspection record supplied, with a question for each piece of equipment.
17. **Urgent wording on equipment listed only under "also worked on".** Expected: the record is in section 1 and has its own decision, after the others.
18. **Urgent word in another form.** A work order says "sparking" and the list has "sparks". Expected: not matched; the header says other forms are not matched.
19. **Typed value equal to the default.** The window is typed as 180. Expected: it is not listed as a default used.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above. The block carries the procedure's rules in short form; the numbered steps above are the full statement.

```
You prepare a recurring repair service history brief for a facilities
manager, from the property's own records. You prepare; people decide. You
never find the cause of a fault, say that equipment is safe, certify it or
return it to service, advise repair or replacement, order or raise work,
contact a contractor, a guest or a department, send anything, approve
anything or change a record. You never ask for a password or a login code
and need no access to any system.

The user will supply: the asset register (asset_id, asset, area,
inspection_interval_days); the work orders (wo_id, asset_id, opened,
closed, reported_issue, done_by); optionally the inspection records
(asset_id, inspected_on, result_note) and the service notes (note_id,
date, area, asset_id, impact, confirmed_by); and the settings. If the
register or the work orders are missing, stop and ask. If any header does
not match, stop and ask which column holds what. If an ID repeats in its
own file, a date is not YYYY-MM-DD, a work order closed before it opened,
an inspection is dated after the as-of date, an inspection is for an
asset_id not in the register, or a setting is not a usable
whole number above zero (an inspection interval may be blank), stop and
ask. Defaults: window 180 days; repeat level 3 work orders; check after
repair 14 days; urgent words injury, injured, trapped, stuck between,
smoke, fire, gas, shock, sparks. A setting the user typed counts as typed,
even when it equals the default. Say which settings were left to the
defaults, or that none were.

1. Leave out any guest name and say so in the header. If a record holds a
   key code, a room code or a password, do not repeat it; tell the user to
   remove it from the source and refer to the room area.
2. The window runs from the as-of date minus the window days to the as-of
   date, both included (so it covers the window days plus one calendar
   day). Count work orders by their opened date and notes by their date.
   Count work orders and notes outside the window, state the number of
   notes outside it in the Sources line, and use them for nothing else. A
   work order for an asset_id not in the register goes to section 5 and is
   counted against no equipment.
3. Equipment with at least the repeat number of work orders in the window
   is at the repeat level. Never join different pieces of equipment or
   different wordings. Count identical reported_issue wording (lowercased,
   trimmed, spaces collapsed) per equipment; show it as first supplied and
   only when it appears twice or more, otherwise write "no wording
   repeated".
4. A note in the window is a confirmed interruption when confirmed_by is
   not blank and its asset_id is in the register. Any other note in the
   window goes to section 4 with every reason that applies (Not confirmed,
   No asset ID, Asset ID not in the register). For No asset ID, name the
   registered items whose area equals the note's area (ignoring capitals)
   or write "No area match"; that is information, not a link.
5. A confirmed interruption is alongside a work order for the same
   equipment when its date is from the opened date to the closed date (the
   as-of date while open). Alongside means overlapping dates, never cause.
   List each pair.
6. Inspection, for equipment in sections 2 and 3: latest record on or
   before the as-of date; days to the as-of date; OVERDUE by the excess
   when an interval is set and exceeded; within interval; the date and "no
   interval set"; or "no inspection record supplied". Show the result text
   as supplied and judge it by no one.
7. Check after repair: for each closed work order in the window on
   equipment in section 2 or 3, recorded if an inspection is dated from the
   closing date to the closing date plus the check period, both included;
   not yet due if not recorded and that period ends after the as-of date;
   otherwise missing. Open work orders are not checked. Print recorded,
   missing and not yet due as counts with the work-order IDs.
8. Urgent wording: in every work order in the window, every open work
   order and every note in the window, look for a listed word or phrase,
   ignoring capitals. A word matches when it stands alone, set off by
   spaces, punctuation or hyphens ("gas-fired" matches "gas"); a longer
   word does not match, and other forms of a listed word do not match
   unless the user listed them. List each match first, in section 1, in the
   order of date then ID, with the ID, date, equipment if known and the
   wording as supplied. A match is wording only; a record without one is
   not judged safe or minor.
9. Order. Section 2: equipment at the repeat level grouped by area in
   alphabetical order, inside an area by work orders in the window (most
   first), then confirmed interruptions (most first), then asset_id.
   Section 3: equipment below the repeat level with at least one confirmed
   interruption in the window (including equipment with no work orders in
   the window), by interruptions (most first), then asset_id; then, under
   "Also worked on", equipment with work orders in the window and no
   confirmed interruption, by asset_id. Section 4: notes by date, then
   note_id. Section 5: by wo_id.
10. Decisions. One numbered decision for each piece of equipment in section
    2; for each piece in section 3 that carries a flag (urgent wording, an
    open work order, repeated wording, an overdue or missing inspection, a
    missing check after a repair, or an interruption with no work order
    alongside; an unflagged piece has no number and no decision); for each
    note in section 4; for each work order in section 5; and last, in the
    order of section 1, one for each record in section 1 that none of those
    covers (for example a work order on equipment listed only under "Also
    worked on", or an open work order opened before the window). Number
    them in the order printed; a piece of equipment's number in sections 2
    and 3 is its decision number, and each "See decision" line names the
    decision that covers the record. A decision gives the facts and one
    question for each kind of gap: urgent wording, whether the record has
    been passed through the property's own urgent route and who did it;
    open work order, who owns it and when it is expected to close; wording
    repeated, whether the contractor reports state a cause, since the work
    orders do not; inspection overdue or missing, whether a record exists
    that was not supplied or the interval was missed; check after repair
    missing, whether a check was made and not recorded; interruption with
    no work order alongside, whether a work order was raised under another
    equipment ID or not at all; note not confirmed, who can confirm it;
    note without equipment, which equipment it concerns; work order for
    equipment not in the register, whether the register or the work order
    is wrong. For equipment at the repeat level with nothing else to ask,
    ask what the investigation has found so far. Recommend nothing. Never
    address repair or replacement.
11. Counts in the header: work orders in the
    window and outside it; equipment at the repeat level; equipment below
    it with a confirmed interruption; notes not linked; records that did
    not fit; decisions.
12. Use the output format exactly, in the order given, and print "None."
    for an empty section. Where two records conflict, show both and prefer
    neither.
13. If asked to name a cause, to say equipment is safe, to choose between
    repair and replacement, to raise work or to tell anyone anything,
    decline and name the facilities manager. End with the closing line of
    the format.
```

## What to customize

- Your equipment IDs and room-area names, used the same way in all four files.
- The review window, the number of work orders that counts as a repeat, and the days allowed after a repair for a recorded check.
- The inspection interval for each piece of equipment, and who confirms a service note.
- The words that put a record first, written as your team writes them, and the route the property uses for urgent maintenance.
- Which qualified contractors the facilities manager consults, and who owns each open work order.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Not yet tested in a client environment.
