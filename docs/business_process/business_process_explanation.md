Phase I – Business Process Modeling

 Project Title
CyberWatch: Cybersecurity Incident Management System

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

Note on DELETE operatio:Deletion is not included in this process because historical cybersecurity incident records should be preserved for future analysis. If a record is incorrect, it should be corrected rather than permanently deleted.

 5. Modeling Tool
c
diagrams.net (draw.io)
published diagram link:https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&highlight=0000ff&edit=_blank&layers=1&link-icons=1&tooltip-icons=1&nav=1&title=CyberWatch_Business_Process.drawio&dark=auto#R%3Cmxfile%3E%3Cdiagram%20id%3D%22prtHgNgQTEPvFCAcTncT%22%20name%3D%22Page-1%22%3E7Vxbd6o4FP41PrYLCDcf1drTWdPbquecmT6mEDXTSBzAqufXT7gVCBQQjHg67UMXbJIN5Pv2LQkOwGS1%2B%2BbC9fKO2ogMFMneDcDVQFFMILP%2FgWAfCTQwjAQLF9uRSE4FM%2FwLxUIplm6wjbxcQ59S4uN1XmhRx0GWn5NB16XbfLM5Jfm7ruECFQQzC5Ki9C9s%2B8v4tRQjld8gvFgmd5b1%2BP1WMGkcv4m3hDbdZkRgOgATl1I%2FOlrtJogEY5eMS9Tv%2BoOr7w%2FmIsdv0sG%2B3%2B3v%2FzQsw3y53b55Nrq70S7kYVFNrNnz98kgeFu8ItBhZ%2BOlvyJMKLNDa4mJfQv3dBN09HxovSZnYxd5DMrHRKvMie5gwA8p0Edd%2FIs6PiSxgOlx%2FZgHSr7FLLhF3Cx6xjdINvEzPjJWxELk%2BmiXeZd4PL4hukK%2Bu2dNlhnITAVE%2FbYpvqoeg5aoSUDcc%2BcwptfiXXeKADuIQTgAkERxFpBK5GphqhjQj8ZyoOgkQNFi1syOF8Hx1ej7iLWaPfx4mkyZEK7WTOq8eOtQQ9SBvXK2Tys8ZE0q4qHm8RA3%2FFqkGNkFt1CDx7uZ041roaqGoABccLdZfEpdf0kX1IFkmkrHLt04NrJjwNI2t5SuY5z%2FQb6%2Fj3GGG5%2FmWRC7TuguUOVbqCVkKEPMRQT6%2BC0%2FSMeHAxw6%2BplBJYQFiWDwtkvso9kahrBsWZjKD80cEzKhhLphP6BLcCgboeG49BVlrihXhi4F4z9n1pORz8O%2FKkMKVDmLxCxm30dP3zMmk7%2FaymjUEpvhXJgqzGbU9iDleV0HFBv2a7jCJPDCN4i8IR9bML4QM19mIzWGBC8cdmKx50FuEWJD1yUTlkGsMpA1ozvE35iVKdIfjsWyFyc4vII%2BFA65WR21DK07A8a7p9Xy5nVzcTHd3K2v7QsTjy8AaOs136NYxmuW3qLMwMV7TRvN4Yb4t%2FAFkTFLPhahxoQXUe44JsHVR2jbmCEa3EqR1OYeF5yZxz0YOYH5R5DRSWH%2FUK7%2FuwmS5bGSHqYWFPUgOJGM7ke3zzPmZqVgQFjiwk6mdxkTTJtmhMEdO9ikYpiNc5ckldSE%2BeVh61wmKQFqcxm9D6tEjj0KSrvAwxPoediKhNeYHJrumMc2vrArezq4zzRYU%2Bz4XkbzYyDIOGo9zwmNq%2BQOas4OovunzHl%2FkQ5k0g%2Fljugg%2F1GEPkLwbxjkf7Jb2dBHQsJ7SRU05MK7fIR4XmkWrcBe0tXLxjsDoG1TkgxQBvRIkyS1MvKUAD0A18ITOINP4LR8AgcEJXDywZEhBZy9sp9Htgz4PAYODbOELGCxqABqMKiMF2QUX1hh2y4JIwUk7x9agSIbBVC4uSAz73xNUZiY6jHDd3lS3Uv03mH%2F76D7pRafPWeuXCUTg%2BHJPj7pmod3DejFECwNLzWVRWJTN1R9aJpyPqnTlcth9i%2BvP8pLYpUcTQ6L1VWwnk%2Bo7r8en1DXDZYH%2BinEDS7ll4X5ce3coO8%2FS5v51EW5yZgTz8KYJ0O%2FZDHnf4U%2Buy5LmYKe8wFhrTjfN%2BNCVll6eBqG6LoghjReXfqsDCmjBSTWhkRl3BP2XoO5Iit0GR9zI7xg4zdeVN7wxS2ZaSpvyi7k1J6Eb4o8FMQ30IFvZ1pXPE9nrWABRVj4RWYOlmQu8eioGB3ixGFraR0SuxoYepiROTzPE%2BbH9dbL1GULLpWreudfHLIXdvdRJ1U1E8FzKJD05DztG57lOj8iFzNgAr9wlHKzycyzXk64E63yNC0RRa7yPE1njw%2F3s2k7dzrUCtZYs9KiKkdwqOVreEZbc0yAqDVH0I85Hm2lBeglLvwkBlCemLTf53PeiB3XdZWP3XmtWIPG20%2BK052ftaYZMVNlt1Kkh%2FkcW8jte85DOUIiVOlWWoH%2FCVeqJnS1JiyTOcViVd0shipqnquLxZ93%2FfKELOrawUQE8tbU8aomIU4CoqkIwnDYfnWrJACX08TsJWXqVsFoufqlpng5QbA3h72maY03Ivxulj5hyrCzQae0dX53AcjvLlAkUdMVhi7c2NVedtV%2FMmNXjT6NXW282f%2B3M3ZCvT6XIBWFt3RRqZluird048vSu1t6r2FdNQ4lRduS%2FdT7TH5itA1D%2BppxzOvdznVR6bvaeAmpiOD5fpg1vb8SDpnGQabmCy4grGo2O0B2PuFVOtfCGfAzXsIqZ6U9jme6pt5yr26DJXU17xBlcah0XwI6z5Wdvj%2BNMZRLDkNTy6J1eI%2F8BzIl%2FY0P%2Br8%2FdJSjFvbvNlBVyLwFbwUeds%2FHv2hZgqyi8RQBlUyoaV9DSYX74EvmPzpoSkhekSJxAyOYjskMVCUdi5uOvoj3jiDQuHxRr%2F5WsKZ9DfEAR9uk98HEKyjiN7eJJp78RbyOHo8vVGqIV9O%2BzuOpRyJeQdGpidckL%2ByFeN1nmY7MyKLT4KKVarT1Prwi0zgtCZpkYV8kaIYd%2F9tPrUkATkuCYcn8y9eud%2BaQuV3vsvQxRT4o0dlp%2Bjt6EV7pjxGC6X8%3D%3C%2Fdiagram%3E%3C%2Fmxfile%3E
