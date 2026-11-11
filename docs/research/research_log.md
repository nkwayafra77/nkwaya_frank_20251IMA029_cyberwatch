
# CyberWatch – Research Log

**Student:** Nkwaya Frank  
**Student ID:** 20251IMA029  
**Project Title:** CyberWatch: Cybersecurity Incident Management System  
**Course:** Database Development with PL/SQL (INSY 8311)  
**Instructor:** Eric Maniraguha  

## 1. Introduction

This research log records sources used to understand cybersecurity incidents, incident classification, risk assessment, existing cybersecurity management systems, available datasets and the database technologies required to develop CyberWatch.

The project will use historical cybersecurity incident data to support incident classification, risk prioritization and response tracking through an Oracle database and an interactive Power BI dashboard.

## 2. Research Sources

### Source 1: Research Paper 1

- **Title:** Cyber security incidents analysis and classification in a case study of Korean enterprises
- **Authors:** Alaa Mohasseb, Benjamin Aziz, Jeyong Jung and Julak Lee
- **Year:** 2020
- **Type:** Peer-reviewed Research Paper
- **APA Reference:** Mohasseb, A., Aziz, B., Jung, J., & Lee, J. (2020). Cyber security incidents analysis and classification in a case study of Korean enterprises. *Knowledge and Information Systems, 62*, 2917–2935. https://doi.org/10.1007/s10115-020-01452-5
- **Link:** https://link.springer.com/article/10.1007/s10115-020-01452-5
- **Key Finding:** The study analyzed cybersecurity incident data collected from five small and medium-sized companies in South Korea. It demonstrated how text analysis and machine learning can help classify incidents and predict possible response actions.
- **Gap Identified:** The study focuses on text classification and predicting response actions. CyberWatch will focus on organizing historical incidents, calculating risk priority scores and recording response activities in an Oracle database.
- **Reading Status:** Abstract and publication details reviewed. Full paper reading to be completed.

### Source 2: Research Paper 2

- **Title:** Cyber incidents risk assessments using feature analysis
- **Authors:** Benjamin Aziz and Alaa Mohasseb
- **Year:** 2023
- **Type:** Peer-reviewed Research Paper
- **APA Reference:** Aziz, B., & Mohasseb, A. (2023). Cyber incidents risk assessments using feature analysis. *SN Computer Science, 5*, Article 7. https://doi.org/10.1007/s42979-023-02199-w
- **Link:** https://doi.org/10.1007/s42979-023-02199-w
- **Key Finding:** The researchers examined how data analysis and machine learning can support cybersecurity risk assessment. They explored predicting malware-related response actions and how incorrect incident classification can create unnecessary response costs.
- **Gap Identified:** The research focuses on machine learning and risk assessment. CyberWatch will implement a database-based approach that combines incident classification, risk prioritization and response tracking.
- **Reading Status:** Abstract and publication details reviewed. Full paper reading to be completed.

### Source 3: Report and Statistics

- **Title:** 2025 Data Breach Investigations Report
- **Organization:** Verizon
- **Year:** 2025
- **Type:** Cybersecurity Report and Statistics
- **APA Reference:** Verizon. (2025). *2025 Data Breach Investigations Report*. https://www.verizon.com/business/resources/reports/
- **Link:** https://www.verizon.com/business/resources/reports/
- **Key Finding:** The report analyzed 22,052 real-world security incidents, including 12,195 confirmed data breaches. The incidents involved organizations in 139 countries.
- **Gap Identified:** The report provides cybersecurity statistics and analysis, but it is not the operational Oracle-based incident management system proposed by CyberWatch.
- **Reading Status:** Official report information and statistics reviewed. Full report reading to be completed.

### Source 4: Existing Cybersecurity System

- **Name:** TheHive
- **Organization:** StrangeBee
- **Type:** Existing Cybersecurity Incident Response and Case Management System
- **APA Reference:** StrangeBee. (n.d.). *TheHive documentation*. https://docs.strangebee.com/
- **Link:** https://docs.strangebee.com/
- **Key Finding:** TheHive supports cybersecurity alert triage, incident investigation, case management, severity updates, response documentation and activity monitoring.
- **Gap Identified:** TheHive is a comprehensive professional platform. CyberWatch will be a smaller academic database project focused on historical incident analysis, risk scoring, response tracking and Power BI reporting.
- **Reading Status:** Official product documentation reviewed. Further documentation reading to be completed.

### Source 5: Dataset

- **Title:** Global Dataset of Cyber Incidents (Version 1.3.2)
- **Authors:** Kerstin Zettl-Schabath, Jakob Bund, Martin Müller, Camille Borrett, Jonas Hemmelskamp, Asaf Alibegovic, Enis Bajra, Alisa Jazxhi, Erik Kellenter, Annika Sachs and Callahan Shelley.
- **Year:** 2025
- **Organization:** European Repository of Cyber Incidents (EuRepoC)
- **Type:** Real-world Cybersecurity Dataset
- **APA Reference:** Zettl-Schabath, K., Bund, J., Müller, M., Borrett, C., Hemmelskamp, J., Alibegovic, A., Bajra, E., Jazxhi, A., Kellenter, E., Sachs, A., & Shelley, C. (2025). *Global Dataset of Cyber Incidents* (Version 1.3.2) [Data set]. European Repository of Cyber Incidents. https://doi.org/10.5281/zenodo.14965395
- **Link:** https://zenodo.org/records/14965395
- **Key Finding:** The dataset contains 3,416 cybersecurity incidents covering the period from 2000 to 2024. It includes 60 variables and provides information suitable for analyzing historical cyber incidents.
- **Gap Identified:** The dataset provides historical incident information but does not provide the complete proposed system for calculating risk priorities and tracking response activities.
- **Recommended File:** eurepoc_global_dataset_1_3.csv
- **Licence Verification:** Pending. The Zenodo record does not currently display a licence value. Permission and educational-use conditions must be confirmed before using the dataset.
- **Reading Status:** Dataset description and metadata reviewed. Dataset handbook and licence conditions still need review.

### Source 6: Technical Documentation

- **Title:** Oracle Database PL/SQL Language Reference (19c)
- **Organization:** Oracle Corporation
- **Year:** 2026
- **Type:** Official Technical Documentation
- **APA Reference:** Oracle. (2026). *Oracle Database PL/SQL Language Reference (19c)*. https://docs.oracle.com/en/database/oracle/oracle-database/19/lnpls/
- **Link:** https://docs.oracle.com/en/database/oracle/oracle-database/19/lnpls/
- **Key Finding:** The documentation explains PL/SQL programming features, including procedures, functions, cursors, packages, triggers and exception handling.
- **Gap Identified:** The documentation explains how to develop database applications but does not provide a ready-made cybersecurity incident management solution. CyberWatch will apply these features to cybersecurity incident management.
- **Reading Status:** Official documentation structure reviewed. Relevant PL/SQL chapters still need detailed reading.

## 3. Research Summary

The reviewed sources demonstrate that cybersecurity incidents can be analyzed using data classification, risk assessment and incident response techniques. Existing systems such as TheHive show the importance of recording, investigating and tracking security incidents.

The EuRepoC dataset is a potential source of real historical cybersecurity incident data. Its educational-use licence must be verified before it is selected as the final dataset.

Oracle PL/SQL provides the database programming features required to build the proposed incident management system, while Power BI will support interactive analysis and reporting.

## 4. Identified Research Gap

Existing research discusses cybersecurity incident classification, risk assessment and response prediction. Existing platforms provide professional incident response and case management features, while public datasets provide historical incident information.

CyberWatch will bring these ideas together in an academic database project by developing an Oracle-based system that records and classifies historical cybersecurity incidents, calculates risk priority scores and tracks response activities. A Power BI dashboard will present incident trends, affected countries, sectors, attack types and risk levels to support decision-making.

## 5. References

1. Aziz, B., & Mohasseb, A. (2023). Cyber incidents risk assessments using feature analysis. *SN Computer Science, 5*, Article 7. https://doi.org/10.1007/s42979-023-02199-w

2. Mohasseb, A., Aziz, B., Jung, J., & Lee, J. (2020). Cyber security incidents analysis and classification in a case study of Korean enterprises. *Knowledge and Information Systems, 62*, 2917–2935. https://doi.org/10.1007/s10115-020-01452-5

3. Oracle. (2026). *Oracle Database PL/SQL Language Reference (19c)*. https://docs.oracle.com/en/database/oracle/oracle-database/19/lnpls/

4. StrangeBee. (n.d.). *TheHive documentation*. https://docs.strangebee.com/

5. Verizon. (2025). *2025 Data Breach Investigations Report*. https://www.verizon.com/business/resources/reports/

6. Zettl-Schabath, K., Bund, J., Müller, M., Borrett, C., Hemmelskamp, J., Alibegovic, A., Bajra, E., Jazxhi, A., Kellenter, E., Sachs, A., & Shelley, C. (2025). *Global Dataset of Cyber Incidents* (Version 1.3.2) [Data set]. European Repository of Cyber Incidents. https://doi.org/10.5281/zenodo.14965395
