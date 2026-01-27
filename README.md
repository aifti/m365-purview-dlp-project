# Microsoft Purview DLP – Risk-Based Controls (Intern Block vs Employee Justification)

## Overview
This project implements and validates **risk-based Data Loss Prevention (DLP)** controls using Microsoft Purview and Microsoft Entra ID. The goal is to prevent external exfiltration of Personal Identifiable Information (PII) while balancing productivity for trusted users since security shouldn't prevent employees from doing their work.

## Model
- Interns (higher risk): External sharing of SSNs is **blocked**
- Employees (lower risk): External sharing requires **business justification (override)**
- Enforcement includes policy tips, incident reports, and audit visibility in Microsoft 365.

## Environment
- Microsoft 365 tenant (E3 trial)
- Microsoft Purview (DLP policies)
- Microsoft Entra ID groups for identity-scoped targeting
- For Microsoft Defender, may need to upgrade this license to an Microsoft Office 365 E5 license, or simply add on an P1 plan
- Test file: `Payroll.xlsx` containing **valid SSN patterns (XXX-XX-XXXX)** using fake data of course

## Key Policies
1. **Policy 01: Intern External SSN Immediate Block**  
   - Blocks external recipients
   - No override
   - Severity: High (incident reports enabled)

2. **Policy 02: Employee External SSN – Override with Justification**  
   - Blocks external recipients by default
   - Allows override only with **documented business justification**
   - Severity: Medium (incident reports enabled)

## Testing Summary
- Confirmed SSN detection triggers correctly once data format matches standard SSN pattern.
- Confirmed intern policy blocks external email attempts.
- Confirmed employee policy supports override workflow (justification) when configured.
- 

## Notes on Alerting / Defender
DLP enforcement and incident report emails were validated in Purview. Full incident correlation in Microsoft Defender is still a work in progress due to licensing limitations. Will be within (docs/limitations-and-notes.md).

## Skills Demonstrated
Microsoft Purview (DLP), Microsoft Entra ID (group scoping), risk-based policy design, audit evidence collection, testing & validation, governance/exception handling (justification).
