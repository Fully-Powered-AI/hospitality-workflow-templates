# Public guest review reply

Answer an online guest review without exposing the guest's stay. Hand over the review and the service actions you have confirmed, and get a short public reply plus separate private notes, each statement tied to its source. The guest relations manager checks and approves.

*Workflow template · Hospitality · Marketing and content · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/public-guest-review-reply/)*

## The outcome

A review goes up on a public site, and the person who answers it has a calm, short draft to work from. The public reply thanks the guest, acknowledges what the review actually says, and states only what the property has verifiably done. Next to it sit private notes for the team: what the review raised that nobody has answered yet, which confirmed actions were kept out of the public reply and why, and what the manager has to decide.

Every sentence in the draft points to its source: a line of the review, a confirmed action, or your own house guidance. Nothing about the stay is added. No dates, rooms, rates or booking details appear unless the review itself put them there, and the name of a staff member, another guest or a child is never repeated, even when the review gives it; it goes in the private notes instead. No refund, credit or upgrade is mentioned or hinted at. The manager decides what is posted, and the draft posts nothing.

## Who starts the work, and when

The guest relations manager starts it when an online review needs a public answer, once per review. The duty manager and the department involved confirm what was done about the problem. The manager reads the draft against the review and the confirmed actions, checks accuracy and the guest's privacy, edits it and approves publication. Marketing sees the final wording if your guidance says so.

## What they supply

- The review as posted: the site, the date, the rating, the name shown and the full text.
- A list of verified service actions, each with who confirmed it, when, and whether it may be mentioned in public.
- Your response guidance: voice, length, sign-off, the contact route to offer, and any words to avoid.
- Who should be told once a reply is posted.

## What comes out

1. **What the review raised.** Every point, numbered, with how the reply handles it.
2. **The public reply.** Short, in your voice, within your length limit.
3. **Where each sentence comes from.** Its source for every sentence in the reply.
4. **Private follow-up notes.** Open points, confirmed actions kept out of public, decisions for the manager and who to tell.
5. **What was left out.** The kinds of detail the draft deliberately did not use.

A good draft can be checked against the review and the action list in a minute, and a reader of the review sees nothing about the stay that they did not write themselves.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Marketing and content](https://fullypowered.ai/functions/marketing-and-content/), because a public reply is also read by people who have not yet booked, and it speaks for the property.
- [Customer support and service](https://fullypowered.ai/functions/customer-support-and-service/), where the guest's own problem is followed up in private.
- [Hospitality](https://fullypowered.ai/industries/hospitality/), for hotels, restaurants and venues that answer reviews on public sites.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), which already have house guidance and want every reply to follow it.

This workflow template stays apart from two neighbours. [Customer reply drafting](https://fullypowered.ai/workflows/customer-reply-drafting/) writes the private message to a guest, where details of the stay belong. [Complaint and refund request handling](https://fullypowered.ai/workflows/complaint-and-refund-request-handling/) applies your policy to a request for money back. This one writes only the public answer and the notes around it.

## What has to change for your company

Write your response guidance down, even on one page: voice, length for each rating, sign-off, and the contact route you offer. Decide which kinds of action may ever be mentioned in public, and who confirms an action before it is listed as verified. Name the person who approves publication and who is told afterwards. Decide how reviews that allege harm, illness, theft, discrimination, a hazard, a hygiene breach or formal action are handled; the template pauses on them and passes them to a person. A review that disputes the facts of a confirmed action does not pause the draft: the reply stays silent on that point and both versions go to the manager in the private notes. Decide which review details the AI assistant may be shown on ChatGPT, Claude, Copilot or Gemini. Your organization keeps control of what is said in its name.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026, and the record is published with it; that trial was not independent, because the assistant had seen the example's reply before drafting. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on past reviews your manager has already answered, plus hard cases written in advance: a review that names a staff member, one that asks for compensation, one that contradicts a confirmed action, one that alleges something serious. The manager checks every sentence against its source before anything is posted. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) shows the record we keep.

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

- [Customer reply drafting](https://fullypowered.ai/workflows/customer-reply-drafting/)
- [Complaint and refund request handling](https://fullypowered.ai/workflows/complaint-and-refund-request-handling/)
- [Copy edit with a change list](https://fullypowered.ai/workflows/copy-edit-with-a-change-list/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
