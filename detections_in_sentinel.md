---
layout: default
---

[HOME](./index.md)

# Analytic Rules

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

[Incident Monitoring](./siem_projects.md)

## Scheduled

These run within a defined timeframe. 

To configure this rule type head to security.microsoft.com > Sentinel > Configuration > Analytics and click on Create > Scheduled Query Rule. 

Enter a name for the rule, leave the remaining settings as they are and click Next. 

Enter your KQL query here. In this case we’re looking in the AuditLogs table under the OperationName column for a match against “Add user”.

RULE QUERY IMAGE

Leave the remaining settings as they are and click Next and do the same for the rest of the tabs as we don’t need to change anything else right now.

## Scheduled Security Events

To configure this rule type head to security.microsoft.com > Sentinel > Configuration > Analytics and click on Create > Scheduled Query Rule.  

Enter a name for the rule, change the MITRE dropdown to Persistence > Create or modify system process, but leave the remaining settings as they are and click Next. 

Enter your KQL query here. In this case we’re looking in the SecurityEvent table under the EventID column for a match against “4688”.

RULE QUERY IMAGE

Change both the Run query every and Lookup data from the last settings to 5 minutes.

QUERY SCHEDULING IMAGE

Leave the remaining settings as they are and click Next. 

Under Incident Settings enable Alert grouping, leave the remaining settings and clcik Next. 

Click Next through the rest of the tabs.
