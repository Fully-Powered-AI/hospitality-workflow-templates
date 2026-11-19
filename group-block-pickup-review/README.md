# Group room block pickup review

Before a room block's review or release date, get rooms blocked, confirmed and unfilled in one brief. A person decides any release.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See Group room block pickup review on our website](https://fullypowered.ai/workflows/group-block-pickup-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the invented ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Hospitality · Sales · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/group-block-pickup-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review)*

## The outcome

Before the review meeting, the revenue manager and the group-sales owner look at the same page. It shows, night by night and room type by room type, how many rooms the group blocked, how many are confirmed, and how many room nights are still unfilled. Tentative bookings are shown on their own line and never counted as pickup.

The brief also shows where the numbers disagree: a pickup figure in the block export that differs from the bookings behind it, a room type with more confirmed rooms than the block holds, a reservation that names the block but falls outside its nights or room types. These stay open until a person settles them. It ends with questions for the account owner and the two decisions that belong to the revenue manager and group-sales owner: whether to release rooms and whether to put a revised offer to the group. Neither is made for them.

## Who starts the work, and when

The revenue manager or the group-sales owner runs it when a block is approaching its review date or its release date, with the block export, the booking rows and the approved summary of the group agreement in hand. They run it once per block, and again if the bookings change before the meeting.

## What they supply

- The block export: for each night and room type, the rooms blocked and the pickup the system reports.
- The booking rows for the block: reservation, night, room type, rooms and status.
- The approved summary of the group agreement: the review date, the release date, the stated minimum pickup and whether the terms are agreed or disputed.
- The room inventory: rooms in inventory by night and room type.
- A few settings: the block to review, today's date and the people involved.

## What comes out

One brief in a fixed order: the pickup at a glance, a line for each night and room type, the counts that do not reconcile, any reservation outside the block, questions for the account owner, the two decisions and check lines that tie the totals. If a file's column headers do not match, it stops and asks before counting anything. If the approved summary shows the terms as disputed, the brief gives the room counts but does not compare them with the agreement and frames no decision.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Operations & process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review), where the review of a block is a routine step before its dates.
- [Sales](https://fullypowered.ai/functions/sales/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review), for the group-sales owner and account owner who hold the relationship with the group.
- [Hospitality](https://fullypowered.ai/industries/hospitality/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review), where hotels sell rooms to groups ahead of time and need to see the pickup before the release date.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review), where several blocks run at once and each needs the same kind of review.
- It is separate from [demand and supply review](https://fullypowered.ai/workflows/demand-and-supply-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review), which compares planned demand with confirmed supply across items and months, and from [renewal risk review](https://fullypowered.ai/workflows/renewal-risk-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review), which looks at contracts coming up for renewal and the warning signs on each account. This one looks at a single block of rooms against its own bookings.

## What has to change for your company

Name your revenue manager, group-sales owner and account owner. Set the column headers of your block export and booking report once, so the headers match each time. Decide which booking statuses in your system mean confirmed, tentative and cancelled, and make sure only those three reach the brief. Agree how the approved agreement summary is written and who approves it, so the dates and the stated minimum come from one place. The brief reads that summary and nothing else from the agreement.

## What has been checked

FullyPowered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026, edited after an independent review, and run again on the edited text. Both runs had seen the example's output first, so neither is independent of the example, and only one input set has been tried: no stop, disputed-terms, missing-summary or passed-date case has been run. The record is published with it. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past block your team already knows, with cases written in advance: a pickup figure that differs from the bookings, tentative rooms, a reservation outside the block, a disputed summary. The revenue manager checks every count against the booking report before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review) describes the record we keep.

- Written by FullyPowered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the workflow template drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related workflow templates

- [Demand and supply review](https://fullypowered.ai/workflows/demand-and-supply-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review)
- [Renewal risk review](https://fullypowered.ai/workflows/renewal-risk-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review)
- [Operations KPI scorecard](https://fullypowered.ai/workflows/operations-kpi-scorecard/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-group-block-pickup-review&from=gh-hospitality-group-block-pickup-review).
