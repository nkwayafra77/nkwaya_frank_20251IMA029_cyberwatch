
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

## 10 Phase I – Business Process Modeling

### Business Process
CyberWatch manages cybersecurity incident recording, classification, risk prioritization, and response tracking.

### Modeling Tool
diagrams.net (draw.io)

### Published Business Process Diagram LINK
https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&highlight=0000ff&edit=_blank&layers=1&link-icons=1&tooltip-icons=1&nav=1&title=CyberWatch_Business_Process.drawio&dark=auto#R%3Cmxfile%3E%3Cdiagram%20id%3D%22prtHgNgQTEPvFCAcTncT%22%20name%3D%22Page-1%22%3E7Vxbd6o4FP41PrYLCDcf1drTWdPbquecmT6mEDXTSBzAqufXT7gVCBQQjHg67UMXbJIN5Pv2LQkOwGS1%2B%2BbC9fKO2ogMFMneDcDVQFFMILP%2FgWAfCTQwjAQLF9uRSE4FM%2FwLxUIplm6wjbxcQ59S4uN1XmhRx0GWn5NB16XbfLM5Jfm7ruECFQQzC5Ki9C9s%2B8v4tRQjld8gvFgmd5b1%2BP1WMGkcv4m3hDbdZkRgOgATl1I%2FOlrtJogEY5eMS9Tv%2BoOr7w%2FmIsdv0sG%2B3%2B3v%2FzQsw3y53b55Nrq70S7kYVFNrNnz98kgeFu8ItBhZ%2BOlvyJMKLNDa4mJfQv3dBN09HxovSZnYxd5DMrHRKvMie5gwA8p0Edd%2FIs6PiSxgOlx%2FZgHSr7FLLhF3Cx6xjdINvEzPjJWxELk%2BmiXeZd4PL4hukK%2Bu2dNlhnITAVE%2FbYpvqoeg5aoSUDcc%2BcwptfiXXeKADuIQTgAkERxFpBK5GphqhjQj8ZyoOgkQNFi1syOF8Hx1ej7iLWaPfx4mkyZEK7WTOq8eOtQQ9SBvXK2Tys8ZE0q4qHm8RA3%2FFqkGNkFt1CDx7uZ041roaqGoABccLdZfEpdf0kX1IFkmkrHLt04NrJjwNI2t5SuY5z%2FQb6%2Fj3GGG5%2FmWRC7TuguUOVbqCVkKEPMRQT6%2BC0%2FSMeHAxw6%2BplBJYQFiWDwtkvso9kahrBsWZjKD80cEzKhhLphP6BLcCgboeG49BVlrihXhi4F4z9n1pORz8O%2FKkMKVDmLxCxm30dP3zMmk7%2FaymjUEpvhXJgqzGbU9iDleV0HFBv2a7jCJPDCN4i8IR9bML4QM19mIzWGBC8cdmKx50FuEWJD1yUTlkGsMpA1ozvE35iVKdIfjsWyFyc4vII%2BFA65WR21DK07A8a7p9Xy5nVzcTHd3K2v7QsTjy8AaOs136NYxmuW3qLMwMV7TRvN4Yb4t%2FAFkTFLPhahxoQXUe44JsHVR2jbmCEa3EqR1OYeF5yZxz0YOYH5R5DRSWH%2FUK7%2FuwmS5bGSHqYWFPUgOJGM7ke3zzPmZqVgQFjiwk6mdxkTTJtmhMEdO9ikYpiNc5ckldSE%2BeVh61wmKQFqcxm9D6tEjj0KSrvAwxPoediKhNeYHJrumMc2vrArezq4zzRYU%2Bz4XkbzYyDIOGo9zwmNq%2BQOas4OovunzHl%2FkQ5k0g%2Fljugg%2F1GEPkLwbxjkf7Jb2dBHQsJ7SRU05MK7fIR4XmkWrcBe0tXLxjsDoG1TkgxQBvRIkyS1MvKUAD0A18ITOINP4LR8AgcEJXDywZEhBZy9sp9Htgz4PAYODbOELGCxqABqMKiMF2QUX1hh2y4JIwUk7x9agSIbBVC4uSAz73xNUZiY6jHDd3lS3Uv03mH%2F76D7pRafPWeuXCUTg%2BHJPj7pmod3DejFECwNLzWVRWJTN1R9aJpyPqnTlcth9i%2BvP8pLYpUcTQ6L1VWwnk%2Bo7r8en1DXDZYH%2BinEDS7ll4X5ce3coO8%2FS5v51EW5yZgTz8KYJ0O%2FZDHnf4U%2Buy5LmYKe8wFhrTjfN%2BNCVll6eBqG6LoghjReXfqsDCmjBSTWhkRl3BP2XoO5Iit0GR9zI7xg4zdeVN7wxS2ZaSpvyi7k1J6Eb4o8FMQ30IFvZ1pXPE9nrWABRVj4RWYOlmQu8eioGB3ixGFraR0SuxoYepiROTzPE%2BbH9dbL1GULLpWreudfHLIXdvdRJ1U1E8FzKJD05DztG57lOj8iFzNgAr9wlHKzycyzXk64E63yNC0RRa7yPE1njw%2F3s2k7dzrUCtZYs9KiKkdwqOVreEZbc0yAqDVH0I85Hm2lBeglLvwkBlCemLTf53PeiB3XdZWP3XmtWIPG20%2BK052ftaYZMVNlt1Kkh%2FkcW8jte85DOUIiVOlWWoH%2FCVeqJnS1JiyTOcViVd0shipqnquLxZ93%2FfKELOrawUQE8tbU8aomIU4CoqkIwnDYfnWrJACX08TsJWXqVsFoufqlpng5QbA3h72maY03Ivxulj5hyrCzQae0dX53AcjvLlAkUdMVhi7c2NVedtV%2FMmNXjT6NXW282f%2B3M3ZCvT6XIBWFt3RRqZluird048vSu1t6r2FdNQ4lRduS%2FdT7TH5itA1D%2BppxzOvdznVR6bvaeAmpiOD5fpg1vb8SDpnGQabmCy4grGo2O0B2PuFVOtfCGfAzXsIqZ6U9jme6pt5yr26DJXU17xBlcah0XwI6z5Wdvj%2BNMZRLDkNTy6J1eI%2F8BzIl%2FY0P%2Br8%2FdJSjFvbvNlBVyLwFbwUeds%2FHv2hZgqyi8RQBlUyoaV9DSYX74EvmPzpoSkhekSJxAyOYjskMVCUdi5uOvoj3jiDQuHxRr%2F5WsKZ9DfEAR9uk98HEKyjiN7eJJp78RbyOHo8vVGqIV9O%2BzuOpRyJeQdGpidckL%2ByFeN1nmY7MyKLT4KKVarT1Prwi0zgtCZpkYV8kaIYd%2F9tPrUkATkuCYcn8y9eud%2BaQuV3vsvQxRT4o0dlp%2Bjt6EV7pjxGC6X8%3D%3C%2Fdiagram%3E%3C%2Fmxfile%3E#%7B%22pageId%22%3A%22prtHgNgQTEPvFCAcTncT%22%7D

### Business Process Diagram PDF
[View Diagram PDF](business_process_diagram.pdf)

### Business Process Explanation
[View Explanation PDF](business_process_explanation.pdf)

