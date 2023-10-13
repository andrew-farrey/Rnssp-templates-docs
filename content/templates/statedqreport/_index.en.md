---
disableToc: false
title: State Data Quality Report
weight: 40
tags: ["data quality", "data quality metrics", "timeliness", "completeness", "validity", "NSSP priority elements"] 
---

```yaml
name: state_dq_report
fullname: State Data Quality Report
description: >
  This updated template summarizes data quality metrics, including 
  timeliness, completeness, and validity. 
  It currently includes NSSP Priority 1 & NSSP Priority 2 elements.
  Original Code By: Andrew Farrey (Kentucky Injury Prevention and Research Center).
  Adapted to the Rnssp Package by: Gbedegnon Roseric Azondekon. 
  National Syndromic Surveillance Program (NSSP). 
  Centers for Disease Control and Prevention (CDC).  
create_dir: true
```
---
## Detailed Description

*Updated on 10/13/2023.*

The state data quality template calculates and summarizes syndromic surveillance data quality metrics pulled from the BioSense platform and the ESSENCE application programming interface (API) similar to the NSSP Data Quality Dashboards. The template assesses coverage, timeliness, completeness, and validity of patient encounters limited to the selected calculated patient class (C_Patient_Class) that occurred during the chosen date range, and currently assesses all NSSP Priority 1 and NSSP Priority 2 data elements for completeness and validity. The default start and end dates include the previous two weeks of data, with the recommended two-day lag time reflected to provide more time for encounter data to arrive. Note that selecting a date range longer than 90 days will result in extensive rendering time.

The teamplate is broken down into four sections:

- Coverage
- Timeliness
- Completeness
- Validity

Coverage visualizations include interactive plots of the total active facility count, total patient encounters limited to the selected C_Patient_Class, total HL7 messages received by BioSense for patient encounters limited to the selected C_Patient_Class, and a table of currently onboarding facilities.

Timeliness visualizations include an overall timeliness plot (depicting first message timeliness), an interactive plot of message counts by NSSP Timeliness Category by facility, an interactive plot of message percentages by NSSP timeliness count by facility, a table containing mean and median first message timeliness by facility (first message "lag"/delay), a table containing mean and median chief complaint timeliness by facility (chief complaint "lag"/delay), and a table containing mean and median diagnosis code timeliness by facility (diagnosis code "lag"/delay). BioSense platform arrival date time stamps have been adjusted to reflect the user’s selected time zone to avoid adversely affecting timeliness calculations.

Completeness is assessed by data element across the entire patient encounter (required data fields must be present at least once per C_Biosense_ID), while validity is assessed by data element on a per message or per patient encounter basis, depending on each data field’s requirement level (see the validity definition table in the template or the [NSSP Data Dictionary](https://www.cdc.gov/nssp/biosense/docs/NSSP-Data-Dictionary-508.xlsx) for more information). 

Completeness visualizations include overall completeness plots for each NSSP priority level broken down by data element, time series plots of CCAvailable and DDAvailable pulled using the ESSENCE API, and a table containing chief complaint and diagnosis code completeness by facility. Validity visualizations include overall validity plots for both NSSP priority levels broken down by data element, validity tables for both NSSP priority level data elements by facility, time series plots of CCInformative and DDInformative pulled using the ESSENCE API, an interactive plot containing messages sent to the user's site exceptions table, and a table containing error message counts by facility and error type the BioSense platform received during the selected date range.

Interactive plots were created using the [plotly](https://plotly.com/r/) package. Interactive tables were created using the [DT](https://rstudio.github.io/DT/), [reactable](https://glin.github.io/reactable/index.html), and [reactablefmtr](https://kcuilla.github.io/reactablefmtr/) packages.

---
## User Inputs

* NSSP Username: NSSP ESSENCE account username
* NSSP Password: NSSP account password
* Site ID: Geographic region. Must select one participating site. 
* Start Date: Start date
* End Date: End date
* Patient Class: Can be either "E (Emergency Department)", "I (Inpatient)", or "O (Outpatient)"
* Time Zone: User's time zone.

---
## Output

When knit with parameters, this template generates a report in HTML format.

---
## Add this template

```r
# Add `state_dq_report` to my existing Rnssp installation
Rnssp::add_rmd_template("state_dq_report")
```
---
## Remove this template

```r
# Remove `state_dq_report` from my existing Rnssp installation
Rnssp::remove_rmd_template("state_dq_report")
```

---
[**Latest Update!**](https://cdcgov.github.io/Rnssp-rmd-templates/changelogs/#state-data-quality-report-template-state_dq_report)

*For questions, ideas for improvement/collaboration, or attribution, please submit an issue [here](https://github.com/CDCgov/Rnssp-rmd-templates/issues).*

---
{{% button href="https://github.com/CDCgov/Rnssp-rmd-templates/raw/master/zip/state_dq_report.zip" icon="fas fa-download" %}}Download this template{{% /button %}}
