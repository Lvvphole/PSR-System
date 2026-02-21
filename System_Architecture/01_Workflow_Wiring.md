# Workflow Wiring

# WORKFLOW WIRING
## Event-Driven Triggers, Timing, Branching,
## Stop Conditions, and Feedback Loops
---
## EVENT-DRIVEN TRIGGER MAP
TRIGGER 1: SCHEDULED WEEKLY QUEUE
Event: Friday 4:00 PM.
Agent: PPA fires.
Condition: None — fires regardless of data completeness.
Routes to: PSR Review Gate.
TRIGGER 2: MID-WEEK INACTIVITY FLAG
Event: Any account crosses 14-day no-contact threshold.
Agent: PPA fires for that account only.
Condition: Tier 1 or Tier 2 accounts only.
Routes to: PSR Review Gate as single entry.
TRIGGER 3: PSR REVIEW GATE
Event: PPA output received.
Agent: Human checkpoint.
Condition: PSR approves, modifies, or removes entries.
Routes to: ABA one trigger per approved entry.
Timing: PSR completes review by Monday 9:00 AM.
TRIGGER 4: ACCOUNT BRIEF REQUEST
Event: Approved queue entry received from PSR gate.
  OR PSR manually requests brief before
  unscheduled call.
Agent: ABA fires.
Condition: Account data present in Salesforce.
Routes to: PSR for insight slot completion.
Timing: Immediate upon trigger.
TRIGGER 5: INSIGHT CONFIRMATION
Event: PSR selects or replaces insight suggestion
  in brief.
Agent: MDA fires.
Condition: Insight field confirmed — not blank.
Routes to: PSR for variant selection and send.
Timing: Immediate upon PSR confirmation.
TRIGGER 6: OUTREACH LOGGED
Event: PSR confirms message sent and logs in
  Google Sheets.
Agent: Outreach log entry created. FTA timer starts.
Condition: Send confirmed by PSR.
Timing: Immediate.
TRIGGER 7: 48-HOUR NO RESPONSE
Event: 48 hours elapsed since outreach logged.
  No response recorded.
Agent: FTA fires.
Condition: Response status equals no-response.
Routes to: PSR for follow-up review and send.
Timing: Exactly 48 hours post-send.
TRIGGER 8: RESPONSE RECEIVED
Event: PSR logs response received in outreach log.
Agent: FTA deactivates for that thread.
Condition: Response status updated to responded.
Routes to: NCA if call resulted from response.
Timing: Immediate upon PSR log update.
TRIGGER 9: POST-CALL BRAIN DUMP
Event: PSR submits brain dump after meaningful call.
Agent: NCA fires.
Condition: Brain dump text present and account
  name provided.
Routes to: PSR to paste structured note
  into Salesforce.
Timing: Immediate upon submission.
TRIGGER 10: WEEKLY SYSTEM REVIEW
Event: Friday 4:30 PM.
Agent: SPA fires — weekly brief.
Condition: Minimum 3 days of performance data present.
Routes to: PSR 5-minute review.
Timing: Available by Friday 5:00 PM.
TRIGGER 11: MONTHLY SYSTEM REVIEW
Event: Last Friday of month at 4:30 PM.
Agent: SPA fires — monthly brief with upgrade
  recommendation.
Condition: Minimum 25 days of performance data.
Routes to: PSR upgrade decision then skill folder
  update if approved.
Timing: Available by Friday 5:30 PM.
---
## TIMING LOGIC
MONDAY
PSR reviews and approves Friday queue by 9:00 AM.
ABA fires for each approved entry.
MDA fires after PSR completes insight slots.
Outreach executed by PSR — target before noon.
TUESDAY THROUGH THURSDAY
FTA monitors outreach log continuously.
NCA fires on-demand after each meaningful call.
ABA fires on-demand for unscheduled proactive calls.
MDA fires on-demand for ad-hoc outreach needs.
FRIDAY
PPA fires at 4:00 PM — generates next week queue.
SPA fires at 4:30 PM — generates performance brief.
PSR 5-minute review at 5:00 PM.
File updates if warranted at 5:15 PM.
Monthly SPA fires on last Friday of month.
---
## CONDITIONAL BRANCHING LOGIC
BRANCH 1: ACCOUNT TIER ROUTING
Tier 1:
  ABA generates full brief.
  MDA generates all three variants.
  FTA escalates immediately after attempt 1
    on quotes over $5,000.
Tier 2:
  ABA generates full brief.
  MDA generates two variants — text and call script.
  FTA fires at 48 hours standard.
Tier 3:
  ABA generates abbreviated brief.
  MDA generates one variant — PSR selects channel.
  FTA fires at 72 hours.
BRANCH 2: TOUCHPOINT TYPE ROUTING
Check-in: MDA uses check-in template library.
Reengagement: MDA uses reengagement template library.
  ABA flags last purchase date prominently.
Quote-followup: MDA uses quote-followup template.
  Includes quote context in all variants.
Referral-trigger: MDA uses referral template.
  Fires only after PSR confirms a positive outcome.
BRANCH 3: CONFIDENCE SCORE ROUTING
0.8 or above: Agent proceeds autonomously.
0.6 to 0.79: Agent proceeds with DATA GAP flags.
  PSR review recommended.
0.4 to 0.59: Fallback prompt activates.
  PSR review required before send.
Below 0.4: Escalate to human.
  Agent output withheld.
BRANCH 4: RESPONSE STATUS ROUTING
Response received:
  FTA deactivates for thread.
  NCA triggered if call resulted.
  PPA updates account status for next cycle.
No response at 48 hours:
  FTA fires attempt 2.
No response after attempt 2:
  FTA triggers PAUSE-AND-REVIEW.
  PPA flags account as STALLED.
  SPA logs pattern for monthly analysis.
---
## STOP CONDITIONS
STOP 1: Contact attempt count reaches 2 with
  no response.
  FTA halts. PAUSE-AND-REVIEW routes to PSR.
  Account enters 14-day cooling period before
  re-entry to queue.
STOP 2: PSR manually flags account as
  DO-NOT-CONTACT.
  All agents halt for that account.
  Account removed from queue until flag lifted.
STOP 3: Response received and call scheduled.
  FTA deactivates.
  MDA deactivates for that thread.
  NCA activates post-call.
STOP 4: Account marked CLOSED or INACTIVE
  in Salesforce.
  All agents halt.
  Account removed from PPA input data.
STOP 5: Agent confidence score below 0.4
  with no fallback output possible.
  Full halt.
  Escalation to PSR with explicit data gap
  description.
---
## LOOP-BACK FEEDBACK CONDITIONS
LOOP 1: NCA to PPA
Note submitted to Salesforce triggers richer data
on next Friday cycle. PPA queue accuracy improves.
Frequency: Continuous.
LOOP 2: MDA response rate to MDA template library
Monthly response rate data by variant and contractor
type routes to SPA. High performers promoted to
default. Low performers retired.
Frequency: Monthly.
LOOP 3: ABA usefulness rating to contractor profiles
PSR usefulness ratings and talking point usage route
to SPA. Profile fields producing useful briefs
identified and weighted. Contractor profiles updated.
Frequency: Monthly.
LOOP 4: FTA recovery rate to FTA angle library
Follow-up response rates by angle and channel route
to SPA. Highest recovery combinations identified.
FTA angle library updated.
Frequency: Monthly.
LOOP 5: Full system weekly cadence discipline
PSR Friday review triggers file updates. PPA fires
on refreshed data. Monday queue improves. Outreach
quality increases. Response rates increase.
Next Friday review data is more useful.
Frequency: Weekly.
