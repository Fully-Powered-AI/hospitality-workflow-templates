# Recurring repair service history

When repeated maintenance keeps disturbing guests, the facilities manager gets one brief by equipment and room area: repeated work orders, confirmed service interruptions and missing inspection records side by side. It finds no cause and orders no work.

*Capability template · Hospitality · Operations and process improvement · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/recurring-repair-service-history/)*

## The outcome

The same lift, air-conditioning unit or ice machine keeps appearing in the maintenance log, and guests keep noticing. The facts sit in three places that rarely meet: the work-order log, the notes front desk and housekeeping make when service is disrupted, and the inspection records. This capability puts them on one page, grouped by room area and ranked by how often a piece of equipment has been worked on in the review window.

For each piece of equipment that has been worked on repeatedly, the brief lists the work orders with their dates and who did the work, counts the exact repeats of the same reported issue, sets the confirmed service interruptions beside the work orders they overlap in time, and shows the state of its inspection records: the last one, whether it is past the interval the property set, and whether a check was recorded after each repair was closed. Where the records are silent, the brief says so and turns the gap into a question.

The brief does not say why anything keeps failing. A repeated fault is not a cause, and the page never claims one. It does not advise repair or replacement, order work, certify equipment or return it to service. The facilities manager investigates, and decides with qualified contractors.

## Who starts the work, and when

The facilities manager, or an assistant who prepares for them, starts it when repeated maintenance is disrupting guest service and the question is "what do the records show?" It also suits a regular review before a budget or contractor meeting. Run it again after new work orders, new inspection records or newly confirmed service notes arrive.

## What they supply

- **The asset register.** One row per piece of equipment: an ID, its name, its room area and, if the property has one, the days allowed between inspections.
- **The work orders.** One row per work order: the ID, the equipment ID, when it was opened and closed, the issue as reported, and who did the work.
- **The inspection records (optional).** One row per inspection: the equipment ID, the date and the result as recorded.
- **The service-impact notes (optional).** One row per disruption: the date, the room area, the equipment ID if known, what happened, and who confirmed it.
- **The settings.** The property, the as-of date, the length of the review window, how many work orders make a repeat, how soon after a repair a check should be recorded, and the words that put a record first.

Each file has set column headings. If they do not match, the work stops and asks rather than guessing. The asset register and the work orders are required, and the work stops and asks if either is missing.

## What comes out

One brief in a fixed order. Anything written in a way that suggests injury, entrapment, fire, gas or electric shock comes first, as supplied. Then the equipment worked on repeatedly, by room area, each with its work orders, repeated wording, confirmed interruptions, inspection state and post-repair checks. Then equipment below the repeat level that still has a confirmed interruption. Then service notes that could not be tied to any equipment and records that did not fit. Last, a numbered list of questions for the facilities manager, each with its facts.

A good brief can be checked line by line against the four files in a few minutes, and the facilities manager recognizes every line on it.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), where a repeated failure is a process question before it is a purchase.
- [Health, safety & environment](https://fullypowered.ai/functions/health-safety-and-environment/), where missing inspection records are a question to put to the person responsible.
- [Hospitality](https://fullypowered.ai/industries/hospitality/), where a lift, a cooling unit or a pool pump that keeps failing is a guest experience, not just a log entry.
- [Real estate](https://fullypowered.ai/industries/real-estate/), for managed buildings with shared equipment and tenants who notice every outage.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where the history of a machine lives in a few people's memories.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more rooms and more equipment outgrow what one manager can remember.

The separate [preventive maintenance plan](https://fullypowered.ai/capabilities/preventive-maintenance-plan/) plans equipment care ahead of time. The [repeat incident pattern review](https://fullypowered.ai/capabilities/repeat-incident-pattern-review/) compares safety incidents and their earlier actions. [Contractor safety prequalification](https://fullypowered.ai/capabilities/contractor-safety-prequalification/) concerns who may work on site. This capability reads what has already happened to one property's equipment.

## What has to change for your company

Use your own equipment IDs and room-area names, and use them the same way in all four files, because the brief links records only by ID. Set the window, the number of work orders that counts as a repeat, and the inspection interval for each asset where you have one. Choose how long after a repair a check should be recorded. Edit the list of words that put a record first so it matches how your team writes. Name who confirms service notes, who investigates, and which qualified contractors the manager consults, because the assistant does none of these. It runs in ChatGPT, Claude, Copilot or Gemini from exports you supply, with no connection to your maintenance system.

## What has been checked

Fully Powered AI wrote this capability template from its own published map of the work. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026; the run was not blind (the published brief had been seen), and the record is published with it. It has not been tested in a client environment. It has not been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini. It finds no cause and certifies no equipment.

Testing in your environment means running it on a past quarter the facilities manager remembers well, plus cases written in advance with their expected behavior: a renamed column, a work order for equipment missing from the register, a service note nobody confirmed, a repair closed with no check afterwards. The manager checks every line against the files before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete capability template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the capability drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related capabilities

- [Preventive maintenance plan](https://fullypowered.ai/capabilities/preventive-maintenance-plan/)
- [Repeat incident pattern review](https://fullypowered.ai/capabilities/repeat-incident-pattern-review/)
- [Contractor safety prequalification](https://fullypowered.ai/capabilities/contractor-safety-prequalification/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
