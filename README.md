# Clinical SAS & CDISC Standards Pipeline Simulation

**Author:** Vaibhav Kawale  
**Protocol:** CLIN001  
**Environment:** SAS OnDemand for Academics / Base SAS  

## Project Overview
This repository contains an end-to-end clinical data programming pipeline developed using Base SAS. The workflow demonstrates the full data lifecycle from raw electronic source intake to regulatory-standard clinical study outputs.

---

## Data Pipeline Architecture

1. **Raw EDC Ingestion (`RAW_DEMO`, `RAW_AE`)**
   * Simulated multi-center electronic clinical trial logs for Demographics and Adverse Events.

2. **SDTM Mapping (`SDTM DM`, `SDTM AE`)**
   * Converted raw records into CDISC SDTM standard domains.
   * Derived global unique subject identifiers (`USUBJID`) using `catx`.
   * Standardized character dates into ISO 8601 strings (`YYYY-MM-DD`).
   * Computed age using `yrdif` and standardized controlled terminology (Sex, Race, MedDRA preferred terms).

3. **ADaM Derivations (`ADaM ADSL`, `ADaM ADAE`)**
   * Created subject-level analysis dataset (`ADSL`) with treatment assignments and safety flags (`SAFFL`).
   * Merged event logs to generate `ADAE`.
   * Derived the core Treatment-Emergent Adverse Event flag (`TRTEMFL`) by comparing event onset against first study dose dates.

4. **Safety Reporting (TLFs)**
   * Generated Summary Table: Treatment-Emergent Adverse Events by Treatment Group and Severity (`PROC FREQ`).
   * Generated Patient Listing: Severe Adverse Event Records for Clinical Review (`PROC PRINT`).

---

## Repository Contents
* `Program_1.sas`: Complete, executable Base SAS source code with clean log execution.
* `clinical_SAS_CDISC_pipeline_project.pdf`: Formatted project documentation and specification overview.
* 
