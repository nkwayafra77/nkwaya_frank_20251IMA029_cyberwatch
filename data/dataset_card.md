# Dataset Card: EuRepoC Global Dataset of Cyber Incidents

**Student:** Nkwaya Frank | **ID:** 20251IMA029 | **Course:** INSY 8311 Database Development with PL/SQL | **Project:** CyberWatch


| Item | Value |
|---|---|
| Source | European Repository of Cyber Incidents (EuRepoC), *Global Dataset of Cyber Incidents* |
| Link | https://zenodo.org/records/14965395 (DOI 10.5281/zenodo.14965395) |
| Licence | **TO CONFIRM:** copy the exact licence wording from the Zenodo record page here before submitting |
| Format | CSV, UTF-8, comma-separated, one header row |
| File | `data/raw/eurepoc_global_dataset_1_3.csv` (never edited) |
| Size | 3,414 records, 85 columns, about 11.5 MB |
| Date collected | **TO FILL:** the date you downloaded it |
| One record represents | One publicly reported cyber incident |

## Personal data check

The victims, initiators and attributing bodies are organisations, groups or countries, not private individuals.
Two text columns, `attributing_actor` and `political_response_responding_actor`, can contain **names of public officials** (for example a deputy prime minister). Decision to confirm with the instructor: the raw file stays untouched and the personal names are removed when loading into the database in Phase IV (keeping only the role).

## Data quality report (counts from the raw file; nothing fixed yet)

**Keys and duplicates**
- 3,414 distinct `incident_id` values for 3,414 rows; 0 fully duplicated rows.
- 10 incident names appear more than once (different incidents with the same title; needs a look in Phase IV).
- 80 incident names have leading or trailing spaces.

**Missing values and placeholders**
- `Not available` is used as a text placeholder instead of an empty cell: `start_date` 92, `end_date` 1,873, `attribution_date` 1,509, `impact_indicator_label` 1,428, `functional_impact` 1,471.
- `casualties` is `Not available` in 3,414 of 3,414 rows, so the column holds no data.
- `evidence_for_sanctions_indicator` is `Not available` in 3,408 rows.
- Truly empty cells: `economic_impact` 1,647, `political_response_type` 230, `user_interaction` 145, `receiver_country_alpha_2_code` 78.
- `economic_impact_value` is 0 in 3,344 rows, but 0 means "unknown" there, not "no cost".
- 578 incidents have `Unknown` as an initiator name.
- `#N/A` (a spreadsheet error value) appears as an alpha-2 country code in 115 rows.

**Several values in one cell (separated by `;`)**
- 1,373 incidents have more than one victim (`receiver_name`); the largest has 1,089.
- 1,737 incidents have more than one `incident_type`: 49 different text combinations built from only 7 real values.
- 2,481 rows have more than one `source_url`; the largest cell holds 383 URLs.
- `receiver_regions` stores a Python-style list such as `['EUROPE', 'EASTEU']` in 3,411 rows.

**Lists that do not line up**
- Victim name, country, category and subcategory have the same number of items in 3,398 rows; 16 rows are misaligned.
- Initiator name, country, category and attribution id line up in 3,408 rows; 6 rows are misaligned.

**Dates stored as text, in two formats**
| Column | dd.mm.yyyy | yyyy-mm-dd | Other text / placeholder |
|---|---|---|---|
| start_date | 3322 | 0 | 92 |
| end_date | 1541 | 0 | 1873 |
| attribution_date | 1692 | 0 | 1722 |
| political_response_date | 250 | 0 | 3164 |
| legal_response_date | 0 | 82 | 3332 |
| added_to_db | 0 | 3414 | 0 |
| updated_at | 0 | 3414 | 0 |

All other numeric-looking fields (`economic_impact_value`, intensity scores) must be checked for text conversion in Phase IV.
