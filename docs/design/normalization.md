# Normalization: UNF → 1NF → 2NF → 3NF

**Student:** Nkwaya Frank | **ID:** 20251IMA029 | **Course:** INSY 8311 Database Development with PL/SQL | **Project:** CyberWatch


All rows below are real rows of `eurepoc_global_dataset_1_3.csv`. Three incidents are used: **4163** (one value everywhere), **4025** (two victims and two attack types) and **3954** (two victims and 3 initiators).

## 1. UNF (the raw file)

One incident is one row, and several columns hold lists separated by `;`.

| incident_id | start_date | incident_type | receiver_name | receiver_country | initiator_name | impact score | impact label | mitre_impact |
|---|---|---|---|---|---|---|---|---|
| 4163 | 19.12.2024 | Disruption;Hijacking with Misuse | Ministry of Justice (Ukraine) | Ukraine | Unknown | 8 | Low | Data Destruction |
| 4025 | 05.11.2024 | Data theft & Doxing;Hijacking with … | Soreq Nuclear Research Center… | Israel;Israel | Handala | 7 | Low | Data Exfiltration |
| 3954 | 06.10.2024 | Data theft & Doxing | Not available;Cisco | Not available;United … | IntelBroker;EnergyWeapo… | 9 | Low | Data Exfiltration |

**Problem:** `incident_type`, `receiver_*` and `initiator_*` are repeating groups (several values in one cell).

## 2. 1NF: remove the repeating groups

Every cell now holds one value. The three lists are independent (the number of attack types has nothing to do with the number of victims), so each list gets its own relation instead of one table that multiplies them together.

**INCIDENT_TYPE_LIST** (key: incident_id, incident_type)
| incident_id | incident_type |
|---|---|
| 4025 | Data theft & Doxing |
| 4025 | Hijacking with Misuse |
| 3954 | Data theft & Doxing |

**RECEIVER_LIST** (key: incident_id, receiver_seq)
| incident_id | receiver_seq | receiver_name | receiver_country | alpha2 | receiver_category | receiver_subcategory |
|---|---|---|---|---|---|---|
| 4025 | 1 | Soreq Nuclear Research Cent… | Israel | IL | Critical infrastructure | Research |
| 4025 | 2 | Not available | Israel | IL | Critical infrastructure | Research |
| 3954 | 1 | Not available | Not available | #N/A | Unknown | Not available |
| 3954 | 2 | Cisco | United States | US | Critical infrastructure | Critical Manufacturing |

**INITIATOR_LIST** (key: incident_id, initiator_seq)
| incident_id | initiator_seq | initiator_name | initiator_country | initiator_category | attribution_id | attribution_date |
|---|---|---|---|---|---|---|
| 3954 | 1 | IntelBroker | Unknown | Unknown | 25189 | 14.10.2024 |
| 3954 | 2 | EnergyWeaponUser | Unknown | Unknown | 25189 | 14.10.2024 |
| 3954 | 3 | zjj | Unknown | Unknown | 25189 | 14.10.2024 |

**Dependency removed:** repeating group (a cell holding a list).

## 3. 2NF: remove partial dependencies

In RECEIVER_LIST and INITIATOR_LIST the key has two parts. Some columns depend on only one part, `incident_id` (or `attribution_id`), so they are copied on every row. Example with incident 4025 if the incident columns were kept in the list table:

| incident_id | receiver_seq | start_date | impact_score | receiver_name |
|---|---|---|---|---|
| 4025 | 1 | 05.11.2024 | 7 | Soreq Nuclear Research Center |
| 4025 | 2 | 05.11.2024 | 7 | Not available |

- `start_date` and `impact_score` depend only on `incident_id`, so they move to **INCIDENT**. `receiver_name` depends on the whole key and stays in **INCIDENT_RECEIVER**.
- In INITIATOR_LIST, `attribution_id` and `attribution_date` repeat for every initiator of incident 3954 (25189 on 3 rows). They depend on the attribution, not on the initiator's position, so they move to **ATTRIBUTION**. The initiator rows become **ATTRIBUTION_INITIATOR** (key: attribution_id, initiator_seq).
- The list of attack types becomes the junction **INCIDENT_INCIDENT_TYPE**; the lists of MITRE techniques and source URLs become **INCIDENT_MITRE** and **INCIDENT_SOURCE** in the same way.

**Dependency removed:** partial dependency on part of a composite key.

## 4. 3NF: remove transitive dependencies

A transitive dependency is a non-key column that depends on another non-key column. Each one below was checked in the data.

| Column that depends on a non-key column | Depends on | Checked in the data | New table |
|---|---|---|---|
| `alpha2` | `receiver_country` | no country has two codes (checked on single-victim rows) | COUNTRY |
| `receiver_category` | `receiver_subcategory` | holds for 33 of 34 subcategories (the exception is the placeholder 'Not available') | SECTOR_CATEGORY, SECTOR |
| `impact_indicator_label` | `impact_indicator_score` | one label per score | IMPACT_LEVEL |

| COUNTRY: country_id | country_name | alpha2_code |
|---|---|---|
| 1 | Israel | IL |
| 2 | Not available | #N/A |
| 3 | United States | US |

| SECTOR: sector_id | category | subcategory_name |
|---|---|---|
| 1 | Critical infrastructure | Critical Manufacturing |
| 2 | Critical infrastructure | Research |
| 3 | Unknown | Not available |

| IMPACT_LEVEL: impact_score | impact_label |
|---|---|
| 0 | Not available |
| 1 | Minor |
| 2 | Minor |
| 3 | Minor |
| 4 | Minor |
| 5 | Minor |

**Note:** the `Not available` and `#N/A` rows above are placeholders from the raw file. Phase IV cleaning turns them into NULL, so they will not become rows in COUNTRY or SECTOR.

**Not forced into a table:** an initiator's country and category are not fixed by its name (107 of 844 named initiators appear with more than one pair), so they stay in ATTRIBUTION_INITIATOR as recorded for that attribution. This is a correct 3NF decision, not a shortcut.

**Dependency removed:** transitive dependency.

## 5. Result: 21 tables

Lookups: COUNTRY, SECTOR_CATEGORY, SECTOR, INCIDENT_TYPE, INITIATOR_CATEGORY, IMPACT_LEVEL, MITRE_TECHNIQUE.
From the dataset: INCIDENT, INCIDENT_INCIDENT_TYPE, INCIDENT_RECEIVER, INCIDENT_SOURCE, INCIDENT_MITRE, ATTRIBUTION, INITIATOR, ATTRIBUTION_INITIATOR, GOVERNMENT_RESPONSE.
Created by CyberWatch (no raw data): RESPONSE_OFFICER, INCIDENT_ASSIGNMENT, RESPONSE_LOG, INCIDENT_PRIORITY, AUDIT_LOG.

Political and legal responses have identical columns, so one table with `response_kind` replaces two.

## 6. Map of every raw field (85 columns)

### Kept
| Raw field | Target | Conversion / note |
|---|---|---|
| incident_id | INCIDENT.incident_id | Number; keep as is |
| name | INCIDENT.incident_name | Trim spaces (80 rows) |
| description | INCIDENT.description | Long text |
| start_date | INCIDENT.start_date / end_date | Text dd.mm.yyyy to DATE; 'Not available' to NULL |
| end_date | INCIDENT.start_date / end_date | Text dd.mm.yyyy to DATE; 'Not available' to NULL |
| incident_type | INCIDENT_TYPE + INCIDENT_INCIDENT_TYPE | Split on ';'; 'Not available' to no row |
| receiver_name | INCIDENT_RECEIVER.receiver_name | Split on ';'; keep position as receiver_seq |
| receiver_country | INCIDENT_RECEIVER.country_id (via COUNTRY) | Split on ';'; look up or add country |
| receiver_country_alpha_2_code | COUNTRY.alpha2_code | Split on ';'; empty to NULL |
| receiver_category | SECTOR_CATEGORY | Split on ';'; distinct values (12) |
| receiver_subcategory | SECTOR / INCIDENT_RECEIVER.sector_id | Split on ';'; 'Not available' to NULL |
| initiator_name | INITIATOR + ATTRIBUTION_INITIATOR | Split on ';'; trim |
| initiator_country | ATTRIBUTION_INITIATOR.country_id / COUNTRY.alpha2_code | Split on ';' |
| initiator_alpha_2 | ATTRIBUTION_INITIATOR.country_id / COUNTRY.alpha2_code | Split on ';' |
| initiator_category | INITIATOR_CATEGORY / ATTRIBUTION_INITIATOR | Split on ';' |
| attribution_id | ATTRIBUTION.attribution_id | Repeated inside the list; keep one value |
| attribution_date | ATTRIBUTION.attribution_date | Text dd.mm.yyyy to DATE; 'Not available' to NULL |
| attribution_type | ATTRIBUTION (same name) | Text; 'Not available' to NULL |
| attribution_basis | ATTRIBUTION (same name) | Text; 'Not available' to NULL |
| attributing_actor | ATTRIBUTION.attributing_actor | Text; remove personal names, keep role |
| attributing_company | ATTRIBUTION (same name) | Text; 'Not available' to NULL |
| attributing_country | ATTRIBUTION.attributing_country_id | Look up COUNTRY |
| settled_initiator | ATTRIBUTION_INITIATOR.is_settled | Split on ';'; 'True'/'False' to Y/N |
| attribution_source_url | INCIDENT_SOURCE | Split on ';'; one row per URL; source_kind = ATTRIBUTION or INCIDENT |
| political_response_date | GOVERNMENT_RESPONSE (response_kind = POLITICAL) | Split on ';'; dd.mm.yyyy to DATE; remove personal names from actor |
| political_response_type | GOVERNMENT_RESPONSE (response_kind = POLITICAL) | Split on ';'; dd.mm.yyyy to DATE; remove personal names from actor |
| political_response_subtype | GOVERNMENT_RESPONSE (response_kind = POLITICAL) | Split on ';'; dd.mm.yyyy to DATE; remove personal names from actor |
| political_response_responding_country | GOVERNMENT_RESPONSE (response_kind = POLITICAL) | Split on ';'; dd.mm.yyyy to DATE; remove personal names from actor |
| political_response_responding_actor | GOVERNMENT_RESPONSE (response_kind = POLITICAL) | Split on ';'; dd.mm.yyyy to DATE; remove personal names from actor |
| mitre_initial_access | MITRE_TECHNIQUE + INCIDENT_MITRE | tactic = Initial Access / Impact; 'Not available' to no row |
| mitre_impact | MITRE_TECHNIQUE + INCIDENT_MITRE | tactic = Initial Access / Impact; 'Not available' to no row |
| has_disruption | INCIDENT.has_disruption | 'True'/'False' to Y/N |
| data_theft | INCIDENT.data_theft | Text category; 'Not available' to NULL |
| unweighted_intensity | INCIDENT (same name) | Text to NUMBER (verify) |
| weighted_intensity | INCIDENT (same name) | Text to NUMBER (verify) |
| impact_indicator_label | IMPACT_LEVEL.impact_label | Moved out: depends on the score (transitive) |
| impact_indicator_score | INCIDENT.impact_score (FK to IMPACT_LEVEL) | Text to NUMBER |
| functional_impact | INCIDENT.functional_impact | Text; 'Not available' to NULL |
| affected_entities | INCIDENT.affected_entities_range | Text range such as 1-10 |
| economic_impact_value | INCIDENT (same name) | 0 to NULL when economic_impact is empty; currency text |
| economic_impact_currency | INCIDENT (same name) | 0 to NULL when economic_impact is empty; currency text |
| legal_response_date | GOVERNMENT_RESPONSE (response_kind = LEGAL) | Split on ';'; yyyy-mm-dd to DATE; remove personal names from actor |
| legal_response_type | GOVERNMENT_RESPONSE (response_kind = LEGAL) | Split on ';'; yyyy-mm-dd to DATE; remove personal names from actor |
| legal_response_subtype | GOVERNMENT_RESPONSE (response_kind = LEGAL) | Split on ';'; yyyy-mm-dd to DATE; remove personal names from actor |
| legal_response_responding_country | GOVERNMENT_RESPONSE (response_kind = LEGAL) | Split on ';'; yyyy-mm-dd to DATE; remove personal names from actor |
| legal_response_responding_actor | GOVERNMENT_RESPONSE (response_kind = LEGAL) | Split on ';'; yyyy-mm-dd to DATE; remove personal names from actor |
| source_url | INCIDENT_SOURCE | Split on ';'; one row per URL; source_kind = ATTRIBUTION or INCIDENT |
| added_to_db | INCIDENT (same name) | Text yyyy-mm-dd to DATE |
| updated_at | INCIDENT (same name) | Text yyyy-mm-dd to DATE |

### Dropped (with reason)
| Raw field | Reason |
|---|---|
| inclusion_criterion | Research coding of how EuRepoC admitted the incident; not needed for classification or response. |
| inclusion_criterion_subcode | Sub-code of the field above; 57% placeholder. |
| source_disclosure | Research coding of who disclosed the incident; out of CyberWatch scope. |
| receiver_regions | Python-style list text; the region can be derived from the country. |
| initiator_subcategory | 56% empty or 'Not available'. |
| number_attributions | Derived: equals the number of ATTRIBUTION_INITIATOR rows. |
| initiator_country.1 | Duplicate of initiator_country. |
| initiator_category.1 | Duplicate of initiator_category. |
| cyber_conflict_issue | Geopolitical research coding; out of scope. |
| offline_conflict_issue | Geopolitical research coding; out of scope. |
| offline_conflict_name | Geopolitical research coding; out of scope. |
| offline_conflict_intensity | Geopolitical research coding; out of scope. |
| offline_conflict_intensity_subcode | Geopolitical research coding; out of scope. |
| number_political_responses | Derived: count of GOVERNMENT_RESPONSE rows. |
| zero_days | Almost always 'Not available'; out of scope. |
| zero_days_subcode | 97% placeholder. |
| user_interaction | 99% empty or 'Not available'. |
| disruption | Text description that repeats incident_type and has_disruption. |
| hijacking | Text description that repeats incident_type. |
| physical_effects_spatial | Research coding; out of scope. |
| physical_effects_temporal | Research coding; out of scope. |
| target_multiplier | Intermediate value; weighted_intensity already holds the result. |
| intelligence_impact | Research coding; functional_impact kept instead. |
| affected_entities_value | Is 0 in 1841 rows even when a range is given, so it is unreliable. |
| affected_third_countries | 55% placeholder; out of scope. |
| affected_third_countries_value | Companion of the field above. |
| economic_impact | Text label; economic_impact_value and currency kept instead (1647 empty). |
| state_responsibility_actor | Legal-analysis coding; out of scope. |
| il_breach_indicator | International-law coding; out of scope. |
| il_breach_indicator_subcode | International-law coding; out of scope. |
| evidence_for_sanctions_indicator | 'Not available' in 3408 rows; no data. |
| number_legal_responses | Derived: count of GOVERNMENT_RESPONSE rows. |
| attribution_legal_reference | Legal-analysis coding; out of scope. |
| attribution_legal_reference_subcode | Legal-analysis coding; out of scope. |
| response_indicator | Research score; CyberWatch records its own responses. |
| casualties | 'Not available' in all 3414 rows; no data. |

Kept: 49 fields. Dropped: 36 fields. Total: 85 of 85.

## 7. Where one record ends up (for the 5-minute demo)

Incident **4025** in the raw file becomes:

| Raw value | Lands in |
|---|---|
| incident_id, name, start_date, impact score | one row in INCIDENT |
| impact label | IMPACT_LEVEL (looked up by score) |
| incident_type (two values) | two rows in INCIDENT_INCIDENT_TYPE pointing to INCIDENT_TYPE |
| receiver name, country, subcategory (two victims) | two rows in INCIDENT_RECEIVER, with country_id and sector_id |
| source_url | one row per URL in INCIDENT_SOURCE |
| initiator and attribution values | ATTRIBUTION, INITIATOR, ATTRIBUTION_INITIATOR |
| political / legal response values | rows in GOVERNMENT_RESPONSE |
