# Data Dictionary

**Student:** Nkwaya Frank | **ID:** 20251IMA029 | **Course:** INSY 8311 Database Development with PL/SQL | **Project:** CyberWatch

Logical design only: Oracle data types and sizes are added in Phase IV. PK = primary key, FK = foreign key.

## COUNTRY
Lookup of countries (victim, initiator, attributing and responding countries).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| country_id | PK | Surrogate identifier of the country. | Yes | Yes |
| country_name |  | Country name as written in the dataset (e.g. Israel). | Yes | Yes |
| alpha2_code |  | ISO 3166-1 two-letter code (e.g. IL). Missing for some countries. | No | Yes |

## SECTOR_CATEGORY
Lookup of the 12 victim categories (e.g. Critical infrastructure).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| category_id | PK | Surrogate identifier of the category. | Yes | Yes |
| category_name |  | Name of the victim category. | Yes | Yes |

## SECTOR
Lookup of the 34 victim subcategories; each belongs to one category.

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| sector_id | PK | Surrogate identifier of the sector. | Yes | Yes |
| category_id | FK | Category this sector belongs to. | Yes | No |
| subcategory_name |  | Name of the subcategory (e.g. Government / ministries). | Yes | (category_id, subcategory_name) |

## INCIDENT_TYPE
Lookup of attack types (Data theft, Ransomware, Disruption, ...).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| type_id | PK | Surrogate identifier of the attack type. | Yes | Yes |
| type_name |  | Name of the attack type. | Yes | Yes |

## INITIATOR_CATEGORY
Lookup of initiator categories (State, Non-state-group, ...).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| initiator_category_id | PK | Surrogate identifier of the initiator category. | Yes | Yes |
| category_name |  | Name of the initiator category. | Yes | Yes |

## IMPACT_LEVEL
Lookup that turns the impact score (0-15) into a label.

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| impact_score | PK | Impact score from the dataset (0 to 15). | Yes | Yes |
| impact_label |  | Label for the score: Not available, Minor, Low or Medium. | Yes | No |

## MITRE_TECHNIQUE
Lookup of MITRE ATT&CK techniques used in the dataset.

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| technique_id | PK | Surrogate identifier of the technique. | Yes | Yes |
| technique_name |  | Technique name (e.g. Phishing, Data Exfiltration). | Yes | (technique_name, tactic) |
| tactic |  | Initial Access or Impact (which dataset column it came from). | Yes | No |

## INCIDENT
One publicly reported cyber incident (one row of the raw file).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| incident_id | PK | Incident number given by EuRepoC. | Yes | Yes |
| incident_name |  | Short title of the incident. | Yes | No |
| description |  | Free-text description of the incident. | No | No |
| start_date |  | Date the incident started (unknown for 92 incidents). | No | No |
| end_date |  | Date the incident ended. | No | No |
| impact_score | FK | Impact score; links to IMPACT_LEVEL. | No | No |
| unweighted_intensity |  | Intensity score before the target multiplier. | No | No |
| weighted_intensity |  | Intensity score after the target multiplier. | No | No |
| functional_impact |  | How long the victim was functionally affected. | No | No |
| has_disruption |  | Whether the incident caused disruption (Y/N). | No | No |
| data_theft |  | Data-theft category recorded by EuRepoC. | No | No |
| affected_entities_range |  | Range of affected entities (e.g. 1-10). | No | No |
| economic_impact_value |  | Estimated economic impact amount. | No | No |
| economic_impact_currency |  | Currency of the economic impact (euro or dollar). | No | No |
| added_to_db |  | Date EuRepoC added the incident to its database. | No | No |
| updated_at |  | Date EuRepoC last updated the incident. | No | No |
| status |  | CyberWatch workflow status (Open, Assigned, In progress, Closed, Archived). | Yes | No |

## INCIDENT_INCIDENT_TYPE
Junction: an incident can have several attack types, a type applies to many incidents.

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| incident_id | PK,FK | The incident. | Yes | (composite) |
| type_id | PK,FK | The attack type. | Yes | (composite) |

## INCIDENT_RECEIVER
Victim organisations of an incident (one row per victim in the raw list).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| incident_id | PK,FK | The incident. | Yes | (composite) |
| receiver_seq | PK | Position of the victim in the incident's list (1, 2, 3...). | Yes | (composite) |
| receiver_name |  | Name of the victim organisation (may be 'Not available'). | Yes | No |
| country_id | FK | Country of the victim. | No | No |
| sector_id | FK | Sector of the victim. | No | No |

## INCIDENT_SOURCE
Web sources reporting an incident (one row per URL).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| source_id | PK | Surrogate identifier of the source row. | Yes | Yes |
| incident_id | FK | The incident the source reports on. | Yes | No |
| source_url |  | Address of the web page. | Yes | (incident_id, source_url) |
| source_kind |  | INCIDENT (general report) or ATTRIBUTION (evidence of attribution). | Yes | No |

## INCIDENT_MITRE
Junction: MITRE techniques linked to an incident.

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| incident_id | PK,FK | The incident. | Yes | (composite) |
| technique_id | PK,FK | The MITRE technique. | Yes | (composite) |

## ATTRIBUTION
Attribution of an incident to an initiator (at most one per incident).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| attribution_id | PK | Attribution number given by EuRepoC. | Yes | Yes |
| incident_id | FK | The incident being attributed. | Yes | Yes |
| attribution_date |  | Date of the attribution. | No | No |
| attribution_type |  | How the attribution was made (e.g. media report). | No | No |
| attribution_basis |  | Basis of the attribution (e.g. by receiver government). | No | No |
| attributing_actor |  | Role or organisation that made the attribution (personal names removed). | No | No |
| attributing_company |  | Company that made the attribution. | No | No |
| attributing_country_id | FK | Country of the attributing actor. | No | No |

## INITIATOR
Named attackers or groups (848 distinct names in the dataset).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| initiator_id | PK | Surrogate identifier of the initiator. | Yes | Yes |
| initiator_name |  | Name of the group or actor (e.g. Handala, Unknown). | Yes | Yes |

## ATTRIBUTION_INITIATOR
Junction: initiators named in an attribution, with the country and category recorded there.

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| attribution_id | PK,FK | The attribution. | Yes | (composite) |
| initiator_seq | PK | Position of the initiator in the list (1, 2, 3...). | Yes | (composite) |
| initiator_id | FK | The initiator. | Yes | No |
| country_id | FK | Country recorded for the initiator in this attribution. | No | No |
| initiator_category_id | FK | Category recorded for the initiator in this attribution. | No | No |
| is_settled |  | Whether the initiator identification is settled (Y/N). | No | No |

## GOVERNMENT_RESPONSE
Political and legal responses to an incident (from the dataset).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| response_id | PK | Surrogate identifier of the response. | Yes | Yes |
| incident_id | FK | The incident responded to. | Yes | No |
| response_kind |  | POLITICAL or LEGAL. | Yes | No |
| response_date |  | Date of the response. | No | No |
| response_type |  | Type of response. | No | No |
| response_subtype |  | Subtype of response. | No | No |
| responding_country_id | FK | Country that responded. | No | No |
| responding_actor |  | Role or organisation that responded (personal names removed). | No | No |

## RESPONSE_OFFICER
CyberWatch staff who handle incidents (created by CyberWatch; no raw data).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| officer_id | PK | Identifier of the officer. | Yes | Yes |
| officer_name |  | Officer name (anonymised sample data). | Yes | No |
| role |  | Analyst, Team Leader or Response Officer. | Yes | No |

## INCIDENT_ASSIGNMENT
Assignment of an incident to an officer by the team leader (CyberWatch data).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| assignment_id | PK | Identifier of the assignment. | Yes | Yes |
| incident_id | FK | The incident assigned. | Yes | No |
| officer_id | FK | The officer receiving the incident. | Yes | No |
| assigned_by | FK | The team leader who assigned it (an officer). | Yes | No |
| assigned_date |  | Date of the assignment. | Yes | No |

## RESPONSE_LOG
Actions taken by officers on an incident (CyberWatch data).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| log_id | PK | Identifier of the log entry. | Yes | Yes |
| incident_id | FK | The incident worked on. | Yes | No |
| officer_id | FK | The officer who acted. | Yes | No |
| action_taken |  | Description of the action. | Yes | No |
| action_date |  | Date of the action. | Yes | No |

## INCIDENT_PRIORITY
Risk score and priority calculated by CyberWatch (at most one per incident).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| incident_id | PK,FK | The incident scored. | Yes | Yes |
| risk_score |  | Score calculated by the PL/SQL function. | Yes | No |
| priority_level |  | Low, Medium, High or Critical. | Yes | No |
| calculated_at |  | Date the score was calculated. | Yes | No |

## AUDIT_LOG
Record of important changes (filled by triggers in Phase VI).

| Column | Key | Meaning | Required | Unique |
|---|---|---|---|---|
| audit_id | PK | Identifier of the audit entry. | Yes | Yes |
| table_name |  | Table that was changed. | Yes | No |
| record_id |  | Key of the changed row. | Yes | No |
| action |  | INSERT, UPDATE or DELETE. | Yes | No |
| old_value |  | Value before the change. | No | No |
| new_value |  | Value after the change. | No | No |
| changed_by |  | Database user who made the change. | Yes | No |
| changed_at |  | Date and time of the change. | Yes | No |

## Relationships

| Parent (one side) | Child | Parent end | Child end | Meaning |
|---|---|---|---|---|
| COUNTRY | INCIDENT_RECEIVER | 1 | 0..N | victim country |
| COUNTRY | ATTRIBUTION | 1 | 0..N | attributing country |
| COUNTRY | ATTRIBUTION_INITIATOR | 1 | 0..N | initiator country |
| COUNTRY | GOVERNMENT_RESPONSE | 1 | 0..N | responding country |
| SECTOR_CATEGORY | SECTOR | 1 | 1..N | groups |
| SECTOR | INCIDENT_RECEIVER | 1 | 0..N | victim sector |
| IMPACT_LEVEL | INCIDENT | 1 | 0..N | labels |
| INCIDENT | INCIDENT_RECEIVER | 1 | 1..N | has victims |
| INCIDENT | INCIDENT_INCIDENT_TYPE | 1 | 1..N | is of type |
| INCIDENT_TYPE | INCIDENT_INCIDENT_TYPE | 1 | 0..N | applies to |
| INCIDENT | INCIDENT_MITRE | 1 | 0..N | uses technique |
| MITRE_TECHNIQUE | INCIDENT_MITRE | 1 | 0..N | used in |
| INCIDENT | INCIDENT_SOURCE | 1 | 1..N | reported by |
| INCIDENT | ATTRIBUTION | 1 | 0..1 | attributed by |
| ATTRIBUTION | ATTRIBUTION_INITIATOR | 1 | 1..N | names |
| INITIATOR | ATTRIBUTION_INITIATOR | 1 | 0..N | named in |
| INITIATOR_CATEGORY | ATTRIBUTION_INITIATOR | 1 | 0..N | classifies |
| INCIDENT | GOVERNMENT_RESPONSE | 1 | 0..N | triggers |
| INCIDENT | INCIDENT_PRIORITY | 1 | 0..1 | scored as |
| INCIDENT | INCIDENT_ASSIGNMENT | 1 | 0..N | assigned via |
| RESPONSE_OFFICER | INCIDENT_ASSIGNMENT | 1 | 0..N | receives / assigns |
| INCIDENT | RESPONSE_LOG | 1 | 0..N | logged in |
| RESPONSE_OFFICER | RESPONSE_LOG | 1 | 0..N | acts in |

AUDIT_LOG has no foreign keys on purpose: it records changes to any table, so `table_name` and `record_id` identify the row.
