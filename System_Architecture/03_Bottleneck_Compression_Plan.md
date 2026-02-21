# Bottleneck Compression Plan

# BOTTLENECK COMPRESSION PLAN
## Slowest Steps, Automation Solutions,
## and Backup Agent Designs
---
## THE SLOWEST STEP IN THE ARCHITECTURE
PSR insight completion between ABA and MDA.
Current state: ABA produces a brief with a blank
Challenger insight slot. MDA cannot fire until PSR
fills it. If PSR is processing inbound quote volume,
this slot sits empty and outreach never executes.
This is the single point of failure in the entire
workflow. Everything before it runs systematically.
Everything after it executes quickly. This one human
dependency — generating a relevant insight under time
pressure — is where the system most commonly stalls.
Root cause: Insight generation requires thinking.
Thinking requires available cognitive bandwidth.
Available cognitive bandwidth is the scarcest resource
in a 99% inbound quote processing role.
---
## AUTOMATION AND REDESIGN TO REDUCE LATENCY
SOLUTION 1: INSIGHT SUGGESTION LAYER
Status: Implement immediately — already built into
  ABA skill folder.
Design: ABA generates three suggested insights from
  territory intelligence and contractor type profile.
  PSR selects one, modifies one, or replaces with
  their own. Selection is faster than generation.
Expected result: Reduces blank slot time from
  minutes to seconds.
SOLUTION 2: INSIGHT LIBRARY QUICK-SELECT
Status: Build at 30-day mark when library has
  sufficient entries.
Design: After 30 days of operation the insight
  library contains proven insights by contractor type
  with response rates. ABA brief includes a
  quick-select panel of three proven insights
  ranked by response rate. PSR selects one.
  MDA fires immediately.
Expected result: Compresses insight bottleneck
  to near zero for established contractor types.
SOLUTION 3: BATCH INSIGHT PREP
Status: Implement as Monday morning habit
  from week one.
Design: Monday morning before queue execution
  PSR spends 10 minutes reviewing territory file
  and pre-loading one insight per contractor type
  into a weekly insight cache note. ABA pulls
  from cache when generating briefs. Insight slot
  pre-filled. MDA fires without PSR re-engagement.
Expected result: Separates insight thinking from
  outreach execution. Both improve when not
  competing for the same cognitive bandwidth.
---
## BACKUP AGENTS AND REDUNDANCY DESIGNS
BACKUP 1: INSIGHT FALLBACK WITHIN MDA
Trigger: Insight slot remains blank after 2 hours.
Action: MDA activates secondary fallback prompt.
  Generates three question-led variants flagged as
  NO INSIGHT PROVIDED.
Purpose: PSR can send a question-led message now
  and upgrade to insight-led on follow-up.
  Prevents outreach paralysis waiting for
  perfect insight.
Rule: A question-led message sent today beats
  a perfect message sent never.
BACKUP 2: ABBREVIATED BRIEF FOR TIER 3 ACCOUNTS
Trigger: ABA input data is thin for Tier 3 accounts.
Action: ABA generates a three-field abbreviated
  brief — last order, contractor type, one suggested
  question. MDA fires on minimal input for
  Tier 3 only.
Purpose: Keeps lower-tier outreach moving without
  consuming Tier 1 brief quality and time.
Rule: Tier 3 abbreviated briefs never delay
  Tier 1 full briefs.
BACKUP 3: PPA MANUAL OVERRIDE
Trigger: Friday data input is incomplete or delayed.
Action: PSR manually inputs simplified account list —
  name, tier, days since contact only. PPA generates
  reduced-confidence queue flagged as PARTIAL DATA.
Purpose: Better than no queue. Outreach continues.
  System flags which accounts need data completion
  before next cycle.
Rule: A partial queue executed beats a perfect queue
  that never ran.
---
## PHASED AUTOMATION ROADMAP
PHASE 1 — NOW — Manual with Claude Cowork
Tools: Claude Pro ($20/month) and Google Sheets (free).
All agents run as Claude conversations using
skill folder files.
Outreach log maintained manually in Google Sheets.
No additional software required.
PHASE 2 — 30 DAYS — Semi-automated with Notion
Tools: Add Notion (free to start).
Migrate skill folders, profiles, and outreach log
into Notion database.
Notion filtered views replace manual Friday
data compilation.
Notion AI runs lighter agent prompts directly
in workspace.
Cost addition: $10/month for Notion AI.
PHASE 3 — 60 DAYS — Triggered notifications
Tools: Add Zapier starter ($20/month).
First automation: when outreach log row shows
no-response and 48-hour threshold crossed,
send PSR phone notification that FTA needs to run.
Second automation: when account inactivity reaches
14 days, send PSR alert that account needs
queue entry.
Cost addition: $20/month.
PHASE 4 — 90 DAYS — Salesforce native alerts
Tools: Home Depot IT configuration of existing
  Salesforce workflow rules.
Cost: No additional cost — uses existing
  Salesforce functionality.
Requires: PSR presents 90-day results to manager
  and requests IT configure workflow rules for
  inactivity alerts and quote aging flags.
Argument: System has produced measurable results
  for 90 days. Salesforce automation removes the
  last manual monitoring step.
TOTAL MONTHLY COST AT FULL PHASE 2 IMPLEMENTATION
Claude Pro: $20
Notion AI: $10
Zapier: $20
Total: $50 per month
Against $30,000 weekly KPI: negligible.
```
---
## SETTING UP THE GITHUB REPOSITORY
Once your local folder is built, push it to GitHub as a backup with these steps.
Go to github.com and create a new repository named exactly `PSR-System`. Set it to private. Do not initialize it with a README because you already have one.
Then in your terminal run these four commands from inside your PSR-System folder:
```
git init
git add .
git commit -m "Initial system build — all agents and architecture"
git remote add origin https://github.com/YOURUSERNAME/PSR-System.git
git push -u origin main
```
After that, every time you update a file — adding an insight to the library, updating the territory intelligence file, refining a prompt after a monthly review — run these two commands to keep GitHub in sync:
```
git add .
git commit -m "Brief description of what you updated"
git push
