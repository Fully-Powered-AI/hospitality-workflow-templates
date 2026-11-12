# Service roster options

For a department manager building a rota for expected occupancy, covers or events: two or three roster options side by side, with each role's need, the staff confirmed available, the periods left uncovered and the labor-cost assumptions you supplied. You verify and approve; nothing is published.

*Workflow template · Hospitality · People and HR · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/service-roster-options/)*

## The outcome

Before the week is committed, the manager sees the choices on one page. For every service period, the page shows how many people each role needs for the demand you expect, how many are confirmed available, how many are only pending, and how many places stay empty. Each option then shows what it would cost at the rates and on-costs you supplied, so a gap and its price can be weighed against each other.

The unknowns stay visible. A person whose availability nobody has recorded is counted as unknown, never as free. A supplied rule that an option would strain is flagged next to that option. Your department still decides: which option, who works which shift, and what goes to HR.

## Who starts the work, and when

The department manager starts it when the forecast for the coming service differs from the standing rota: a busy weekend, a large event order, a quiet week. It runs again when availability changes or an event order moves. The manager verifies the figures and the constraints, and approves the chosen roster with HR where the property's process requires it.

## What they supply

- The service window and the periods in it, with how long each period's shift is.
- The expected demand for each period: rooms occupied, covers or event guests, from your forecasts and event orders.
- The staffing rules you approved: how many guests or covers one person handles, and the minimum per role.
- Staff availability, by reference code rather than name, with each cell marked confirmed, pending or unavailable. A blank cell is treated as unknown.
- Hourly rates, the on-cost percentage and any rules you want checked, such as a cap on shifts per person.

## What comes out

One page in a fixed order. The supplied assumptions, then each role's need by period, then the availability counts. Then two or three roster options, each with the staffed number, the uncovered number and the spare number for every role and period, its pending staff, any rule flag and its cost. A comparison line for each option follows, then the questions only the manager can settle.

The options work in headcounts. They do not name who works, and they do not rank or compare individuals. The page contains no schedule to publish and nothing to send.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [People and HR](https://fullypowered.ai/functions/people-and-hr/), which owns the approval of the roster and the rules it is checked against.
- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), where the day's service is made to work with the people available.
- [Hospitality](https://fullypowered.ai/industries/hospitality/), where occupancy, covers and events move the need from one day to the next.
- [Ecommerce and retail](https://fullypowered.ai/industries/ecommerce-and-retail/), where shop-floor and fulfilment cover follows promotions and peak days.
- [Media and entertainment](https://fullypowered.ai/industries/media-and-entertainment/), where venues and productions staff to an event's size.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where a rota has run the same way for years and a busy week exposes its gaps.

## What has to change for your company

Decide the periods and their lengths. Set your own staffing ratios and minimums, and decide which measures drive each role. Name the rules you want checked and the ones you check by hand. Decide whether the on-cost percentage applies to every role. Keep staff as reference codes in what you paste, and agree when HR sees an option. It stays a different piece of work from the [headcount plan](https://fullypowered.ai/workflows/headcount-plan/), which plans roles for a year, and from [payroll preparation and timesheet review](https://fullypowered.ai/workflows/payroll-preparation-and-timesheet-review/), which handles hours already worked. For events with their own run of show, the [event plan](https://fullypowered.ai/workflows/event-plan/) comes first. It runs in ChatGPT, Claude, Copilot or Gemini from the files you supply, with no connection to your scheduling or payroll system.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example on 10 November 2026 in Claude; the record is published with it. The template was clarified in small ways afterward, and those clarifications have not been run again. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

The template judges no working-time or employment-law limit. It applies only the rules you supply, as arithmetic, and says nothing about whether those rules are enough. Testing in your environment means running it on a past week your manager already knows, plus hard cases written in advance: a blank availability cell, a renamed column, a rule the options strain, a request to say who should work. The manager checks every figure before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

- Written by Fully Powered AI.
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

- [Headcount plan](https://fullypowered.ai/workflows/headcount-plan/)
- [Payroll preparation and timesheet review](https://fullypowered.ai/workflows/payroll-preparation-and-timesheet-review/)
- [Event plan](https://fullypowered.ai/workflows/event-plan/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
