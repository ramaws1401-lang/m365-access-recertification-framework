This project presents a Microsoft 365–native access recertification framework that automates periodic user access reviews using Power Automate, Microsoft Lists, and Power BI.
It enables SMEs to maintain compliance with ISO/IEC 27001 A.9.2.5 and SOX ITGC without the need for complex Identity Governance and Administration (IGA) platforms.

The system provides:

Automated, manager-driven review workflows

Structured, time-stamped evidence of decisions

Campaign-level governance dashboards and KPIs
The solution is composed of four integrated components within Microsoft 365:

User Master (Excel / SharePoint) – Maintains the in-scope user–application–role dataset.

Power Automate Flow – Routes access review requests to respective managers and records outcomes.

Microsoft Lists (AccessReviewTasks) – Captures structured evidence with timestamps, campaign IDs, and reviewer comments.

Power BI Dashboard – Visualizes KPIs such as coverage, on-time completion, revocations, exceptions, and risk-based insights.

Flow Summary: User Master → Power Automate → Microsoft List (AccessReviewTasks) → Power BI Dashboard
Key Features

Automated Review Campaigns: Per-manager dispatch using Power Automate with CampaignID tagging.

Audit-Ready Evidence: Durable, exportable logs of who decided what and when.

Governance Metrics: Real-time KPIs—Coverage %, On-Time %, ApprovaComponent	Technology
Workflow Orchestration	Microsoft Power Automate
Evidence Repository	Microsoft Lists (SharePoint Online)
Governance Analytics	Microsoft Power BI
Data Source	Excel / SharePoint Table
Identity & Access	Microsoft Entra ID (Azure AD)Setup Guide

Prepare the User Master

Create an Excel table or SharePoint list with columns:
UserID, UserName, Email, ManagerEmail, Department, RoleName, RiskScore, CriticalAccess.

Create the Evidence List

In SharePoint, create a list named AccessReviewTasks with columns:
CampaignID, ManagerEmail, UserID, UserName, Department, RoleName, Decision, Comments, Status, TrackingID.

Enable versioning and make Decision a required field.

Build the Power Automate Flow

Load the User Master table.

Group by ManagerEmail and send review emails per manager.

Include CampaignID and TrackingID in each email for traceability.

Develop the Power BI Dashboard

Connect to the Microsoft List.

Create derived columns:

DueVirtual = Created + 14 days

DecisionDateVirtual = Modified (if Decision not blank)

Build visuals for coverage, on-time %, revokes, and risk-based exceptions.s vs Revokes, Past-Due, Exceptions.

Low Overhead: Uses existing M365 licensing—no external servers or custom infrastructure.

Compliance Alignment: Supports ISO/IEC 27001:2022 (A.5.18) and SOX ITGC periodic review expectations.KPI	Description
Coverage %	% of items with completed decisions
On-Time %	% of decisions before SLA date
Revocation Ratio	% of revoked items vs total
Past-Due Items	Pending decisions beyond SLA
Exception Ageing	Exceptions nearing expiry
| Framework          | Control Reference | Description                        |
| ------------------ | ----------------- | ---------------------------------- |
| ISO/IEC 27001:2022 | A.5.18            | Review of user access rights       |
| ISO/IEC 27001:2013 | A.9.2.5           | Periodic review of user access     |
| SOX ITGC           | Section 404       | Evidence of periodic access review |


