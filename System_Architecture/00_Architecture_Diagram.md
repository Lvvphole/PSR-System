# Architecture Diagram
# ARCHITECTURE DIAGRAM
## Contractor Top-of-Mind Presence Engine
---
## SYSTEM OVERVIEW IN ONE SENTENCE
Five specialized agents handle account analysis, brief
generation, message drafting, follow-up triggering, and
note capture — all feeding a continuous feedback loop
that improves weekly and compounds monthly.
---
## DATA SOURCES FEEDING THE SYSTEM
Salesforce CRM
— Account records, order history, contact logs,
  open quote status.
Outreach Log (Google Sheets)
— Send events, response status, variant selected,
  outcome tracked.
Contractor Type Profile Files
— Full materials lists, category gaps, outcome
  priorities by trade type.
Territory Intelligence File
— Monthly market conditions, pricing movements,
  submarket activity.
Message Performance Log
— Response rates by variant, contractor type,
  touchpoint type.
---
## AGENT MAP
PORTFOLIO PULSE AGENT (PPA)
Function: Analyzes portfolio data, produces
  prioritized outreach queue.
Trigger: Friday 4:00 PM scheduled.
  Mid-week 14-day threshold conditional.
Input: Salesforce account data.
Output: Ranked segmented queue.
Sends to: PSR Review Gate → Account Brief Agent.
ACCOUNT BRIEF AGENT (ABA)
Function: Synthesizes account data into pre-call
  intelligence brief with category gaps and
  insight suggestions.
Trigger: Approved queue entry from PSR.
  On-demand for unscheduled calls.
Input: Salesforce notes, contractor profile,
  territory intelligence.
Output: Structured one-page brief.
Sends to: PSR insight completion →
  Message Drafting Agent.
MESSAGE DRAFTING AGENT (MDA)
Function: Generates three channel-specific
  message variants.
Trigger: PSR confirms Challenger insight slot.
Input: Completed brief, insight, touchpoint type,
  relationship tone.
Output: Text variant, email variant,
  call opening script.
Sends to: PSR for selection and send →
  Outreach Log.
FOLLOW-UP TRIGGER AGENT (FTA)
Function: Monitors outreach log and produces
  calibrated follow-up recommendations
  at 48-hour intervals.
Trigger: 48 hours post-send with no response logged.
Input: Outreach log entry, account tier,
  contact attempt count.
Output: Follow-up queue entry or
  PAUSE-AND-REVIEW flag.
Sends to: PSR for review and send.
NOTE CAPTURE AGENT (NCA)
Function: Converts post-call brain dumps into
  structured Salesforce notes.
Trigger: PSR submits brain dump after
  any meaningful call.
Input: Unstructured brain dump, account name,
  call date.
Output: Structured Salesforce-ready note.
Sends to: PSR to paste into Salesforce →
  feeds back to PPA next cycle.
SYSTEM PERFORMANCE AGENT (SPA)
Function: Aggregates performance data and produces
  weekly brief and monthly upgrade recommendation.
Trigger: Friday 4:30 PM weekly.
  Last Friday of month for full review.
Input: All agent logs and performance metrics.
Output: Weekly metric summary.
  Monthly upgrade recommendation with proposed
  prompt edit.
Sends to: PSR for review and upgrade approval.
---
## FULL WORKFLOW DIAGRAM
FRIDAY 4:00 PM
└── PPA fires
    └── Input: Salesforce account data
    └── Output: Ranked outreach queue
    └── Routes to: PSR Review Gate
MONDAY 9:00 AM — PSR REVIEW GATE
└── PSR approves / modifies / removes queue entries
    └── Approved entries route to ABA one per account
MONDAY — ABA FIRES PER APPROVED ENTRY
└── Input: Salesforce notes + profiles + territory file
    └── Output: Brief with 3 insight suggestions
    └── Routes to: PSR insight completion
MONDAY — PSR INSIGHT COMPLETION
└── PSR selects or replaces insight suggestion
    └── Confirmed insight routes to MDA
MONDAY — MDA FIRES
└── Input: Brief + confirmed insight + touchpoint type
    └── Output: Text / Email / Call script variants
    └── Routes to: PSR for selection and send
MONDAY — PSR SENDS
└── Selects variant
    └── Personalizes if needed
    └── Sends via chosen channel
    └── Logs send in Google Sheets outreach log
TUESDAY THROUGH THURSDAY — FTA MONITORS
└── 48 hours no response detected
    └── Attempt 1: FTA generates follow-up
        └── PSR reviews and sends
    └── Attempt 2: FTA generates follow-up
        └── PSR reviews and sends
    └── Attempt 2 no response: PAUSE-AND-REVIEW
        └── 14-day cooling period begins
        └── PPA flags account as STALLED
AFTER EVERY MEANINGFUL CALL — NCA FIRES
└── PSR submits brain dump
    └── NCA produces structured note
    └── PSR pastes into Salesforce
    └── Richer note feeds PPA next Friday
FRIDAY 4:30 PM — SPA FIRES
└── Weekly: metric summary, anomaly flags
    └── Monthly: upgrade recommendation +
        proposed prompt edit
    └── PSR 5-minute review
    └── File updates if warranted
    └── Monthly upgrade implemented before next Monday
---
## CONFIDENCE AND ESCALATION ROUTING
0.8 or above — Agent proceeds autonomously.
0.6 to 0.79 — Proceeds with DATA GAP flags.
  PSR review recommended.
0.4 to 0.59 — Fallback prompt activates.
  PSR review required before send.
Below 0.4 — Full escalation. Output withheld.
  Human decides.
---
## STOP CONDITIONS
Contact attempt 2 with no response —
  PAUSE 14 days.
PSR flags DO-NOT-CONTACT —
  all agents halt for that account.
Response received —
  FTA stops, NCA activates.
Account closed in Salesforce —
  full system halt for that account.
Confidence below 0.4 with no fallback —
  escalate, halt.
---
## FEEDBACK LOOPS
NCA to PPA: Richer notes improve queue accuracy.
  Continuous.
MDA to Message Library: Response rates update
  templates. Monthly.
ABA to Contractor Profiles: Usefulness ratings
  update profiles. Monthly.
FTA to Angle Library: Recovery rates update
  follow-up angles. Monthly.
SPA to all Skill Folders: Performance data drives
  prompt edits. Monthly.
PSR file updates to all agents:
  Territory and profile updates. Weekly.
