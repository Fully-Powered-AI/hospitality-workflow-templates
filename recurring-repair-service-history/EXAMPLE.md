# Recurring repair service history: an invented example

*Illustrative example with invented data.* The hotel, the equipment, the contractors, the dates and the disruptions below are all invented. The hotel is an invented 60-room property called Alder Quay Inn. Its facilities manager asks for the brief; people are referred to by role and contractors by letter.

The inputs come first, in full, so the template can be run on them. The brief follows. Its section headings and room areas are set in bold and italic for the page; the template prints them in capitals.

## The inputs

### 1. Settings (typed by the facilities manager)

```
Property: Alder Quay Inn
Prepared for: facilities manager
As-of date: 2026-11-02
Review window: 180 days (defaults used for the rest)
Repeat level: 3 work orders (default)
Check after repair: 14 days (default)
Urgent words: injury, injured, trapped, stuck between, smoke, fire, gas, shock, sparks (default)
```

### 2. Asset register

```
asset_id,asset,area,inspection_interval_days
A-101,Guest lift 2,East wing lifts,90
A-102,Ice machine,Level 2 service alcove,
A-103,Air-conditioning unit,Room 214,180
A-104,Boiler feed pump,Plant room,90
A-105,Pool filter pump,Pool deck,60
```

### 3. Work orders

```
wo_id,asset_id,opened,closed,reported_issue,done_by
W-3001,A-101,2026-06-11,2026-06-12,Doors stick,Lift Contractor A
W-3002,A-103,2026-06-20,2026-06-22,Not cooling,HVAC Contractor B
W-3003,A-104,2026-02-10,2026-02-11,Noise from pump,In-house technician
W-3004,A-101,2026-07-29,2026-07-30,doors stick ,Lift Contractor A
W-3005,A-102,2026-07-30,2026-08-02,No ice,Ice machine supplier C
W-3006,A-103,2026-08-18,2026-08-19,not cooling,HVAC Contractor B
W-3007,A-199,2026-08-25,2026-08-25,Tap dripping,In-house technician
W-3008,A-104,2026-09-02,2026-09-02,Pump noisy; smoke smell near motor,In-house technician
W-3009,A-101,2026-09-15,2026-09-15,doors stick,In-house technician
W-3010,A-102,2026-09-30,2026-10-01,no ice,Ice machine supplier C
W-3011,A-103,2026-10-20,2026-10-21,Water leak at unit,In-house technician
W-3012,A-101,2026-10-27,,Car stuck between floors,Lift Contractor A
```

### 4. Inspection records

```
asset_id,inspected_on,result_note
A-101,2026-04-21,Monthly lift check complete; no defects noted
A-101,2026-07-02,Visual check; doors noted stiff
A-103,2026-09-01,Filter cleaned
A-104,2026-08-14,Routine check; nothing noted
A-105,2026-10-05,Routine check; nothing noted
```

### 5. Service-impact notes

```
note_id,date,area,asset_id,impact,confirmed_by
N-1,2026-06-12,East wing lifts,A-101,Lift out of service about 6 hours; luggage carried up stairs,front desk supervisor
N-2,2026-07-29,East wing lifts,A-101,Lift out of service about 4 hours,front desk supervisor
N-3,2026-10-27,East wing lifts,A-101,Lift out of service from 14:00; upper-floor guests affected,duty manager
N-4,2026-06-20,Room 214,A-103,Room taken out of sale for 2 nights,housekeeping supervisor
N-5,2026-10-20,Room 214,A-103,Room out of sale for 1 night; wet carpet,housekeeping supervisor
N-6,2026-09-29,Level 2 service alcove,A-102,Guests on level 2 reported no ice,front desk supervisor
N-7,2026-10-12,Pool deck,,Pool closed for part of the day,
N-8,2026-08-10,Room 305,,Guests reported the television not working,front desk supervisor
```

## The brief

**RECURRING REPAIR SERVICE HISTORY: Alder Quay Inn, as of 2026-11-02**

For: facilities manager. Window: 2026-05-06 to 2026-11-02 (180-day setting, both ends included).
Repeat level: 3 work orders.
Check after repair: 14 days.
Sources: asset register (5 items); work orders (12 rows); inspection records (5 rows); service notes (8 rows); settings. Defaults used: repeat level, check period and urgent words.
Urgent words match whole words and phrases as listed; other forms are not matched.
Work orders in the window: 11; outside it: 1. At the repeat level: 2. Below it with a confirmed interruption: 1. Notes not linked: 2. Records that did not fit: 1. Decisions: 7.
This brief finds no cause, certifies no equipment and advises neither repair nor replacement.

**1. Attention first**

W-3008, 2026-09-02, A-104 Boiler feed pump, Plant room: "Pump noisy; smoke smell near motor". Matched: "smoke". See decision 7.
W-3012, 2026-10-27, A-101 Guest lift 2, East wing lifts: "Car stuck between floors". Matched: "stuck between". See decision 1.

**2. Equipment at the repeat level, by area**

*East wing lifts*

1. A-101 Guest lift 2. Work orders in window: 4 (W-3001 opened 2026-06-11, closed 2026-06-12, Lift Contractor A; W-3004 opened 2026-07-29, closed 2026-07-30, Lift Contractor A; W-3009 opened 2026-09-15, closed 2026-09-15, In-house technician; W-3012 opened 2026-10-27, open, Lift Contractor A).
   Same wording: "Doors stick" 3 times (W-3001, W-3004, W-3009).
   Confirmed interruptions: 3 (N-1 2026-06-12, "Lift out of service about 6 hours; luggage carried up stairs", confirmed by front desk supervisor; N-2 2026-07-29, "Lift out of service about 4 hours", confirmed by front desk supervisor; N-3 2026-10-27, "Lift out of service from 14:00; upper-floor guests affected", confirmed by duty manager). Alongside: W-3001 with N-1; W-3004 with N-2; W-3012 with N-3.
   Inspection: latest 2026-07-02, 123 days before, interval 90 days, OVERDUE by 33 days. Result as supplied: "Visual check; doors noted stiff".
   Check within 14 days of closing: recorded 0; missing 3 (W-3001, W-3004, W-3009); not yet due 0; open work orders not checked 1.
   See decision 1.

*Room 214*

2. A-103 Air-conditioning unit. Work orders in window: 3 (W-3002 opened 2026-06-20, closed 2026-06-22, HVAC Contractor B; W-3006 opened 2026-08-18, closed 2026-08-19, HVAC Contractor B; W-3011 opened 2026-10-20, closed 2026-10-21, In-house technician).
   Same wording: "Not cooling" 2 times (W-3002, W-3006).
   Confirmed interruptions: 2 (N-4 2026-06-20, "Room taken out of sale for 2 nights", confirmed by housekeeping supervisor; N-5 2026-10-20, "Room out of sale for 1 night; wet carpet", confirmed by housekeeping supervisor). Alongside: W-3002 with N-4; W-3011 with N-5.
   Inspection: latest 2026-09-01, 62 days before, interval 180 days, within interval. Result as supplied: "Filter cleaned".
   Check within 14 days of closing: recorded 1 (W-3006); missing 1 (W-3002); not yet due 1 (W-3011); open work orders not checked 0.
   See decision 2.

**3. Below the repeat level, with a confirmed interruption**

3. A-102 Ice machine, Level 2 service alcove. Work orders in window: 2 (W-3005 opened 2026-07-30, closed 2026-08-02, Ice machine supplier C; W-3010 opened 2026-09-30, closed 2026-10-01, Ice machine supplier C).
   Same wording: "No ice" 2 times (W-3005, W-3010).
   Confirmed interruptions: 1 (N-6 2026-09-29, "Guests on level 2 reported no ice", confirmed by front desk supervisor). Alongside: none.
   Inspection: no inspection record supplied.
   Check within 14 days of closing: recorded 0; missing 2 (W-3005, W-3010); not yet due 0; open work orders not checked 0.
   FLAG: wording repeated; no inspection record; check missing after W-3005 and W-3010; interruption N-6 with no work order alongside. See decision 3.

Also worked on in the window, with no confirmed interruption: A-104 Boiler feed pump, 1 work order (W-3008).

**4. Notes not linked to equipment**

N-7, 2026-10-12, Pool deck: "Pool closed for part of the day". Reasons: Not confirmed; No asset ID. Area matches: A-105 Pool filter pump. See decision 4.
N-8, 2026-08-10, Room 305: "Guests reported the television not working". Reasons: No asset ID. No area match. See decision 5.

**5. Records that did not fit**

W-3007, opened 2026-08-25, asset ID A-199 is not in the register: "Tap dripping". See decision 6.

**6. Decisions for the facilities manager: 7**

1. A-101 Guest lift 2. W-3012 is open and its wording matched "stuck between"; four work orders in the window, "Doors stick" three times, three confirmed interruptions, inspection overdue by 33 days, no check recorded after any of three closed work orders. Has W-3012 been passed through the property's own urgent route, and by whom? Who owns W-3012 and when is it expected to close? Do the contractor reports for W-3001, W-3004 and W-3009 state a cause, since the work orders do not? Is there an inspection record after 2026-07-02 that was not supplied, or was the interval missed? Was a check made after W-3001, W-3004 and W-3009 and not recorded?
2. A-103 Air-conditioning unit. Three work orders, "Not cooling" twice, two confirmed interruptions, inspection within interval, no check recorded after W-3002. Do the contractor reports for W-3002 and W-3006 state a cause? Was a check made after W-3002 and not recorded? (The period for W-3011 ends on 2026-11-04.)
3. A-102 Ice machine. Two work orders, "No ice" twice, one confirmed interruption (N-6, 2026-09-29) with no work order alongside, no inspection record, no check recorded after W-3005 or W-3010. Do the supplier's reports state a cause? Was a work order raised for N-6 under another equipment ID, or not at all? Is there an inspection record that was not supplied? Was a check made after W-3005 and W-3010 and not recorded?
4. N-7, Pool deck. Not confirmed, and no equipment named; the area matches A-105 Pool filter pump. Who can confirm the note, and which equipment does it concern?
5. N-8, Room 305. Confirmed by the front desk supervisor, no equipment named, no area in the register. Which equipment, if any, does it concern?
6. W-3007, asset ID A-199. Is the register or the work order wrong?
7. W-3008, A-104 Boiler feed pump, opened and closed 2026-09-02, In-house technician: "Pump noisy; smoke smell near motor", matched "smoke". The pump has no confirmed interruption and is listed only under "Also worked on". Has W-3008 been passed through the property's own urgent route, and by whom?

Draft for the facilities manager. Nothing has been sent, ordered, certified or changed. Repair or replacement is not addressed here.
