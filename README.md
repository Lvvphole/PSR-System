# PSR-System
# PSR-System: Contractor Top-of-Mind Presence Engine
## Pro Sales Representative — Home Depot District 1
## Northeast Atlanta, Georgia
---
## SYSTEM PURPOSE
This repository contains the complete agentic architecture
for a Contractor Top-of-Mind Presence Engine. The system
is designed to ensure contractors in the PSR portfolio
consistently think of the PSR as their first supplier
contact, eliminating the problem of being forgotten
between projects.
Desired output: Contractors utilizing the PSR as their
first supplier contact consistently and moving toward
a one-stop shop purchasing relationship.
---
## HOW TO USE THIS SYSTEM WITH CLAUDE COWORK
1. Open Claude Cowork on your desktop.
2. Point Claude to this entire PSR-System folder.
3. Tell Claude which agent you need to run.
4. Paste the required input data.
5. Claude reads the relevant skill folder and executes.
Opening instruction to use every time:
"Read the complete folder structure before responding.
I need to run [Agent Name]. Here is my input data:
[paste data]."
---
## FOLDER INDEX
### System_Architecture/
Contains the governing documents for how all agents
work together. Read these to understand the full system.
Claude references these when running multi-agent tasks
or when you ask system-level questions.
00_Architecture_Diagram.md
— Visual map of all agents, triggers, data flows,
  and feedback loops in text format.
01_Workflow_Wiring.md
— Event-driven triggers, timing logic, conditional
  branching, stop conditions, and loop-back rules.
02_Feedback_Optimization_Layer.md
— Weekly and monthly data capture, prompt update rules,
  skill refinement process, and permanent upgrade protocol.
03_Bottleneck_Compression_Plan.md
— Slowest steps identified, automation solutions,
  and backup agent designs.
### Skill_Folders/
Contains one complete skill folder per agent. Each file
includes the primary prompt, fallback prompt, input
schema, output schema, confidence scoring, escalation
rules, logging requirements, and performance metrics.
01_Portfolio_Pulse_Agent.md — Weekly queue generation.
02_Account_Brief_Agent.md — Pre-call intelligence briefs.
03_Message_Drafting_Agent.md — Outreach message variants.
04_Follow_Up_Trigger_Agent.md — No-response follow-up.
05_Note_Capture_Agent.md — Post-call Salesforce notes.
### Contractor_Profiles/
One file per major contractor type in the portfolio.
Contains full project materials lists, common category
gaps, margin pressure points, and outcome priorities.
Updated monthly by PSR.
### Territory_Intelligence/
One file per month. Contains current market conditions
in Northeast Atlanta — active submarkets, material
pricing movements, supply chain signals. Updated first
Monday of each month.
### Message_Library/
Running log of message variants sent, response rates
by variant and contractor type, and promoted default
templates. Updated monthly by System Performance Agent.
### Insight_Library/
Running log of Challenger insights that opened
meaningful conversations. One entry per insight:
insight used, contractor type, outcome.
Updated continuously by PSR after successful calls.
### Accounts/
One file per contractor account. Each file contains a YAML front matter
block with 17 structured fields followed by seven prose sections:
Project Intelligence, Category Intelligence, Relationship Notes,
Open Quotes, Referral Network, Risk Signals, Touchpoint History.
Front matter is machine-parseable for cache regeneration.
Body sections are read by agents directly.
TEMPLATE_account_record.md — blank template for new account onboarding
TEMPLATE_order_history.md — blank order history log for new accounts
### Outreach_Log/
One file per contractor account tracking every outreach attempt.
Front matter holds current FTA status and attempt count.
Body table holds the chronological send log.
TEMPLATE_outreach_log.md — blank template for new account onboarding
### Weekly_Logs/
Performance data logs for each weekly cycle. Used as
input for System Performance Agent monthly review.
---
## WEEKLY OPERATING RHYTHM
FRIDAY 4:00 PM
Run Portfolio Pulse Agent — generate Monday queue.
MONDAY 9:00 AM
Review and approve queue.
Run Account Brief Agent for each approved entry.
Complete Challenger insight slots.
Run Message Drafting Agent.
Execute outreach.
TUESDAY THROUGH THURSDAY
Follow-Up Trigger Agent monitors outreach log.
Note Capture Agent fires after every meaningful call.
FRIDAY 4:30 PM
5-minute system review.
Update files if warranted.
Log weekly performance data.
LAST FRIDAY OF MONTH
System Performance Agent monthly review.
One upgrade implemented before next Monday.
---
## VERSION HISTORY
Date | Change Made | Agent Affected | Reason
--- | --- | --- | ---
[date] | Initial system build | All | System launch