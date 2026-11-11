# Room turn priority list: tried once on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in [example.md](example.md): the five input blocks for the invented Wexcombe Lane Hotel (settings, departure list, arrival list, supervisor's notes and priority rules). No client data was used. The run followed the template's instruction block and output format. The model that ran it did not write the template, and it read the example's output only after producing its own.

## What came out

The full list, in the template's output format:

```
ROOM TURN PRIORITY LIST: Wexcombe Lane Hotel, Friday 4 December 2026, as of 10:30

For: housekeeping supervisor. Sources: departure list (9 rooms); arrival list (10 rooms); supervisor notes (7 notes); priority rules (4); settings. Defaults used: a note is old after 180 minutes.
Rooms: 11. On the worklist: 10. On maintenance hold: 1. Awaiting inspection: 1.
Inspection recorded in notes: 1. Flagged: 7. Decisions: 8.
Status is for the housekeeping supervisor to verify. This list does not say any room is clean or ready.

1. WORKLIST, IN PRIORITY ORDER
1. 110 Accessible Queen. Rule 1 (guest_flag is accessible-room-confirmed). Arrival 13:00, flag accessible-room-confirmed. State: Vacant, to be turned. List: departed 06:45. Note 07:15: "vacant dirty". FLAG, note is old: 3 hours 15 minutes old. See decision 1.
2. 102 King. Rule 2 (guest_flag is early-arrival-confirmed). Arrival 12:00, flag early-arrival-confirmed. State: Being turned. List: departed 09:15. Note 10:10: "cleaning in progress", "Bathroom".
3. 114 Queen. Rule 3 (arrival_time before 15:00). Arrival 10:45, flag none. State: Not yet departed. List: expected 11:00. No note. FLAG, arrival before departure: arrival 10:45, expected departure 11:00. See decision 2.
4. 120 Queen. Rule 3 (arrival_time before 15:00). Arrival 14:00, flag none. State: Status not supplied. No note. FLAG, status not supplied. See decision 3.
5. 101 King [AWAITING INSPECTION]. Rule 3 (arrival_time before 15:00). Arrival 14:30, flag none. State: Awaiting inspection. List: departed 08:40. Note 09:50: "cleaned awaiting inspection", "Attendant finished; waiting for the check".
6. 116 Suite. Rule 4 (guest_flag is group-block). Arrival 17:00, flag group-block. State: Not yet departed. List: expected 12:00. No note.
7. 104 Queen. No rule matched. Arrival 15:00, flag none. State: Conflicting status. List: expected 11:00. Note 10:20: "cleaning in progress", "Attendant started on the room". FLAG, conflicting status: list expects departure at 11:00; the 10:20 note says cleaning in progress. See decision 4.
8. 112 King. No rule matched. Arrival 15:30, flag none. State: Departure not known. List: blank status, no time. Note 09:40: "key returned to desk", "Key on the desk; no word on the room". FLAG, departure not confirmed, status wording not recognised: "key returned to desk". See decision 5.
9. 118 Queen. No rule matched. Arrival 16:30, flag none. State: Inspection recorded. Note 09:20: "inspected", "Inspected by the supervisor".
10. 105 King. No arrival today. State: Not yet departed. List: expected, no time. No note. FLAG, departure not confirmed: expected with no time. See decision 6.

2. ON MAINTENANCE HOLD
108 Suite. Note 10:05: "maintenance hold", "Shower valve leaking; maintenance called". List: departed 10:05. Arrival 16:00, flag group-block. FLAG, hold with an arrival. See decision 7.

3. LOAD CHECK
Minutes needed: 245 for 7 rooms (110 40, 102 30, 114 30, 116 55, 104 30, 112 30, 105 30). Minutes available: 240 (2 x 120). Difference: 5 short. Not counted: 120, status not supplied; 101, awaiting inspection; 118, inspection recorded; 108, on hold.

4. FOR THE FRONT DESK AND MAINTENANCE
Maintenance: 108, "Shower valve leaking; maintenance called".
Front desk, arrivals with a flag or a hold, by arrival time: 114, arrival 10:45, arrival before departure; 110, arrival 13:00, note is old; 120, arrival 14:00, status not supplied; 104, arrival 15:00, conflicting status; 112, arrival 15:30, departure not confirmed, status wording not recognised; 108, arrival 16:00, hold with an arrival.

5. DECISIONS FOR THE HOUSEKEEPING SUPERVISOR: 8
1. 110, note is old. The only note, "vacant dirty", is from 07:15. Is there a newer note, or what is the status now?
2. 114, arrival before departure. Arrival 10:45, expected departure 11:00. Is the arrival time, the departure time or the room wrong?
3. 120, status not supplied. Arrival 14:00, not on the departure list, no note. What is the status?
4. 104, conflicting status. The list expects departure at 11:00; the 10:20 note says cleaning in progress. Which record is current, and who confirms it?
5. 112, departure not confirmed, status wording not recognised. Blank departure status and time; the note says "key returned to desk". Has the guest left, and what time is now expected? Which of the five phrases applies?
6. 105, departure not confirmed. Expected with no time. Has the guest left, and what time is now expected?
7. 108, hold with an arrival. On hold per the 10:05 note; arrival at 16:00. Does the front desk know of the hold, and does the assignment stand?
8. Load check. 245 minutes needed, 240 available, 5 short. Which of the minutes, the rooms or the order will the supervisor change, if any?

6. NOTES FOR ROOMS ON NEITHER LIST
None.

Draft for the housekeeping supervisor. Nothing has been inspected, assigned, sent or changed. This list certifies nothing about the state of any room.
```

## What was observed

- Every required part was produced: the header and counts, the six numbered sections, the closing line. Nothing in the instructions made it stop; the inputs were complete and well formed.
- The result matches the published example's output in the order of all ten worklist rooms, the tier each room fell into, every state, every flag, the load figures (245 needed, 240 available, 5 short), the front desk list and the eight decisions. Rooms 101 and 118 were the only ones with the awaiting-inspection mark or an inspection recorded, as the checklist asks.
- The differences are in wording and layout only. The example's flag lines add a short explanation after each flag kind, and its decisions are longer; this run kept both shorter. The load check lists were given in worklist order, as in the example; this run left out the room types and wrote the states in lower case in the "not counted" list. No difference changed a fact, a room's place or a count.
- Every fact in both outputs is traceable to the inputs. Neither output adds a fact that is not in them. Both contain derived figures (ages, sums, counts), which were rechecked by hand.
- No guess was needed on the facts, but a few details of layout were left to the reader:
  - The output format shows how to write the guest flag when it is "none"; this run wrote "flag none", as the example does.
  - The format does not say how to order the rooms in the load check list or the "not counted" list.
  - The format does not say how long the explanation after a flag should be, so the length varies between runs.
  - The count line wraps differently in the format and in the example; this is cosmetic.
  - The header in the format has no instruction for the line "Defaults used" when no default applies; here a default did apply, so it was not tested.
- Edits made after this run, none re-run: the template now orders the load check lists (worklist order, holds last) and says what to write for "Defaults used" when none applies, which closes the two layout gaps above; a missing as-of time and missing load settings are covered in the instruction block; the output format now shows "No note.", "Not on the departure list." and "flag none"; the flag instruction says several flags on one room count once. The record above is the run as it happened.
- Only one input set was tried. The sixteen acceptance tests in the template were not run, and nothing was tested in a client environment.
