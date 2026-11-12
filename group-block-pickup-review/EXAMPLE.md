# Group room block pickup review: an invented example

*Illustrative example with invented data.* The property, the group, the reservations, the people and every figure below are invented. "Hotel A" is an invented 90-room hotel and "Group G" an invented conference group with a block of 101 room nights over three nights in March 2027. The revenue manager runs the review; the group-sales owner and the account owner for Group G respond. First come the inputs the revenue manager supplied, in full, then the brief the workflow template returned.

## The inputs

### 1. Settings

```
Block to review: BLK-A1
Run date: 2027-02-01
Property: Hotel A
Revenue manager: revenue manager
Group-sales owner: group-sales owner
Account owner: account owner for Group G
```

### 2. Block export (block.csv)

```
block_ref,group,stay_date,room_type,blocked_rooms,reported_pickup
BLK-A1,Group G,2027-03-09,King,20,14
BLK-A1,Group G,2027-03-09,Twin,5,6
BLK-A1,Group G,2027-03-10,King,30,22
BLK-A1,Group G,2027-03-10,Twin,12,9
BLK-A1,Group G,2027-03-11,King,24,10
BLK-A1,Group G,2027-03-11,Twin,10,3
BLK-B2,Group H,2027-03-10,King,8,8
```

### 3. Booking pickup (pickup.csv)

```
block_ref,reservation_id,stay_date,room_type,rooms,status
BLK-A1,R101,2027-03-09,King,5,confirmed
BLK-A1,R102,2027-03-09,King,6,confirmed
BLK-A1,R103,2027-03-09,King,3,confirmed
BLK-A1,R104,2027-03-09,King,2,cancelled
BLK-A1,R201,2027-03-09,Twin,4,confirmed
BLK-A1,R202,2027-03-09,Twin,2,confirmed
BLK-A1,R101,2027-03-10,King,5,confirmed
BLK-A1,R102,2027-03-10,King,6,confirmed
BLK-A1,R103,2027-03-10,King,3,confirmed
BLK-A1,R105,2027-03-10,King,8,confirmed
BLK-A1,T303,2027-03-10,King,2,tentative
BLK-A1,R201,2027-03-10,Twin,4,confirmed
BLK-A1,R202,2027-03-10,Twin,2,confirmed
BLK-A1,R203,2027-03-10,Twin,3,confirmed
BLK-A1,R101,2027-03-11,King,5,confirmed
BLK-A1,R105,2027-03-11,King,4,confirmed
BLK-A1,T301,2027-03-11,King,4,tentative
BLK-A1,R202,2027-03-11,Twin,2,confirmed
BLK-A1,R203,2027-03-11,Twin,1,confirmed
BLK-A1,T302,2027-03-11,Twin,2,tentative
BLK-A1,R901,2027-03-12,King,2,confirmed
BLK-A1,R902,2027-03-10,Suite,1,confirmed
BLK-B2,R950,2027-03-10,King,8,confirmed
```

### 4. Approved agreement summary (agreement.csv)

```
block_ref,review_date,release_date,minimum_pickup_percent,terms_status,summary_note
BLK-A1,2027-02-03,2027-02-09,70,approved,Summary approved by the group-sales owner on 2027-01-18
```

### 5. Room inventory (inventory.csv)

```
stay_date,room_type,rooms_in_inventory
2027-03-09,King,60
2027-03-09,Twin,30
2027-03-10,King,60
2027-03-10,Twin,30
2027-03-11,King,60
2027-03-11,Twin,30
```

## The brief

```
GROUP BLOCK PICKUP BRIEF: Group G, block BLK-A1

For: revenue manager and group-sales owner, Hotel A. Prepared 2027-02-01. Review date 2027-02-03 (2 days away). Release date 2027-02-09 (8 days away).
Inputs: block export block.csv; booking pickup pickup.csv; agreement summary agreement.csv; room inventory inventory.csv. Rows for other blocks ignored: 1 in the block export, 1 in the booking rows.
Terms status in the approved summary: approved.

Pickup at a glance
Blocked room nights: 101.
Confirmed in the block: 62 (61.4%).
Stated minimum in the approved summary: 70%. Pickup is 8.6 points below it.
Unfilled room nights: 39. Row 2027-03-11 King is unreconciled, so its 15 are not settled.
Tentative room nights, not counted: 8. If every tentative room were confirmed, unfilled would be 31.
Cancelled room nights ignored: 2.

By night and room type
2027-03-09: blocked 25, confirmed in block 19 (76.0%), unfilled 6, tentative 0. Unfilled is 6.7% of the 90 rooms in inventory.
  King: blocked 20, confirmed 14, reported by the export 14, unfilled 6, tentative 0.
  Twin: blocked 5, confirmed 6, reported by the export 6, unfilled 0, tentative 0. One room above the block.
2027-03-10: blocked 42, confirmed in block 31 (73.8%), unfilled 11, tentative 2. Unfilled is 12.2% of the 90 rooms in inventory.
  King: blocked 30, confirmed 22, reported by the export 22, unfilled 8, tentative 2.
  Twin: blocked 12, confirmed 9, reported by the export 9, unfilled 3, tentative 0.
2027-03-11: blocked 34, confirmed in block 12 (35.3%), unfilled 22, tentative 6. Unfilled is 24.4% of the 90 rooms in inventory.
  King: blocked 24, confirmed 9, reported by the export 10, unfilled 15, tentative 4. Unreconciled.
  Twin: blocked 10, confirmed 3, reported by the export 3, unfilled 7, tentative 2.

Counts that do not reconcile
2027-03-11 King: the export reports 10 rooms picked up and the booking rows show 9 confirmed. The brief uses 9. Unresolved.
2027-03-09 Twin: 6 rooms confirmed against 5 blocked, one above the block. Unresolved.

Outside the block
R901, 2027-03-12, King, 2 rooms, confirmed: the night is not in the block.
R902, 2027-03-10, Suite, 1 room, confirmed: the room type is not in the block.
Neither is counted anywhere above.

Questions for the account owner
1. 2027-03-11 King: the export reports 10 rooms picked up and the booking rows show 9 confirmed. Which figure is right?
2. 2027-03-09 Twin: 6 rooms are confirmed against 5 blocked. Was the sixth room agreed as an addition to the block?
3. R901 (2 King rooms on 2027-03-12) and R902 (1 Suite room on 2027-03-10) name the block but fall outside its nights or room types. Do they belong to Group G?
4. 2027-03-10 King: 2 tentative rooms against 8 unfilled King room nights. Does the group expect the tentative rooms to confirm before the release date, 2027-02-09?
5. 2027-03-11: King has 4 tentative rooms against 15 unfilled room nights (not settled), and Twin has 2 tentative rooms against 7 unfilled. Does the group expect the tentative rooms to confirm before 2027-02-09?
6. 2027-03-11 has the lowest pickup, 35.3% (12 of 34). Has the group said whether it expects more rooms that night?
7. Pickup is 61.4%, 8.6 points below the stated minimum of 70% in the approved summary. Does the group expect to close the gap before 2027-02-09?

Decisions for the revenue manager and group-sales owner
1. Whether to release any unfilled rooms, and which. Facts: 39 room nights unfilled, 8 tentative, release date 2027-02-09 (8 days away). The count for 2027-03-11 King is unreconciled, so its 15 unfilled room nights are not settled. This brief releases nothing.
2. Whether to put a revised offer to the group. Facts: pickup 61.4% against a stated minimum of 70%; lowest night 2027-03-11 at 35.3%. This brief sends nothing.

Check lines
Blocked 101 - confirmed in block 62 = unfilled 39.
Confirmed in block rows 63 = confirmed in block 62 + above the block 1.
Nights: blocked 25 + 42 + 34 = 101; confirmed in block 19 + 31 + 12 = 62; unfilled 6 + 11 + 22 = 39.

Brief for the revenue manager and group-sales owner. Nothing has been released, sent or changed. They decide any release or revised offer.
```
