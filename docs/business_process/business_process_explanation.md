Phase I – Business Process Modeling

 Project Title
CyberWatch: Cybersecurity Incident Management System**

Student: Nkwaya Frank  
Student ID: 20251IMA029  
Course:** Database Development with PL/SQL (INSY 8311)  
Instructor: Eric Maniraguha

 1. Business Process Definition

Process Name: Cybersecurity Incident Recording, Classification, Risk Prioritization and Response Tracking Process.

Purpose
The purpose of this process is to help organizations record, organize, classify, prioritize, and monitor cybersecurity incidents using one centralized system.

 Objectives
1. Record historical cybersecurity incidents and new incident information.
2. Classify incidents by attack type, affected country, and sector.
3. Calculate risk scores to identify high-priority incidents.
4. Assign incidents to responsible response officers.
5. Record response actions and update incident status.
6. Generate reports using Power BI.

Problem Addressed
Cybersecurity incident information can come from different sources, making it difficult to organize, classify, prioritize, and monitor incidents. Organizations may also struggle to identify serious incidents and follow up on response activities.

 Expected Outcome
A centralized system that stores cybersecurity incidents, calculates their risk priorities, tracks response activities, and provides useful reports for decision-making.

Importance
This process helps organizations maintain accurate incident records, identify important risks, monitor response progress, and make better cybersecurity decisions.

 2. Actors and Their Responsibilities

| Actor | Responsibility |
|---|---|
| EuRepoC Dataset | Provides historical cybersecurity incident information. |
| Incident Analyst | Imports, checks, and classifies incident information. |
| CyberWatch System | Stores incidents and calculates risk scores. |
| Cybersecurity Team Leader | Reviews priorities and assigns incidents for follow-up. |
| Response Officer | Records response actions and updates incident status. |
| Management | Views Power BI reports and makes decisions. |

 3. Business Process Explanation

The process starts when historical cybersecurity incident information is obtained from the EuRepoC dataset or new incident information is entered by an authorized analyst.

The Incident Analyst checks the information to make sure it is complete and valid. If the information is incorrect or incomplete, it is returned for correction. If it is valid, the CyberWatch System stores the incident in the database.

The analyst then classifies the incident according to its attack type, affected country, and sector. The CyberWatch System calculates a risk score to help identify the priority of each incident.

The Cybersecurity Team Leader reviews the incident classification and risk priority before assigning the incident to a Response Officer. The Response Officer records the actions taken and updates the incident status.

If the response is not complete, the officer continues working on the incident and updates its records. When the response is complete, the incident is marked as closed.

Finally, Management uses Power BI dashboards to view incident statistics, trends, and risk information. These reports support better planning and decision-making.

The process ends when the incident response is completed and the incident record is available for future analysis.

 4. Data-Generating Activities

The CyberWatch system performs database operations to manage cybersecurity incident information.

| Activity | Operation | Information Generated or Used |
|---|---|---|
| Import incident information | CREATE | New incident details |
| Validate incident | READ | Existing incident records |
| Classify incident | UPDATE | Attack type, country, and sector |
| Calculate risk score | READ / CREATE | Risk score and priority level |
| Review incident priority | READ / UPDATE | Approved priority |
| Assign response officer | CREATE / UPDATE | Assignment information |
| Record response activity | CREATE | Action taken, date, and officer |
| Update incident status | UPDATE | Current incident status |
| View reports and dashboard | READ | Incident statistics and trends |
| Archive closed incident | UPDATE | Archived status |

NOTE PLEASE DELETE operation:Deletion is not included in this process because historical cybersecurity incident records should be preserved for future analysis. If a record is incorrect, it should be corrected rather than permanently deleted.

 5. Modeling Tool
c
