# Feedback Optimization Layer

# FEEDBACK OPTIMIZATION LAYER
## Data Capture, Prompt Updates, Skill Refinement,
## and Permanent Upgrade Protocol
---
## DATA CAPTURED WEEKLY
From PSR behavior:
- Accounts contacted vs accounts queued
  — contact rate.
- Which message variants were selected and sent.
- Which outreach generated responses — yes or no.
- Which responses led to conversations, quote
  requests, or no follow-through.
- Brief usefulness ratings — useful or not useful
  per call.
- Notes submitted within 24 hours vs delayed
  or missing.
- Follow-ups sent vs follow-ups queued.
From system behavior:
- All agent confidence scores logged.
- All escalation flags raised and PSR decisions.
- Queue entries modified or removed by PSR —
  indicates PPA calibration gap.
- Fallback prompts activated — indicates input
  quality issue.
- Response rates by agent output type.
---
## HOW PERFORMANCE UPDATES PROMPTS
WEEKLY UPDATE RULE
If any single metric falls below 50% of target
in a given week:
SPA flags immediately in weekly brief.
PSR reviews and provides qualitative note on why.
Temporary prompt adjustment tested next week.
Result logged.
MONTHLY UPDATE RULE
SPA aggregates 30 days of data.
Identifies lowest performing metric.
Proposes specific prompt edit in output.
PSR approves, modifies, or rejects proposed edit.
If approved: edit implemented in skill folder
before next Monday. New baseline established.
PROMPT EDIT PROCESS
1. SPA identifies underperforming agent and metric.
2. SPA proposes specific language change or
   schema field addition.
3. PSR reviews — approve, modify, or reject.
4. If approved: old prompt archived with date
   and reason. New prompt activated.
5. New prompt performance tracked for 30 days.
6. If improved: new prompt confirmed permanent.
   If not improved: revert to archived version,
   try alternative edit.
---
## HOW SKILLS ARE REFINED
CONTRACTOR TYPE PROFILES
Updated when: ABA brief produces a talking point
that lands well and is not yet in the profile,
or produces a category gap flag that turns out
to be incorrect.
Update mechanism: PSR adds or corrects profile
entry after call. NCA output feeds into profile
review monthly.
TERRITORY INTELLIGENCE FILE
Updated: First Monday of each month.
PSR inputs: material categories moving in the
territory, active submarkets, supply chain signals
heard from Pros on the ground.
Claude structures into updated territory file.
Old month file archived — not deleted.
MESSAGE TEMPLATE LIBRARY
Updated: Monthly based on MDA response rate data.
High performers — 30% or higher response rate
over 10 or more sends — promoted to default.
Low performers — under 15% over 10 or more
sends — retired.
One new variant tested per contractor type
per monthly cycle.
INSIGHT LIBRARY
Updated: Any time PSR identifies an insight that
opened a meaningful conversation.
PSR adds one entry: insight used, contractor type,
outcome in one sentence.
Library grows continuously without a fixed cycle.
No entries are ever deleted — only flagged as
active or archived.
---
## WHICH CHANGES BECOME PERMANENT SYSTEM UPGRADES
THREE-REPETITION RULE
Any output that produces a measurable positive
outcome three consecutive times becomes a
permanent default.
Measurable positive outcomes defined as:
- Message variant generates a response.
- Talking point leads to category gap conversation.
- Follow-up angle recovers a stalled contact.
- Brief element rated useful by PSR.
Three repetitions confirms the result is structural
not accidental. One or two successes remain
experimental. Three become permanent.
FIFTY-PERCENT RULE
Any agent output rated not useful more than 50%
of the time over 30 days triggers mandatory
prompt rewrite.
This is not optional and not deferred.
SPA flags it. PSR approves the rewrite.
New prompt activates before next Monday.
PERMANENT STRUCTURE LOG
Every upgrade confirmed as permanent is logged
in the README.md version history table with:
- Date of change.
- Agent affected.
- Metric that triggered the change.
- Old prompt or template archived.
- New prompt or template active.
- Performance before and after.
This log is the institutional memory of the
system's evolution. After 12 months it is
documented proof of compounding system
intelligence.
