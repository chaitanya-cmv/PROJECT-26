# Major Health Indicators — Sub-District Level Data

## Overview

This dataset contains **monthly public health indicator data reported at the sub-district level** across India, covering immunization, maternal and child health, family planning, disease surveillance, hospital operations, and mortality statistics. It reflects the kind of data typically reported through India's Health Management Information System (HMIS), aggregated below the district level.

- **Rows:** 500 records
- **Columns:** 311 indicators
- **Granularity:** One row per State → District → Sub-District → Sector, per reporting date
- **Geographic coverage:** Multiple Indian states (e.g., Bihar, Madhya Pradesh, Telangana)

## File

`Major_Health_Indicators_Sub-district_Level_Sample_Data.csv`

## Column Structure

Each column follows the pattern:

```
<Human-Readable Label> (<snake_case_code>)
```

For example: `DPT 1 (Child Immunisation) (child_dpt1)` — the label before the parentheses is for readability; the code in parentheses is the short machine-friendly field name.

### Key column groups

| Group | Examples | Description |
|---|---|---|
| **Identifiers** | `date`, `state_name`, `state_code`, `district_name`, `district_code`, `subdistrict_name`, `subdistrict_code`, `sector` | Geographic and temporal keys uniquely identifying each record |
| **Child Immunisation** | `child_bcg`, `child_dpt1`–`child_dpt3`, `child_opv1`–`child_opv3`, `child_measles1`, `child_rota1`–`3`, `child_vita1` | Doses administered for routine childhood vaccines |
| **Childhood Disease** | `child_diarr`, `child_pneumonia`, `child_measles`, `child_malaria`, `child_tb`, `child_sam` | Reported childhood disease case counts |
| **Maternal & Pregnancy Care** | `pw_anc_reg`, `pw_tt1`, `pw_hb4plus_test`, `pw_gdm_pos`, `mat_death_bleed`, `mat_death_htn_fits` | Antenatal care service delivery and maternal death causes |
| **Family Planning** | `iucd_removals`, `nsv_done`, `condom_pcs_dist`, `cop_cycles_dist` | Contraceptive and sterilization service counts |
| **Disease Surveillance** | `dengue_elisa_pos`, `mal_pf_micro_pos`, `kala_azar_positive_cases`, `je_pos` | Positive case counts for vector-borne and notifiable diseases |
| **Hospital Operations** | `inpatient_female_adults`, `inpatient_male_adults`, `csec_total`, `lab_tests_done`, `usg_tests`, `xray_tests` | Inpatient volumes and diagnostic service counts |
| **Mortality** | `inf_death_24h`, `adol_death_suicide`, `mat_death_unknown`, `death_sncu` | Death counts by age group and cause |
| **Outpatient Services** | `outpatient_diabetes`, `outpatient_hypertension`, `outpatient_mental_illness`, `outpatient_oncology` | OPD attendance by condition |
| **Quality/Satisfaction** | `mera_aspatal_score`, `drug_stockout_rate` | Patient satisfaction and supply-chain indicators |

> **Note:** Most indicators are raw **counts** (number of doses given, cases reported, procedures performed) rather than rates or percentages, with the exception of `mera_aspatal_score` (a satisfaction score, 0–100%) and `drug_stockout_rate` (a percentage).

## Data Quality Notes

- Many cells contain `0` where a service was not reported or not applicable for that sub-district/period — this is common in administrative health data and should be distinguished from true missing values during cleaning.
- `sector` values vary (e.g., `Public`, `Private`, `Rural`) and may need standardization before grouping.
- Dates are stored as strings in `YYYY-MM-DD` format and should be parsed with `pd.to_datetime()`.
- Given the high column count relative to rows, expect many sparse/zero-heavy columns — worth checking column-level completeness before including a feature in analysis.

## Suggested Uses

- Public health surveillance and disease trend analysis
- Immunization coverage analysis by geography
- Maternal and child health service delivery evaluation
- Health system performance benchmarking across districts/sectors

## License / Attribution

*(Add details here on the data source and any usage license/attribution requirements before publishing.)*
