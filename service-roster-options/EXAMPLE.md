# Service roster options: an invented example

*Illustrative example with invented data.* The restaurant, the staff codes, the forecasts, the rates and the rules below are all invented, and the staff are reference codes, not people. The restaurant is an invented dining room inside an invented hotel, and the restaurant manager is asking for roster options for one weekend with an event on the Saturday. First come the inputs the manager supplied, in full, then the page the capability returned.

## The inputs

### 1. Settings

```
Department: Restaurant floor
Manager role: Restaurant manager
Window: Friday 20 November to Sunday 22 November 2026
Periods and shift length: Dinner 6 hours; Lunch 5 hours
Hourly rates: Server 16.00; Host 15.00
On-cost: 12 percent, applied to every role
Rules to check: A. No person works more than 3 shifts in the window.
Rules not to check here: B. Closers do not open the next morning
  (the manager checks this when naming people).
HR: sees any option that relies on pending staff or shows a rule flag.
Today: Tuesday 10 November 2026
```

### 2. Demand forecast (demand.csv)

```
date,period,measure,expected
2026-11-20,Dinner,covers,70
2026-11-21,Lunch,covers,45
2026-11-21,Dinner,covers,95
2026-11-21,Dinner,event guests,36
2026-11-22,Lunch,covers,60
```

### 3. Staffing rules (requirements.csv)

```
role,measure,per_staff,minimum_per_period
Server,covers,20,2
Server,event guests,12,2
Host,covers,60,1
```

### 4. Availability (availability.csv)

```
staff_ref,role,2026-11-20 Dinner,2026-11-21 Lunch,2026-11-21 Dinner,2026-11-22 Lunch
S01,Server,confirmed,confirmed,confirmed,unavailable
S02,Server,confirmed,unavailable,confirmed,confirmed
S03,Server,confirmed,confirmed,pending,confirmed
S04,Server,pending,confirmed,confirmed,
S05,Server,confirmed,confirmed,,pending
S06,Server,unavailable,pending,confirmed,confirmed
S07,Server,,confirmed,pending,confirmed
H01,Host,confirmed,confirmed,confirmed,confirmed
H02,Host,confirmed,unavailable,confirmed,pending
H03,Host,pending,,pending,unavailable
```

## The output

**SERVICE ROSTER OPTIONS: Restaurant floor, Friday 20 to Sunday 22 November 2026**

For: Restaurant manager. HR sees any option that relies on pending staff or shows a rule flag. Prepared Tuesday 10 November 2026 from the settings, the demand forecast (5 rows), the staffing rules (3 rows) and the availability file (10 staff).

**Assumptions as supplied.** Shift length: Dinner 6 hours, Lunch 5 hours. Rates: Server 16.00, Host 15.00 an hour. On-cost: 12 percent on every role. Rules checked: A (no more than 3 shifts per person in the window). Rules not checked here: B (closers do not open the next morning). No other pool of staff was supplied, so there are two options.

**Need by role and period.**

- Fri 20 Nov Dinner: Server 4 (70 covers, 20 each, rounded up). Host 2 (70 covers, 60 each, 1.17 rounded up).
- Sat 21 Nov Lunch: Server 3 (45 covers, 2.25 rounded up). Host 1 (45 covers at 60 each rounds up to 1, the minimum).
- Sat 21 Nov Dinner: Server 8 (5 for 95 covers plus 3 for 36 event guests, 12 each). Host 2 (95 covers; no host rule for event guests, so none counted).
- Sun 22 Nov Lunch: Server 3 (60 covers, exactly 3). Host 1 (60 covers, exactly 1).

**Availability counts (confirmed / pending / unavailable / unknown).**

- Server: Fri Dinner 4 / 1 / 1 / 1. Sat Lunch 5 / 1 / 1 / 0. Sat Dinner 4 / 2 / 0 / 1. Sun Lunch 4 / 1 / 1 / 1.
- Host: Fri Dinner 2 / 1 / 0 / 0. Sat Lunch 1 / 0 / 1 / 1. Sat Dinner 2 / 1 / 0 / 0. Sun Lunch 1 / 1 / 1 / 0.

**Option 1: confirmed staff only.**

- Server (staffed / uncovered / spare): Fri Dinner 4 / 0 / 0. Sat Lunch 3 / 0 / 2. Sat Dinner 4 / 4 / 0. Sun Lunch 3 / 0 / 1.
- Host: Fri Dinner 2 / 0 / 0. Sat Lunch 1 / 0 / 0. Sat Dinner 2 / 0 / 0. Sun Lunch 1 / 0 / 0.
- Pending staff needed: none.
- Rule A (no more than 3 shifts per person), checked as capacity: Server, confirmed staff can work at most 17 shifts under the limit against 14 staffed, no flag. Host, FLAG: confirmed hosts can work at most 5 shifts (H01 3, H02 2, counting only periods where each is confirmed) against 6 staffed. One host shift cannot be filled from confirmed staff without a fourth shift for someone. The headcounts above are left as they are.
- Cost: 112 staffed hours (Server 78, Host 34). Wages 1,758.00; with on-cost 1,968.96. Uncovered: 4 server places on Sat Dinner, 24 hours.

**Option 2: confirmed and pending staff.**

- Server (staffed / uncovered / spare): Fri Dinner 4 / 0 / 1. Sat Lunch 3 / 0 / 3. Sat Dinner 6 / 2 / 0. Sun Lunch 3 / 0 / 2.
- Host: Fri Dinner 2 / 0 / 1. Sat Lunch 1 / 0 / 0. Sat Dinner 2 / 0 / 1. Sun Lunch 1 / 0 / 1.
- Pending staff needed, at least 3 shifts: 2 server shifts on Sat Dinner (all pending servers available that period) and 1 host shift, because confirmed hosts reach only 5 of the 6 host shifts under Rule A.
- Rule A, checked as capacity: Server 21 against 16, Host 8 against 6, no flag.
- Cost: 124 staffed hours (Server 90, Host 34). Wages 1,950.00; with on-cost 2,184.00. Uncovered: 2 server places on Sat Dinner, 12 hours.

**Option 3: not supplied (no other pool).**

**Comparison.**

- Option 1: 20 shifts staffed, 4 uncovered (24 hours), no pending staff, one rule flag (Host), 1,968.96 with on-cost.
- Option 2: 22 shifts staffed, 2 uncovered (12 hours), at least 3 pending shifts, no rule flag, 2,184.00 with on-cost.
- Difference: Option 2 staffs 2 more places for 215.04 more.
- For reference, filling every need would cost 2,399.04 with on-cost (2,142.00 in wages, 102 server hours and 34 host hours).

**Unknowns that remain.** Availability is blank for S07 on Fri Dinner, S05 on Sat Dinner, S04 on Sun Lunch and H03 on Sat Lunch. They are counted as unknown in every option.

**Questions for the restaurant manager.**

1. Sat Dinner is short in both options (4 places, or 2 with both pending servers). Will you ask about the blank Sat Dinner cell (S05), and how do you want to handle the shortfall that remains?
2. Option 1 leaves one host shift that only a fourth shift for someone can fill. Will you accept that, or work from Option 2?
3. Option 2 depends on at least 3 pending shifts (two servers on Sat Dinner and one host). Who will ask for those confirmations?
4. Rule B was not checked. Will you check it when you name people?
5. Both options go to HR, because Option 1 has a rule flag and Option 2 relies on pending staff; which do you bring first?

Every figure traces to the five demand rows, the three staffing rules, the ten availability rows and the settings above. The page names no one to work a shift, ranks no one, and sends and publishes nothing.
