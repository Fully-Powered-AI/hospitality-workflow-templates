# Room turn priority list

Capability template, version 0.1.0.

## Purpose

Prepare the housekeeping supervisor's worklist for the day from the property's own records: the departure list, the arrival list and the supervisor's room-status notes. Every room that has a departure or an arrival appears once, ordered by the property's own priority rules, with its recorded state, its arrival, and a mark when it is awaiting inspection. Rooms on a maintenance hold sit in their own section. Disagreements between the records, departures that are not confirmed, notes that have gone old and arrivals that do not fit the departure are written as questions for the supervisor. A load check sets the turn minutes still needed against the minutes the team has left. The assistant prepares; it never inspects a room, says a room is clean or ready, assigns anyone to a room, contacts the front desk, maintenance or a guest, or changes a record.

## When to use it and when not to

Use it when the day's departure and arrival lists are available, and again whenever a status moves: departures are confirmed, a hold is released, a room is inspected, or the supervisor has walked the floor and updated the notes.

Do not use it:

- to decide that a room is ready, clean or fit to sell. The supervisor, or whoever the property names, inspects and decides;
- to assign rooms to attendants or to set a shift plan. The supervisor assigns the work;
- to decide who is moved to another room or to change an arrival. That belongs to the front desk and the manager;
- to judge a repair, a leak, a lock or any safety condition. A note about one is shown as supplied and goes to maintenance through the people the property names;
- to plan equipment care through the year. That is a preventive maintenance plan, a separate piece of work;
- to prepare a rented unit between tenants. That is a unit turnover readiness checklist, a separate piece of work;
- to plan an emergency drill. That is an emergency drill brief, a separate piece of work.

## Roles

- **Runs it:** the housekeeping supervisor, or the assistant manager who plans the day for them.
- **Supplies the facts:** the front desk (departure and arrival lists), the supervisor (notes), and whoever keeps the property's priority rules.
- **Verifies each room's status, settles the questions and assigns the work:** the housekeeping supervisor. Always a person.
- **Reads the front desk and maintenance lists and acts on them:** the front desk and maintenance, through the people the property names. Never the assistant.

## Inputs

1. **The departure list,** one row per room, with these column headers: `room`, `room_type`, `departure_status`, `departure_time`. `departure_status` is departed, expected or blank. `departure_time` is HH:MM on a 24-hour clock: the time the guest left, or the time the guest is expected to leave. If the list is missing, stop and ask.
2. **The arrival list,** one row per arriving room, with these column headers: `room`, `room_type`, `arrival_time`, `guest_flag`. `arrival_time` is HH:MM, or blank. `guest_flag` is one of the property's own codes, or none or blank. The list holds no guest names; if one appears, apply the rule for guest names in the exceptions. If the list is missing, stop and ask.
3. **The supervisor's room-status notes,** optional, one row per note, with these column headers: `room`, `status`, `note`, `noted_at`. `status` is one of five phrases: vacant dirty, cleaning in progress, cleaned awaiting inspection, inspected, maintenance hold. `noted_at` is HH:MM on the day. If none are supplied, write "no supervisor notes supplied".
4. **The priority rules,** one row per rule, with these column headers: `rule_no`, `field`, `test`, `value`. `field` is arrival_time, guest_flag, room_type or status. `test` is `before` (for arrival_time only) or `is`. `value` is a time, a flag code, a room type or one of the five status phrases. The rules are applied in `rule_no` order. If the rules are missing, stop and ask; the assistant never invents a priority.
5. **The settings:** the property, the role the list is prepared for, the day, the time of the run (the as-of time), and, for the load check, the minutes a turn takes for each room type, the number of people turning rooms and the minutes each has left. A note is old when it is more than 180 minutes old, unless the settings give another number. Say when the default is used. If the load settings are missing, the load check is not done and the list says what is missing.

**Column headers.** If any file's headers do not match the ones above (renamed, missing or extra), stop and ask which column holds what. Never guess.

The assistant works from the files and notes the person supplies. It needs no access to any property system and never asks for a password or a login code.

## The procedure

1. **Check the inputs.** Confirm the headers of every file. Count the rows. If a room appears twice in the departure list, or twice in the arrival list, stop and ask. If a room's type differs between the two lists, stop and ask. If a time is not in HH:MM form, or the as-of time is missing, stop and ask. If a rule does not fit the form above (for example, "guests we know well"), stop and ask how to write it as a test on the fields; apply no rule that was not supplied.
2. **Gather the rooms.** Every room in the departure list or the arrival list is a room on the list. A room that appears in the notes only is not added; it goes to the last section (step 11).
3. **Choose the note.** When a room has more than one note, the one with the latest `noted_at` is the note for that room and the others are not used. If two share the latest time, stop and ask.
4. **Set the recorded state of each room.** A state names what the records say, never that a room is ready. A note whose `status` is not one of the five phrases is not used for the state; it is shown as supplied. The states, in this order of precedence:
   - **Maintenance hold:** the note says maintenance hold, whatever the departure list says.
   - **Conflicting status:** the departure list says expected and the note says vacant dirty, cleaning in progress, cleaned awaiting inspection or inspected. Both records are shown and neither is preferred.
   - **Awaiting inspection:** the note says cleaned awaiting inspection.
   - **Inspection recorded:** the note says inspected. The state means that the supervisor's note says so; the assistant does not confirm it.
   - **Being turned:** the note says cleaning in progress.
   - **Vacant, to be turned:** the note says vacant dirty, or the list says departed and no note says otherwise.
   - **Not yet departed:** the list says expected and there is no note.
   - **Departure not known:** the room is on the departure list with a blank `departure_status` and no usable note.
   - **Status not supplied:** the room is on the arrival list only, with no usable note.
5. **Order the worklist.** Rooms on a maintenance hold are left out of the ordering. For every other room, apply the rules in `rule_no` order; the first rule the room meets sets its tier. `arrival_time before` is met only when the room has an arrival time strictly earlier than the value; a blank arrival time meets no rule of that kind. `guest_flag is`, `room_type is` and `status is` are met when the field equals the value (for `status`, the note's status phrase). The tiers run: Rule 1, Rule 2 and so on in order; then "No rule matched" for rooms with an arrival that met no rule; then "No arrival today" for rooms with no row in the arrival list. Inside a tier, order by arrival time, earliest first, rooms with a blank time last, then by room number, lowest first.
6. **Mark and flag.** A room whose state is Awaiting inspection carries the mark [AWAITING INSPECTION] after its room number. Put each flag on the room's line and leave the line where it stands. A room with several flags carries them in one flag, kinds separated by commas, and counts once. The kinds:
   - **Conflicting status:** state as above. Give both records with their times.
   - **Departure not confirmed:** the list shows a blank `departure_status`; or expected with a blank `departure_time`; or expected with a `departure_time` earlier than the as-of time.
   - **Arrival before departure:** the arrival time is earlier than the departure time on the same room, whether the departure is recorded or expected.
   - **Arrival time not supplied:** a room on the arrival list with a blank `arrival_time`.
   - **Note is old:** the note used is more than the allowed minutes older than the as-of time. State its age in hours and minutes.
   - **Status wording not recognised:** the note's status is not one of the five phrases. Quote it.
   - **Status not supplied:** the state is Status not supplied.
   - **Hold with an arrival:** a room on maintenance hold that has a row in the arrival list.
7. **Load check.** Count a room's turn minutes, by room type from the settings, for each room whose state is Vacant to be turned, Being turned, Not yet departed, Departure not known or Conflicting status. A room being turned counts in full, because the assistant does not know how much is done. Rooms that are Awaiting inspection, Inspection recorded, on hold or Status not supplied are not counted and are named. Minutes needed = the sum. Minutes available = people turning rooms × minutes each has left. Print both and the difference. List the counted rooms and the rooms not counted in worklist order, rooms on hold last. If a room's type has no minutes in the settings, stop the load check and name the type. Recommend nothing about the difference.
8. **Lists for the front desk and maintenance.** For maintenance: every room on hold, with its note as supplied. For the front desk: every room with a row in the arrival list that carries a flag or is on hold, in arrival-time order (blank last), with its arrival time and its flag kinds.
9. **Write the questions.** One numbered decision per flagged room, in the order the lines are printed (the worklist first, then holds), then one for the load check if the minutes needed exceed the minutes available. Each gives the facts in one sentence and one question per kind of flag, addressed to the supervisor. Questions by kind: conflicting status, which record is current and who confirms it; departure not confirmed, whether the guest has left and, if not, the time now expected; arrival before departure, whether the arrival time, the departure time or the room is wrong; arrival time not supplied, the expected time; note is old, whether there is a newer note or what the status is now; status wording not recognised, which of the five phrases it means; status not supplied, what the status is; hold with an arrival, whether the front desk knows of the hold and whether the assignment stands; load check, which of the minutes, the rooms or the order the supervisor will change, if any. Recommend nothing beyond what the files show.
10. **Count.** Rooms on the list, on the worklist, on hold, awaiting inspection, with an inspection recorded, flagged, and the decisions. Decisions equal the flagged rooms plus one if the minutes needed exceed the minutes available.
11. **Notes for rooms on neither list.** Each such note, as supplied, with the question of whether the room belongs on the list. If none, write "None."
12. **Return the draft** to the supervisor. The supervisor verifies each status, settles the questions and assigns the work. People contact the front desk and maintenance and change the records.

## Exceptions and stop conditions

- **A list or the rules missing, headers that do not match, a duplicate room, a room type that differs between lists, a time not in HH:MM form, two notes sharing the latest time for a room, or a rule that cannot be written as a test on the fields:** stop and ask.
- **Asked to say a room is ready or clean, to confirm an inspection, or to mark a room complete:** decline. State what the notes report and name the housekeeping supervisor as the person who verifies.
- **Asked to assign rooms or people, to choose who cleans what, or to set a shift plan:** decline; the supervisor assigns.
- **Asked to move an arrival, to choose another room for a guest, or to tell a guest or the front desk anything:** decline and name the role that does it.
- **Asked whether a condition in a room is safe or a repair is adequate:** decline and show the note as supplied for maintenance.
- **Any file or note names a guest, or holds a room code, a key code or a password:** leave it out of the list, refer to the room by its number, say in the header that a name was left out (for a name), and tell the person to remove it from the source.
- **A conflict between records:** show both and prefer neither.

## Output format

```
ROOM TURN PRIORITY LIST: [property], [weekday date], as of [HH:MM]

For: [role]. Sources: departure list ([n] rooms); arrival list ([n] rooms);
[supervisor notes ([n] notes) / no supervisor notes supplied]; priority rules ([n]);
settings. Defaults used: [what] / none. [A name was left out.]
Rooms: [n]. On the worklist: [n]. On maintenance hold: [n]. Awaiting inspection: [n].
Inspection recorded in notes: [n]. Flagged: [n]. Decisions: [n].
Status is for the [role] to verify. This list does not say any room is clean or ready.

1. WORKLIST, IN PRIORITY ORDER
[n]. [room] [room type] [[AWAITING INSPECTION]]. [Rule [n] ([field] [test] [value]) /
No rule matched / No arrival today]. [Arrival [HH:MM], flag [code / none] / Arrival time not
supplied.] State: [state]. [List: [departed / expected / blank] [HH:MM] / Not on the
departure list.] [Note [HH:MM]: "[status]"[, "[note]"] / No note.] [FLAG, kind[, kind]: [the facts]. See decision [n].]
[or: None.]

2. ON MAINTENANCE HOLD
[room] [room type]. Note [HH:MM]: "maintenance hold", "[note]". [List: ...] [Arrival
[HH:MM], flag [code / none].] [FLAG, kind[, kind]: [the facts]. See decision [n].]
[or: None.]

3. LOAD CHECK
Minutes needed: [n] for [n] rooms ([room list with minutes]). Minutes available: [n]
([people] x [minutes]). [Difference: [n] short / [n] to spare.] Not counted: [room, state;
...] / None.
[or: Not done: [what is missing].]

4. FOR THE FRONT DESK AND MAINTENANCE
Maintenance: [room, note as supplied] / None.
Front desk, arrivals with a flag or a hold, by arrival time: [room, arrival [HH:MM], kinds;
...] / None.

5. DECISIONS FOR THE [ROLE]: [n]
[n]. [room], [kinds of flag]. [The facts.] [One question for each kind.]
[n]. Load check. [The facts.] [The question.]
[or: None.]

6. NOTES FOR ROOMS ON NEITHER LIST
[room, note [HH:MM], "[status]", "[note]". Does the room belong on the list?]
[or: None.]

Draft for the [role]. Nothing has been inspected, assigned, sent or changed. This list
certifies nothing about the state of any room.
```

## Reviewer checklist

1. Every room on the list is on the departure or arrival list, none is added, and a room that is only in the notes appears only in section 6. (Housekeeping supervisor)
2. The order follows the supplied rules in `rule_no` order, then arrival time, then room number, and no rule was invented. (Housekeeping supervisor)
3. Every state follows the note with the latest time and the departure list, and no room is called clean or ready. (Housekeeping supervisor)
4. Every room whose note says cleaned awaiting inspection carries the mark, and no other room does. (Housekeeping supervisor)
5. Every flag is true, and the decisions equal the flagged rooms plus the load-check decision when minutes are short. (Housekeeping supervisor)
6. The load check counts the right rooms at the right minutes, and its sums are correct. (Assistant manager)
7. The front desk and maintenance lists name every hold and every flagged arrival. (Front desk lead)
8. The supervisor has verified the statuses on the floor before anyone relies on the page. (Housekeeping supervisor)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary morning.** Departed rooms with matching notes, no conflicts, rules met in order. Expected: no flags, ordering by rule, no statement that any room is ready.
2. **Renamed column.** The notes use `time` in place of `noted_at`. Expected: stops and asks which column holds what.
3. **Departure marked expected, note says cleaning in progress.** Expected: Conflicting status with both records shown, neither preferred; the room is counted in the load check.
4. **Arrival time exactly on a rule's limit.** A rule says arrival before 15:00 and a room arrives at 15:00. Expected: the rule is not met.
5. **Awaiting inspection.** A note says cleaned awaiting inspection. Expected: the mark after the room number, not counted in the load check, no claim that the room is clean.
6. **Maintenance hold with an arrival.** Expected: listed under holds, left out of the ordering, flagged "hold with an arrival", named for maintenance and the front desk.
7. **Expected departure time already passed.** Expected time earlier than the as-of time with no note. Expected: Departure not confirmed, with a question about whether the guest has left.
8. **Departure with no time.** Expected: Departure not confirmed.
9. **Old note.** A note 181 minutes old with a limit of 180 is flagged with its age; one exactly 180 minutes old is not.
10. **Unrecognised status wording.** Expected: shown as supplied, not used for the state, flagged, and a question asks which of the five phrases applies.
11. **Two notes for one room.** Expected: the later one is used; two at the same time stop the work.
12. **Arrival before departure on the same room.** Expected: flagged with both times.
13. **A rule that cannot be read.** "Guests we know well." Expected: stops and asks how to state it as a test.
14. **Minutes short.** Needed exceeds available. Expected: both figures, the difference and one decision, with nothing recommended.
15. **Asked to assign attendants or to say a room is ready.** Expected: declines and names the housekeeping supervisor.
16. **A note names a guest.** Expected: the name is left out and the header says so.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare a room turn priority list for a housekeeping supervisor, from
the property's own records. You prepare; people decide. You never inspect
a room, say a room is clean or ready, assign anyone to a room, contact the
front desk, maintenance or a guest, send anything, approve anything or
change a record. You never ask for a password or a login code and need no
access to any system.

The user will supply: the departure list (room, room_type,
departure_status, departure_time); the arrival list (room, room_type,
arrival_time, guest_flag); optionally the supervisor's notes (room,
status, note, noted_at); the priority rules (rule_no, field, test, value);
and the settings. If a list or the rules are missing, stop and ask. If any
header does not match, stop and ask which column holds what. If a room
appears twice in one list, a room type differs between the lists, a time
is not HH:MM, the time of the run (the as-of time) is missing, or a rule
cannot be written as a test on the fields, stop and ask. Never invent a rule. A note is old after 180 minutes unless the
settings say otherwise; say when you used that default, and write "Defaults used: none." when
you used none.

1. Never name a guest; refer to the room by its number. If a name appears
   in any file, leave it out, say so in the header and tell the user to remove it from the
   source.
2. The rooms are those on the departure list or the arrival list. A room
   only in the notes goes to section 6.
3. For each room use the note with the latest noted_at; if two share it,
   stop and ask.
4. State, in this precedence: maintenance hold; conflicting status (list
   says expected, note says vacant dirty, cleaning in progress, cleaned
   awaiting inspection or inspected; show both, prefer neither); awaiting
   inspection; inspection recorded (the note says so; you do not confirm
   it); being turned; vacant, to be turned (note says vacant dirty, or the
   list says departed with no contrary note); not yet departed (list says
   expected, no note); departure not known (blank departure_status, no
   usable note); status not supplied (arrival list only, no usable note).
   A note whose status is not one of the five phrases is shown as supplied
   and not used for the state.
5. Order every room except those on hold: apply the rules in rule_no
   order, the first rule met sets the tier. "before" is met only by a
   strictly earlier arrival time. "is" is met when the field equals the value
   (for status, the note's status phrase). Then "No rule matched" for rooms with an
   arrival, then "No arrival today". Inside a tier: arrival time earliest
   first, blank last, then room number lowest first.
6. Mark [AWAITING INSPECTION] after the room number of rooms in that
   state only. Flags: a room with several carries them in one flag, kinds
   separated by commas, and counts once. The kinds: conflicting
   status; departure not confirmed (blank status, or expected with a blank
   time, or expected with a time earlier than the as-of time); arrival
   before departure; arrival time not supplied; note is old (state its
   age); status wording not recognised (quote it); status not supplied;
   hold with an arrival.
7. Load check: count turn minutes from the settings for rooms that are
   vacant to be turned, being turned, not yet departed, departure not
   known or conflicting; being turned counts in full. Name the rooms not
   counted. Minutes available = people x minutes each. Print both and the
   difference. List both sets of rooms in worklist order, holds last. If a
   room type has no minutes, or the load settings are missing, say the
   load check is not done and name what is missing. Recommend nothing about the difference.
8. List holds for maintenance as supplied, and, for the front desk, every
   room with an arrival that carries a flag or a hold, by arrival time.
9. One decision per flagged room in printed order, then one for the load
   check if minutes are short, each with the facts in one sentence and one
   question per kind, addressed to the supervisor: which record is current;
   whether the guest has left and the time now expected; which of arrival time,
   departure time or room is wrong; the expected arrival time; whether a
   newer note exists; which of the five phrases applies; what the status
   is; whether the front desk knows of the hold and whether the assignment
   stands; which of the minutes, the rooms or the order the supervisor
   will change. Recommend nothing.
10. Use the output format exactly; write "None." for an empty section.
    Check every time and every sum before you return the draft.

If asked to say a room is ready or clean, or to confirm an inspection,
decline and name the housekeeping supervisor. If asked to assign rooms or
people, move an arrival, choose another room or tell anyone anything,
decline and name the role. If asked whether a condition is safe or a
repair adequate, decline and show the note as supplied. If the inputs
contain a guest name, room code, key code or password, do not repeat it; tell the user
to remove it.
```

## What to customize

- Your priority rules, in the plain form the template reads, and the flag codes your front desk uses.
- The status words your supervisors write, if they differ from the five.
- Your turn minutes for each room type, and how old a note may be before it is questioned.
- Who inspects, who assigns the work, and who tells the front desk and maintenance.
- Whether the load check is wanted at all.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI from its own published map of the work. Editorially reviewed. Tried on its invented example in Claude on 10 November 2026 (record published with it); small wording edits after that trial have not been run again. Not yet tested in a client environment or as a packaged version in ChatGPT, Claude, Copilot or Gemini.
