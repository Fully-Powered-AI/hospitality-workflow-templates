# Room turn priority list

Get one morning worklist of rooms to turn in your own priority order, with conflicts written as questions. The supervisor verifies and assigns.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See Room turn priority list on our website](https://fullypowered.ai/workflows/room-turn-priority-list/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the sample ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Hospitality · Operations and process improvement · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/room-turn-priority-list/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list)*

## The outcome

The day's housekeeping plan starts from one page instead of three lists and a handful of remembered conversations. Every room that has a departure or an arrival appears once, in the order your own priority rules give; a supervisor note about any other room is listed apart, as a question. Beside each room sits what the records say about it: whether the guest has left, whether the room is being turned, whether it is waiting for inspection, and when the arriving guest is expected.

The page then does the part that is easy to miss at a busy hour. It marks the rooms awaiting inspection so they are not forgotten. It puts any disagreement between the lists and the notes next to the room, as a question: a departure shown as expected while a note says the room is being cleaned, a departure with no time, a note several hours old, a room on a maintenance hold with a guest due. It adds up the turn minutes still needed against the minutes the team has left, and says plainly when the two do not match.

The page never says a room is ready. The supervisor verifies each room's status and decides who does what. The AI assistant inspects nothing, certifies no room clean, assigns nobody, contacts nobody and changes nothing in the property system.

## Who starts the work, and when

The housekeeping supervisor, or an assistant manager who plans the day for them, runs it once the morning's departure and arrival lists are available. Run it again whenever the picture moves: a block of departures is confirmed, a maintenance hold is released, a room is inspected, or the supervisor has walked the floor and updated the notes. The supervisor reads it, settles the questions and assigns the work.

## What they supply

- **The departure list** from your hotel reservation system. One row per room: the room, its type, whether the guest has departed, is expected to depart or is not known, and the time.
- **The arrival list.** One row per arriving room: the room, its type, the expected arrival time and a flag from your own set of codes, such as a confirmed early arrival or a group block.
- **The supervisor's room-status notes.** One row per note: the room, a status in a short fixed set of words, a free note and the time it was written.
- **The priority rules.** Your own, in order, each one a simple test on the arrival time, the flag, the room type or the status.
- **The settings.** The property, the day and the time of the run, how old a note may be, the minutes a turn takes for each room type, and how many people have how many minutes left.

Each file comes with set column headings. If a heading does not match, the work stops and asks rather than guessing.

## What comes out

One page in a fixed order. A header with the dates, sources and counts. The worklist in priority order, each room with its recorded state, its arrival and any flag. Rooms on a maintenance hold in their own section. A load check of minutes needed against minutes available. A short list for the front desk and for maintenance. A numbered list of questions for the supervisor, each with its facts. Any note about a room that is on neither list.

A good page can be checked against the three lists in ten minutes, and the supervisor recognizes every line on it.

See the worked example in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list), where the daily plan is a repeated process that should run the same way each morning.
- [Hospitality](https://fullypowered.ai/industries/hospitality/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list), where the order rooms come back decides whether guests wait at the desk.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list), where the priority rules live in one supervisor's head and belong on a page.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list), when more rooms and more shifts turn over than one person can follow.

The sibling for a rented unit between tenants is [unit turnover readiness checklist](https://fullypowered.ai/workflows/unit-turnover-readiness-checklist/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list). [Emergency drill brief](https://fullypowered.ai/workflows/emergency-drill-brief/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list) is separate work, and [preventive maintenance plan](https://fullypowered.ai/workflows/preventive-maintenance-plan/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list) covers equipment through the year.

## What has to change for your company

Start from your own priority rules and write them in the plain form the template reads: a test on arrival time, on a flag, on a room type or on a status, in the order you apply them. Agree the flag codes your front desk uses. Choose the status words your supervisors write, or accept the five in the template. Set your turn minutes for each room type and how old a note may be before it is questioned. Name who inspects, who assigns and who tells the front desk about a hold, because the assistant does none of these. It runs in ChatGPT, Claude, Copilot or Gemini from files you supply, with no connection to your property system.

## What has been checked

FullyPowered AI wrote this workflow template from its own published map of the work. It was editorially reviewed on 10 November 2026. It was tried on its example in Claude on 10 November 2026; the record is published with it. Small wording edits made to the instructions and output format after that trial have not been run again. It has not yet been tested in a client environment. It has not been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini. It certifies nothing about the state of a room.

Testing in your environment means running it on two or three past mornings your supervisor remembers well, plus hard cases written in advance, each with its expected behavior: a renamed column, a departure marked expected while a note says cleaning, a note that is too old, a room on hold with an arrival, a rule the template cannot read. The supervisor checks every line against the lists before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list) describes the record we keep.

- Written by FullyPowered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example.
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

- [Unit turnover readiness checklist](https://fullypowered.ai/workflows/unit-turnover-readiness-checklist/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list)
- [Emergency drill brief](https://fullypowered.ai/workflows/emergency-drill-brief/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list)
- [Preventive maintenance plan](https://fullypowered.ai/workflows/preventive-maintenance-plan/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hospitality-room-turn-priority-list&from=gh-hospitality-room-turn-priority-list).
