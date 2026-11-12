# Trial: Public guest review reply, run on its invented example

- **Product:** Claude, run in Claude Code

Model: Claude Sonnet 5.5 (model ID claude-sonnet-5-5). The assistant that ran this trial did not write the template, but it had read the template, the example and an earlier trial record of this workflow template before drafting.

Date: 2026-11-10

The inputs are the invented example in `public/example.md` (Hotel Q, a made-up 40-room hotel, and an invented review). No client data was used.

This is the second run on 10 November 2026. The first run was made before the instruction block was revised (names rule, missing stop conditions, over-limit ranking, action-line rules, one order for the private notes) and before "Platform limits: none" was added to the example's inputs. That run's record has been replaced by this one, because the instruction block it tested no longer exists in that form.

## Inputs used

The review, the four verified service actions (A1 to A4), the response guidance (RG-1) and the platform limits line (none) from "The inputs" in `public/example.md`.

This trial is not independent. The example's published reply, and the first run's reply, were seen before this reply was written. The reply below was written from the revised instruction block, but its close likeness to the published example should be read with that in mind.

## What came out

The revised instruction block and the output format were followed as written.

```
PUBLIC GUEST REVIEW REPLY: Review site P, posted Sunday 8 November 2026, 3 of 5
Status: Draft for Dana. Not posted. Dana checks accuracy and the guest's privacy before approving.
Sources: the review; actions A1 to A4 as supplied; RG-1, dated 1 October 2026.

WHAT THE REVIEW RAISED
R1. Praise: the location and the breakfast. Thanked.
R2. Complaint: noise on the first night from building work. Apologised for; no action listed.
R3. Complaint: the lift out of order on the day of departure. Apologised for; answered by A2.
R4. Praise: the front desk moved the guest to a quieter room. Acknowledged; A1.
R5. Wish: to have been warned about the building work at booking. Not answered in public; A3 is marked no.

PUBLIC REPLY (99 words, limit 100)
Hello TravellerR, thank you for your review and for your kind words about our location and breakfast. I am sorry the building work made your first night noisy and that the lift was out of order on the day you left. I am glad our front desk could move you to a quieter room for the second night. The lift has since been repaired and is back in service. If you would like to talk with us about your stay, please contact our guest relations team through the contact page on our website.
Dana, Guest Relations Manager, Hotel Q

WHERE EACH SENTENCE COMES FROM
1. "Hello TravellerR, thank you ... location and breakfast." Greeting from RG-1; R1.
2. "I am sorry the building work ... the day you left." R2, R3.
3. "I am glad our front desk ... second night." R4; A1 (the review says the move was made for the reviewer).
4. "The lift has since been repaired and is back in service." A2 (marked yes; confirmed after the review was posted).
5. "If you would like to talk with us ... our website." Contact route from RG-1.
6. Sign-off: RG-1.

PRIVATE FOLLOW-UP NOTES (not for posting)
Open points: R5. The guest wished to be warned at booking. A3 is confirmed but marked no for public mention.
Confirmed actions kept out of the public reply: A3, not marked for public mention. A4, not marked for public mention.
Decisions for Dana: 1. Whether anything is said publicly about A3. 2. Whether anything about A4 is said to the guest privately; this workflow template does not draft that.
Claims in the review that conflict with a confirmed action: none.
Serious allegations: none.
Names to handle: none (no staff, guest or child is named; "TravellerR" is the name shown).
Tell after posting: duty manager, marketing.

LEFT OUT OF THE PUBLIC REPLY
Dates and length of stay, room details, rates, charges and the refund, booking channel, who travelled, staff names, and any action marked no. The stay details in the reply are those the review states: the first and second nights, the building work, the lift and the quieter room.

Draft for Dana's approval. Nothing has been posted, sent or recorded.
```

## What was observed

- Every part of the output format was produced, in the format's order, including "Names to handle" and numbered decisions. Nothing in the inputs triggered a stop condition. The review has no allegation, no named person and no request for compensation, and no card number or code.
- The reply is 99 words against a limit of 100, counted with `wc -w` including the sign-off, so the margin is one word. The over-limit rule was not exercised.
- Differences from the published example: about five small wording choices ("for your kind words", "I am" for "I'm"); shorter source lines. The decisions and kept-out actions match.
- No fact appears in either output that is not in the inputs. One thing is worth a check by the manager: A2 says the passenger lift was repaired, and the reply says "the lift", taking that to be the lift the guest meant. The review does not say which lift.
- The new action-line rules were read as follows. A1 speaks of "a guest"; the review itself says the front desk moved the reviewer, so A1 was used. A2 was confirmed on 9 November, after the review was posted; "has since" was used and the date not stated.
- Not exercised by this example: the stop conditions on language, card numbers and names, the over-limit ranking and the empty action list. The acceptance tests for them remain proposals.
- Nothing in the template asked for a password or code, and nothing was posted or sent.
- Rule clarifications made after this run, not re-run: the instruction block now also lists loyalty status among the details to leave out, says one sentence may apologise for two complaints, and describes the output when a review contains an allegation. None of these changes what this example's inputs call for, and the output above was not re-generated.
