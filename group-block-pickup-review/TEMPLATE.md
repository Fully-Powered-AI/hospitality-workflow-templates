# Group room block pickup review

Workflow template, version 0.1.0.

## Purpose

Prepare the pickup brief for one group room block as it nears its review or release date. From the block export, the booking rows, the approved summary of the group agreement and the room inventory, the brief shows how many room nights are blocked, how many are confirmed and how many are unfilled, night by night and room type by room type, with tentative bookings kept on their own line. It shows where the counts disagree and leaves those unresolved, and it ends with numbered questions for the account owner and the two decisions that belong to the revenue manager and group-sales owner. The assistant prepares; it releases no rooms, contacts no one, changes no booking and decides nothing.

## When to use it and when not to

Use it for one block at a time, in the days before the block's review date or release date, once the booking report has been refreshed. Run it again if bookings change before the meeting.

Do not use it:

- to read, interpret or apply the group agreement. The brief uses only the dates, the stated minimum and the terms status written in the approved summary that a person supplies. It does not work out charges, penalties or rights, and it gives no legal view;
- to release rooms, change a block or write to the group. A person does those;
- to judge demand across the property or plan supply across months. That is demand and supply review;
- to assess the account's likelihood of renewing. That is renewal risk review.

## Roles

- **Runs it:** the revenue manager or the group-sales owner.
- **Supplies the approved agreement summary and answers for the terms:** the group-sales owner.
- **Answers the questions about the group's plans:** the account owner, the person who holds the relationship with the group.
- **Decides any release of rooms and any revised offer:** the revenue manager and the group-sales owner, together.
- **Settles counts that do not reconcile:** whoever keeps the booking records, as the group-sales owner directs. For a reported-pickup difference the account owner is asked which figure is right and passes it to them. An inventory shortfall (blocked rooms above rooms in inventory) goes to the revenue manager or whoever keeps the inventory, because the account owner cannot know it.

Use the titles your property uses.

## Inputs

The assistant works from files and notes the person supplies. It needs no connection to any system and never asks for a password or a login code. Exports are read with these default column headers. If a header differs from the one expected, stop, list the headers found beside the headers expected, and ask which column is which. Never guess a column.

1. **Block export.** `block_ref,group,stay_date,room_type,blocked_rooms,reported_pickup`. One row per night and room type. Dates are written YYYY-MM-DD. `reported_pickup` is the pickup figure the system shows; a blank cell means it was not supplied. If missing, stop.
2. **Booking pickup.** `block_ref,reservation_id,stay_date,room_type,rooms,status`. One row per reservation, night and room type. The status must be confirmed, tentative or cancelled (any capitals). If missing, stop.
3. **Approved agreement summary.** `block_ref,review_date,release_date,minimum_pickup_percent,terms_status,summary_note`. The summary is written and approved by a person. The assistant reads these fields and nothing else about the agreement. If missing, print "agreement summary not supplied" and continue without dates or a minimum.
4. **Room inventory.** `stay_date,room_type,rooms_in_inventory`. If missing, write "room inventory not supplied" and continue.
5. **Settings.** The block to review (`block_ref`), the run date, the property, and the titles of the revenue manager, the group-sales owner and the account owner. If the block or the run date is missing, stop and ask.

## The procedure

1. **Check the files.** Confirm the headers. Stop if a room figure is not a whole number of zero or more, if a date is not a real date written YYYY-MM-DD, if a status is not confirmed, tentative or cancelled, if the block export repeats a `block_ref`, `stay_date` and `room_type`, or if the booking rows repeat a `reservation_id`, `stay_date` and `room_type` within the block.
2. **Choose the block.** Keep the rows whose `block_ref` is the block to review. Count and report the rows of other blocks that were ignored, in each file. If the block is not in the block export, stop.
3. **Match rooms.** Match room types ignoring case and spaces. A booking row of this block whose night and room type are not a row of the block is outside the block: list it, whatever its status except cancelled, and count it nowhere.
4. **Count each night and room type.** For each block row: confirmed = rooms in confirmed bookings; tentative = rooms in tentative bookings; cancelled rooms are counted only for the closing figure of cancelled room nights. Confirmed in block = the smaller of confirmed and blocked. Above the block = confirmed minus blocked, if above 0. Unfilled = blocked minus confirmed, if above 0. Only confirmed bookings are pickup; tentative rooms never are.
5. **Total.** Add each night, then the whole block. Pickup percent = confirmed in block divided by blocked, times 100, rounded to one decimal place with a half rounded up. Work the percent for each night the same way.
6. **Compare the reported pickup.** Where `reported_pickup` is supplied and differs from the confirmed count of the booking rows, mark the row unreconciled and show both figures. Totals use the booking rows. The unfilled figure of an unreconciled row is shown but is not settled. A row above the block (confirmed rooms exceed blocked rooms) is also listed under "Counts that do not reconcile" and is unresolved, but it takes no "Unreconciled." marker on its room-type line, because its unfilled figure is 0 and not in doubt; it is asked under (b), not (a).
7. **Compare with the inventory.** Where inventory is supplied, a row whose blocked rooms exceed the rooms in inventory is unreconciled. List it under "Counts that do not reconcile" with both figures and refer it to the revenue manager or whoever keeps the inventory; the account owner is not asked about it. For each night, unfilled as a share of inventory = the night's unfilled divided by the sum of `rooms_in_inventory` for that night across the room types supplied, rounded to one decimal place with a half rounded up. If a night has a block row with no inventory row, write "inventory not supplied for [room type]" instead of the share.
8. **Read the approved summary.** Work out the days from the run date to the review date and to the release date. A blank date is written "not supplied". If a date has passed, say by how many days in the "For:" line and print the line "The brief cannot show whether rooms were released." directly below it. If `terms_status` is exactly "approved" (any capitals) and `minimum_pickup_percent` is supplied, compare pickup with it: the difference is the rounded pickup percent minus the stated minimum, in points, one decimal place. The stated minimum is applied to the whole block, as supplied. If it is blank, write "Not compared: stated minimum not supplied". Any other `terms_status`, including "disputed", is unresolved: give the room counts, write "Not compared: terms status is [status]", and frame no decision.
9. **Show the tentative effect.** For each block row, the tentative rooms that could fill an unfilled room are the smaller of tentative and unfilled. Unfilled if every tentative room were confirmed = unfilled minus the sum of those. This is shown for information; the main figures never include it.
10. **Write the questions for the account owner,** numbered in one run, in this order, each with its facts. Skip a rule that has nothing to ask. (a) Each row where the reported pickup differs from the booking rows: which figure is right; the account owner passes this to whoever keeps the booking records. An inventory shortfall is not asked here; it is referred to the revenue manager or whoever keeps the inventory. (b) Each row above the block: whether the extra room was agreed as an addition. (c) The outside-the-block reservations, as one question: whether they belong to the group. (d) Each night that has tentative rooms and unfilled rooms: whether the group expects the tentative rooms to confirm before the release date. (e) The night with the lowest pickup percent, if the block has more than one night and that night has unfilled rooms; name every night tied: whether the group has said it expects more rooms. (f) If the terms status is approved, a stated minimum is supplied and pickup is below it: whether the group expects to close the gap before the release date. Ask about the group's plans; never about what the agreement means. Question (d) is one per night, naming each room type that has tentative rooms with that room type's own tentative and unfilled figures, and marking an unfilled figure that is not settled.
11. **Frame the two decisions.** Decision 1 is whether to release any unfilled rooms and which; decision 2 is whether to put a revised offer to the group. Give the facts for each (unfilled and tentative room nights, the days to the release date, the pickup against the stated minimum, the lowest night). Where a fact is blank, write it as in the format: "release date not supplied", "stated minimum not supplied", or, for a block of one night, "one night only, no lowest night". Mention any unreconciled row whose unfilled figure is not settled. Recommend nothing unless the revenue manager asks. If the terms are not approved, or no summary was supplied, replace both with one line: "Unresolved: the terms status is [status]. No decision is framed until the group-sales owner settles the approved summary."
12. **Tie out.** Blocked minus confirmed in block must equal unfilled. Confirmed in block rows must equal confirmed in block plus above the block. The nights must add to the block totals. If any fails, stop, report both figures and the difference, and write nothing else.
13. **Return the brief** to the revenue manager and group-sales owner only.

## Exceptions and stop conditions

- **A header does not match, a figure or date is invalid, a status is not one of the three, a row repeats or the block is not in the export:** stop and ask. Do not repair the file.
- **The tie-out fails:** stop; report the figures and the difference.
- **The reported pickup differs from the booking rows, a night has more confirmed rooms than blocked, or the block is larger than the inventory:** list it under "Counts that do not reconcile" as unresolved (an inventory shortfall or a reported-pickup difference also takes the "Unreconciled." marker; a row above the block does not, and is asked under (b)); a reported-pickup difference is asked under (a), an inventory shortfall is referred to the revenue manager or whoever keeps the inventory; release nothing and propose nothing for that row.
- **The terms status is not approved:** give the counts, do not compare them with the agreement and frame no decision.
- **No agreement summary:** print "agreement summary not supplied" and continue without dates or a minimum.
- **Asked to read the agreement itself, explain what a clause means, work out a penalty or charge, or say what the group owes:** decline. Name the group-sales owner and, where needed, the property's own advisers. The brief uses only the approved summary.
- **Asked to release rooms, change the block, contact the group, update a booking or send the brief:** decline. A person does that.
- **Asked to count a tentative booking as pickup, or to settle an unreconciled figure by choosing one:** decline. The account owner or the booking records settle it.
- **The files contain a password, a login code or payment details:** do not repeat them; tell the person to remove them from the source.

## Output format

```
GROUP BLOCK PICKUP BRIEF: [group], block [block_ref]

For: [revenue manager] and [group-sales owner], [property]. Prepared [run date]. Review date [date] ([n] days away / passed [n] days ago / not supplied). Release date [date] ([n] days away / passed [n] days ago / not supplied).
[If a date has passed: The brief cannot show whether rooms were released.]
Inputs: block export [file]; booking pickup [file]; agreement summary [file / agreement summary not supplied]; room inventory [file / room inventory not supplied]. Rows for other blocks ignored: [n] in the block export, [n] in the booking rows.
Terms status in the approved summary: [status / not supplied].

Pickup at a glance
Blocked room nights: [n].
Confirmed in the block: [n] ([pct]%).
Stated minimum in the approved summary: [pct]%. Pickup is [x] points below / above it / equal to it. / Not compared: [reason].
Unfilled room nights: [n]. [Row [date] [room type] is unreconciled, so its [n] are not settled.]
Tentative room nights, not counted: [n]. If every tentative room were confirmed, unfilled would be [n].
Cancelled room nights ignored: [n].

By night and room type
[date]: blocked [n], confirmed in block [n] ([pct]%), unfilled [n], tentative [n]. Unfilled is [pct]% of the [n] rooms in inventory. / inventory not supplied for [room type].
  [room type]: blocked [n], confirmed [n], reported by the export [n / not supplied], unfilled [n], tentative [n]. [One room above the block. / [n] rooms above the block.] [Unreconciled.]
[Print the night line and its room type lines for each night.]

Counts that do not reconcile
[date] [room type]: [what differs, with both figures]. [The brief uses [figure]. / Inventory shortfall: referred to the [revenue manager] or whoever keeps the inventory.] Unresolved. / None.

Outside the block
[reservation_id], [date], [room type], [n] rooms, [status]: [the night / the room type] is not in the block.
Neither is counted anywhere above. / None.

Questions for the account owner
[n]. [Date and room type or reservation.] [Facts.] [Question.]
/ None.

Decisions for the revenue manager and group-sales owner
1. Whether to release any unfilled rooms, and which. Facts: [unfilled] room nights unfilled, [tentative] tentative, release date [date] ([n] days away / passed [n] days ago / not supplied). [Unreconciled note.] This brief releases nothing.
2. Whether to put a revised offer to the group. Facts: pickup [pct]% against a stated minimum of [pct]% / stated minimum not supplied; lowest night [date] at [pct]% / one night only, no lowest night. This brief sends nothing.
/ Unresolved: the terms status is [status]. No decision is framed until the group-sales owner settles the approved summary.

Check lines
Blocked [n] - confirmed in block [n] = unfilled [n].
Confirmed in block rows [n] = confirmed in block [n] + above the block [n].
Nights: blocked [one n per night, joined by +] = [n]; confirmed in block [one n per night, joined by +] = [n]; unfilled [one n per night, joined by +] = [n].

Brief for the [revenue manager] and [group-sales owner]. Nothing has been released, sent or changed. They decide any release or revised offer.
```

If a section has nothing to show, print "None." under its heading. Where the stated minimum is not compared, print the reason on that line. In the "Inputs:" line use the file names as supplied, and use the titles as supplied. "Confirmed in block rows" is the total of confirmed rooms in the booking rows of the block's nights and room types. A cancelled booking outside the block is not listed and not counted.

## Reviewer checklist

1. Every file's headers matched, or the brief stopped. (Revenue manager)
2. Each night and room type can be reproduced by hand from the booking rows. (Revenue manager)
3. Only confirmed bookings are counted as pickup; tentative and cancelled rooms are not. (Revenue manager)
4. Every difference between the reported pickup and the booking rows is listed as unresolved, and nothing was settled by choosing a figure. (Group-sales owner)
5. The dates, the stated minimum and the terms status are those of the approved summary, and nothing is said about what the agreement means. (Group-sales owner)
6. Every reservation outside the block is listed and counted nowhere. (Revenue manager)
7. Each question asks about the group's plans or about a count, and none recommends a release or an offer. (Group-sales owner)
8. The check lines tie. (Revenue manager)

## Acceptance tests

Proposed tests. None has been run as written, though the run on the invented example covered several of them in passing (see the trial record).

1. **Ordinary block.** Every file complete, reported pickup equal to the booking rows, terms approved. Expected: all figures tie and no count is listed as unreconciled.
2. **Tentative rooms.** A tentative booking on a night with unfilled rooms. Expected: shown on its own line and in the "if every tentative room" figure, not counted as pickup, and a question for the account owner.
3. **Reported pickup differs.** The export shows 10 and the bookings 9. Expected: unreconciled, both figures shown, the brief uses 9, unfilled marked not settled, a question asked.
4. **Above the block.** 6 confirmed against 5 blocked. Expected: confirmed in block 5, one above the block, unfilled 0, a question asked.
5. **Outside the block.** A confirmed booking for a night that is not in the block. Expected: listed under "Outside the block" and counted nowhere.
6. **Cancelled booking.** Expected: counted only in the cancelled room nights figure.
7. **Disputed terms.** The summary's terms status is "disputed". Expected: counts given, "Not compared", no decisions framed.
8. **No summary supplied.** Expected: "agreement summary not supplied", no dates and no minimum, and the rest of the brief complete.
9. **Release date passed.** Expected: the number of days past is stated in the "For:" line, with the line "The brief cannot show whether rooms were released." directly below it.
10. **Header mismatch.** A booking file with `qty` in place of `rooms`. Expected: stops and lists the headers found and expected.
11. **Other blocks in the files.** Expected: their rows ignored and the number reported.
12. **Asked to read the agreement or release rooms.** Expected: declines and names the group-sales owner.
13. **Inventory shortfall.** Blocked rooms above the rooms in inventory. Expected: unreconciled, listed with both figures and referred to the revenue manager or whoever keeps the inventory, and not asked of the account owner.
14. **Blank minimum or one night.** An approved summary with a blank minimum, or a one-night block. Expected: "stated minimum not supplied" or "one night only, no lowest night" in the decisions, and no error.
15. **Tie-out fails.** One night's confirmed count altered by 1. Expected: stops and reports the difference.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare a pickup brief for one group room block, for a revenue
manager and a group-sales owner, from the files and notes the person
supplies. You prepare; people decide. You release no rooms, contact
no one, change no booking and send nothing. Anything that sends,
posts, pays or changes a record waits for a person's approval. You
never ask for a password or a login code. You do not read or
interpret the group agreement: you use only the dates, the stated
minimum and the terms status in the approved summary the person
supplies.

The user will supply: the block export, the booking rows, the approved
agreement summary, the room inventory, and settings (the block to
review, the run date, the property, the titles of the revenue manager,
the group-sales owner and the account owner). Expected files and
default headers:
- block export: block_ref,group,stay_date,room_type,blocked_rooms,
  reported_pickup (one row per night and room type; a blank
  reported_pickup means not supplied)
- booking rows: block_ref,reservation_id,stay_date,room_type,rooms,
  status (status is confirmed, tentative or cancelled, any capitals)
- approved agreement summary: block_ref,review_date,release_date,
  minimum_pickup_percent,terms_status,summary_note
- room inventory: stay_date,room_type,rooms_in_inventory
Dates are YYYY-MM-DD. If a header does not match, stop, list the
headers found beside the headers expected, and ask; never guess a
column. Stop also, and do not repair the file, if a room figure is not
a whole number of zero or more, a date is not a real date, a status is
not one of the three, the block export repeats a block_ref, stay_date
and room_type, the booking rows repeat a reservation_id, stay_date and
room_type within the block, or the block is not in the block export.
If the block or the run date is missing, stop and ask. If the block
export or booking rows are missing, stop. If the summary is missing,
print "agreement summary not supplied" and continue without dates or a
minimum. If the inventory is missing, print "room inventory not
supplied" and continue.

1. Keep only the rows of the block to review; report how many rows of
   other blocks you ignored, in each file. Match room types ignoring
   case and spaces. A booking of this block whose night and room type are
   not a row of the block is outside the block: list it, whatever its
   status except cancelled, and count it nowhere, not even in the
   cancelled figure.
2. For each night and room type: confirmed = rooms in confirmed
   bookings; tentative = rooms in tentative bookings; cancelled rooms
   count only toward "Cancelled room nights ignored", the total of
   cancelled rooms in the rows of the block. Confirmed in block = the
   smaller of confirmed and blocked. Unfilled = blocked minus
   confirmed, if above 0. Above the block = confirmed minus blocked, if
   above 0. Only confirmed bookings are pickup. Add each night, then
   the block.
3. Pickup percent = confirmed in block / blocked x 100, one decimal,
   half rounded up, for each night and the block. Where inventory is
   supplied, unfilled as a share of inventory for a night = the night's
   unfilled / the sum of rooms_in_inventory for that night across the
   room types supplied, one decimal, half rounded up; if a block row
   has no inventory row, write "inventory not supplied for [room type]".
4. Where reported_pickup is supplied and differs from the confirmed
   count of the booking rows, or a row's blocked rooms exceed its rooms
   in inventory, mark the row "Unreconciled." and list it under "Counts
   that do not reconcile" as unresolved, with both figures. Use the
   booking rows in the totals, mark the unfilled figure of that row as
   not settled, and never choose a figure for the person. A row above
   the block is also listed under "Counts that do not reconcile" and
   unresolved, but takes no "Unreconciled." marker (its unfilled is 0)
   and is asked under (b), not (a). An inventory shortfall is not asked
   of the account owner: refer it to the revenue manager or whoever
   keeps the inventory.
5. Work out the days from the run date to the review date and to the
   release date; a blank date is "not supplied". If a date has passed,
   say by how many days in the "For:" line and print the line "The
   brief cannot show whether rooms were released." directly below it.
   If terms_status is exactly "approved" (any capitals) and
   minimum_pickup_percent is supplied, give the difference in points,
   one decimal, between the rounded pickup percent and
   minimum_pickup_percent. If the minimum is blank, write "Not
   compared: stated minimum not supplied". Otherwise write "Not
   compared: terms status is [status]" and frame no decision.
6. Show unfilled if every tentative room were confirmed, for
   information only: for each row, the tentative rooms that could fill
   an unfilled room are the smaller of tentative and unfilled; unfilled
   if every tentative room were confirmed = unfilled minus the sum of
   those.
7. Write the numbered questions for the account owner, in one run, in
   this order, each with its facts, skipping a rule with nothing to
   ask: (a) each row where the reported pickup differs from the booking
   rows: which figure is right (the account owner passes it to whoever
   keeps the booking records); (b) each row
   above the block: whether the extra room was agreed as an addition;
   (c) the outside-the-block reservations, as one question: whether
   they belong to the group; (d) each night with tentative and unfilled
   rooms, one question per night naming each room type that has
   tentative rooms with that room type's own tentative and unfilled
   figures, marking an unfilled figure that is not settled: whether the
   group expects the tentative rooms to confirm before the release
   date; (e) the night with the lowest pickup percent, if the block has
   more than one night and that night has unfilled rooms, naming every
   night tied: whether the group has said it expects more rooms; (f) if
   the terms status is approved, a stated minimum is supplied and
   pickup is below it: whether the group expects to close the gap before the release date.
   Ask about the group's plans and about counts; never about what the
   agreement means.
8. Write the two decisions with their facts and recommend nothing
   unless asked. Where a fact is blank, write it as the format does:
   "release date not supplied", "stated minimum not supplied", or, for
   a one-night block, "one night only, no lowest night". If the terms are not approved or no summary was
   supplied, write instead the one "Unresolved" line of the format.
9. Tie out: blocked - confirmed in block = unfilled; confirmed in block
   rows (the total confirmed rooms in the booking rows of the block's
   nights and room types) = confirmed in block + above the block; the
   nights add to the totals. If anything fails, stop, report the
   figures and the difference, and write nothing else.
10. Use the output format exactly. In the "Inputs:" line use the file
    names as supplied; use the titles as supplied. Where a section has
   nothing to show, print "None." End with the closing line.

If asked to read the agreement, say what a clause means, work out a
charge, release rooms, change a booking, contact the group, count a
tentative booking as pickup, or send the brief, decline and name the
person who decides. Never adjust a figure to make it tie.
```

## What to customize

- Your revenue manager, group-sales owner and account owner titles.
- The column headers of your block export and booking report, so they match every time.
- Which statuses in your system mean confirmed, tentative and cancelled.
- How the approved agreement summary is written, who approves it and where its dates and stated minimum come from.
- How many days before the release date you run the review.
- Who receives the approved brief, and in what form.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Editorially reviewed. Tried on its invented example in Claude on 10 November 2026, then edited after an independent review and run again on the edited text; both runs had seen the example's output first, so neither is independent of the example, and only one input set has been tried. The record is published with the template. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
