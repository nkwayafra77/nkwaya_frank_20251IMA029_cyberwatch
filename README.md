
# CyberWatch: Cyber Incident Classification, Risk Prioritization and Response Tracking System

## 1. Student Information

- **Student Name:** Nkwaya Frank
- **Student ID:** 20251IMA029
- **Institution:** Adventist University of Central Africa (AUCA)
- **Course:** Database Development with PL/SQL
- **Academic Year:** 2026–2027

## 2. Problem Statement

Cybersecurity incidents such as phishing, ransomware and data breaches affect organizations and important services around the world. However, organizing incident information, understanding the types of attacks, assessing their severity and tracking response activities can be challenging without a structured database system.

CyberWatch aims to address this problem by providing a centralized system for recording, classifying, analyzing and prioritizing publicly reported cybersecurity incidents.

## 3. Project Objectives

The main objectives of CyberWatch are:

1. To store and organize publicly reported cybersecurity incidents in an Oracle database.
2. To classify incidents according to attack type, affected country and sector.
3. To calculate incident priority scores using predefined risk assessment rules.
4. To record and monitor incident response activities.
5. To maintain audit records of important changes made to incident information.
6. To provide interactive reports and visualizations to support cybersecurity analysis.

## 4. Data Source

**Proposed Dataset:** EuRepoC Global Dataset of Cyber Incidents.

**Dataset Link:** https://zenodo.org/records/14965395

The dataset contains publicly reported cybersecurity incidents from different countries and sectors. It will provide the historical records needed to develop and test the CyberWatch database.

**Note:** The dataset licence and educational-use permissions must be confirmed before final use.

## 5. Planned Database Tables

The following tables are proposed for the system:

- **INCIDENT:** Stores cybersecurity incident information.
- **COUNTRY:** Stores information about affected countries.
- **SECTOR:** Stores information about affected economic and organizational sectors.
- **ATTACK_TYPE:** Stores categories of cyberattacks.
- **INCIDENT_ATTACK_TYPE:** Connects incidents with their attack types.
- **INCIDENT_SECTOR:** Connects incidents with affected sectors.
- **SOURCE:** Stores information about incident information sources.
- **RESPONSE_LOG:** Records actions and response activities.
- **AUDIT_LOG:** Records important changes made to the system.

The final database structure will be refined during the database design phase.

## 6. Planned PL/SQL Features

CyberWatch will implement the following Oracle PL/SQL features:

- **Stored Procedures:** To register, update and manage cybersecurity incidents.
- **Functions:** To calculate incident risk and priority scores.
- **Cursors:** To generate reports about incidents by country, attack type and severity.
- **Packages:** To organize related database procedures and functions.
- **Triggers:** To automatically record important changes in the audit log.
- **Exception Handling:** To manage invalid inputs and database errors.

## 7. Planned Innovation

The project will include an interactive Power BI dashboard connected to the Oracle database.

The dashboard will display:

- Total number of cybersecurity incidents.
- Incidents by attack type.
- Incidents by country and affected sector.
- Incident severity and priority levels.
- Response activities and their statuses.

This will help users understand incident trends and identify which recorded incidents require greater attention.

**Project Scope:** CyberWatch will initially analyze historical publicly reported incidents. It is not intended to detect or prevent live cyberattacks automatically.

## 8. Technologies

- Oracle Database
- Oracle PL/SQL
- Microsoft Power BI
- GitHub

## 9. References

1. European Repository of Cyber Incidents (EuRepoC). (2025). *Global Dataset of Cyber Incidents*. Zenodo. https://doi.org/10.5281/zenodo.14965395

2. European Repository of Cyber Incidents (EuRepoC). *EuRepoC Database*. https://eurepoc.eu/database/
