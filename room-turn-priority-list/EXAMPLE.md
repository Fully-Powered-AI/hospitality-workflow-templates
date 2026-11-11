# Room turn priority list: an invented example

*Illustrative example with invented data.* The hotel, the rooms, the codes and every record below are invented. Wexcombe Lane Hotel is an invented hotel. Its housekeeping supervisor plans the morning of Friday 4 December 2026. No guest is named.

The inputs come first, in full, so the template can be run on them. The priority list follows.

## The inputs

### 1. Settings (typed by the housekeeping supervisor)

```
Property: Wexcombe Lane Hotel
Prepared for: housekeeping supervisor
Day: Friday 4 December 2026
As of: 10:30
Turn minutes: King 30, Queen 30, Accessible Queen 40, Suite 55
People turning rooms: 2
Minutes each has left: 120
```

No limit for the age of a note was given, so the default of 180 minutes applies.

### 2. Departure list

```
room,room_type,departure_status,departure_time
101,King,departed,08:40
102,King,departed,09:15
104,Queen,expected,11:00
105,King,expected,
108,Suite,departed,10:05
110,Accessible Queen,departed,06:45
112,King,,
114,Queen,expected,11:00
116,Suite,expected,12:00
```

### 3. Arrival list

```
room,room_type,arrival_time,guest_flag
101,King,14:30,none
102,King,12:00,early-arrival-confirmed
104,Queen,15:00,none
108,Suite,16:00,group-block
110,Accessible Queen,13:00,accessible-room-confirmed
112,King,15:30,none
114,Queen,10:45,none
116,Suite,17:00,group-block
118,Queen,16:30,none
120,Queen,14:00,none
```

### 4. The supervisor's room-status notes

```
room,status,note,noted_at
101,cleaned awaiting inspection,Attendant finished; waiting for the check,09:50
102,cleaning in progress,Bathroom,10:10
104,cleaning in progress,Attendant started on the room,10:20
108,maintenance hold,Shower valve leaking; maintenance called,10:05
110,vacant dirty,,07:15
112,key returned to desk,Key on the desk; no word on the room,09:40
118,inspected,Inspected by the supervisor,09:20
```

### 5. Priority rules

```
rule_no,field,test,value
1,guest_flag,is,accessible-room-confirmed
2,guest_flag,is,early-arrival-confirmed
3,arrival_time,before,15:00
4,guest_flag,is,group-block
```

## The priority list

ROOM TURN PRIORITY LIST: Wexcombe Lane Hotel, Friday 4 December 2026, as of 10:30

For: housekeeping supervisor. Sources: departure list (9 rooms); arrival list (10 rooms); supervisor notes (7 notes); priority rules (4); settings. Defaults used: a note is old after 180 minutes.
Rooms: 11. On the worklist: 10. On maintenance hold: 1. Awaiting inspection: 1. Inspection recorded in notes: 1. Flagged: 7. Decisions: 8.
Status is for the housekeeping supervisor to verify. This list does not say any room is clean or ready.

1. WORKLIST, IN PRIORITY ORDER
1. 110 Accessible Queen. Rule 1 (guest_flag is accessible-room-confirmed). Arrival 13:00, flag accessible-room-confirmed. State: Vacant, to be turned. List: departed 06:45. Note 07:15: "vacant dirty". FLAG, note is old: the note is 3 hours 15 minutes old, over the 180-minute limit. See decision 1.
2. 102 King. Rule 2 (guest_flag is early-arrival-confirmed). Arrival 12:00, flag early-arrival-confirmed. State: Being turned. List: departed 09:15. Note 10:10: "cleaning in progress", "Bathroom".
3. 114 Queen. Rule 3 (arrival_time before 15:00). Arrival 10:45, flag none. State: Not yet departed. List: expected 11:00. No note. FLAG, arrival before departure: the arrival is 10:45 and the expected departure is 11:00. See decision 2.
4. 120 Queen. Rule 3 (arrival_time before 15:00). Arrival 14:00, flag none. State: Status not supplied. Not on the departure list. No note. FLAG, status not supplied. See decision 3.
5. 101 King [AWAITING INSPECTION]. Rule 3 (arrival_time before 15:00). Arrival 14:30, flag none. State: Awaiting inspection. List: departed 08:40. Note 09:50: "cleaned awaiting inspection", "Attendant finished; waiting for the check".
6. 116 Suite. Rule 4 (guest_flag is group-block). Arrival 17:00, flag group-block. State: Not yet departed. List: expected 12:00. No note.
7. 104 Queen. No rule matched. Arrival 15:00, flag none. State: Conflicting status. List: expected 11:00. Note 10:20: "cleaning in progress", "Attendant started on the room". FLAG, conflicting status: the list shows the guest expected to leave at 11:00 and the note, written at 10:20, says the room is being cleaned. See decision 4.
8. 112 King. No rule matched. Arrival 15:30, flag none. State: Departure not known. List: no departure status, no time. Note 09:40: "key returned to desk", "Key on the desk; no word on the room". FLAG, departure not confirmed, status wording not recognised: the list gives no departure status or time, and the note's status "key returned to desk" is not one of the five phrases. See decision 5.
9. 118 Queen. No rule matched. Arrival 16:30, flag none. State: Inspection recorded. Not on the departure list. Note 09:20: "inspected", "Inspected by the supervisor".
10. 105 King. No arrival today. State: Not yet departed. List: expected, no time. No note. FLAG, departure not confirmed: the list gives no expected departure time. See decision 6.

2. ON MAINTENANCE HOLD
108 Suite. Note 10:05: "maintenance hold", "Shower valve leaking; maintenance called". List: departed 10:05. Arrival 16:00, flag group-block. FLAG, hold with an arrival: an arrival is on the list for this room. See decision 7.

3. LOAD CHECK
Minutes needed: 245 for 7 rooms (110 Accessible Queen 40, 102 King 30, 114 Queen 30, 116 Suite 55, 104 Queen 30, 112 King 30, 105 King 30). Minutes available: 240 (2 x 120). Difference: 5 short. Not counted: 120, Status not supplied; 101, Awaiting inspection; 118, Inspection recorded; 108, on maintenance hold.

4. FOR THE FRONT DESK AND MAINTENANCE
Maintenance: 108, "Shower valve leaking; maintenance called".
Front desk, arrivals with a flag or a hold, by arrival time: 114, arrival 10:45, arrival before departure; 110, arrival 13:00, note is old; 120, arrival 14:00, status not supplied; 104, arrival 15:00, conflicting status; 112, arrival 15:30, departure not confirmed, status wording not recognised; 108, arrival 16:00, hold with an arrival.

5. DECISIONS FOR THE HOUSEKEEPING SUPERVISOR: 8
1. 110, note is old. The only note for the room, "vacant dirty", was written at 07:15 and is 3 hours 15 minutes old at 10:30; the guest departed at 06:45 and an arrival with a confirmed accessible room is due at 13:00. Is there a newer note, or what is the room's status now?
2. 114, arrival before departure. The arrival is listed at 10:45 and the guest is expected to depart at 11:00. Is the arrival time, the departure time or the room wrong?
3. 120, status not supplied. The room has an arrival at 14:00, is not on the departure list and has no note. What is its status?
4. 104, conflicting status. The departure list shows the guest expected to depart at 11:00; the note written at 10:20 says "cleaning in progress". Which record is current, and who confirms it?
5. 112, departure not confirmed, status wording not recognised. The list gives no departure status or time, and the note says "key returned to desk", which is not one of the five phrases. Has the guest left, and what time is now expected? Which of the five phrases applies to the room?
6. 105, departure not confirmed. The departure is expected and the list gives no time. Has the guest left, and what time is now expected?
7. 108, hold with an arrival. The room is on maintenance hold per the note at 10:05, and an arrival with a group-block flag is listed at 16:00. Does the front desk know of the hold, and does the assignment stand?
8. Load check. 245 minutes are needed and 240 are available, 5 short. Which of the minutes, the rooms or the order will the supervisor change, if any?

6. NOTES FOR ROOMS ON NEITHER LIST
None.

Draft for the housekeeping supervisor. Nothing has been inspected, assigned, sent or changed. This list certifies nothing about the state of any room.
