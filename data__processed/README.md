# Folder for the processed data

After the processing script, it should contain:
* `full-processed-v1.csv`

Version 1 of preprocessed file columns:
* Demographics, symptomatic status, biomarker values:
    * `study_code` - unique id
    * `gender` - 'Male' or 'Female'
    * `age` - decimal age
    * `symptomatic` - 'Y'/'N' based on patient status
    * `cxcl10` - CXCL10 (LOD)
    * `cxcl10_log` - log transformed CXCL10
    * `il_1b` - IL-1B (LOD)
    * `il_1b_log` - log transformed IL-1B
    * `il_1b_ella` - More precise meassure of IL-1b done in under 5 year olds
    * `il_1b_ella_log` - log transformed `il_1b_ella`
    * `tfna_ella` - TFNA done in under 5 year olds
    * `tfna_ella_log` - log-transformed `tfna_ella`
* Any virus status:
    *  `any_virus` - 'Y'/'N', includes SARS-Cov or respiratory virus panel
    *  `virus_n` - number of RVP and SARS-Cov coinfections
* Respiratory panel:
    * `any_rvp` - 'Y'/'N', any of the rvp viruses
    * `rvp_n` - number of RVP coinfections
    * `rvp_any_[adeno | rv | hmpv | cov229 | covnl63 | flu_a | piv | rsv]` - 'Y'/'N', presence of any of the RVP viruses
    * `rvp_[adeno | rv | hmpv | cov229 | covnl63 | flu_a | piv | rsv]_ct` - raw Ct value of any of the RVP viruses
    * ~~`rvp_avg_ct` - average Ct value of RVP panel~~
    * ~~`rvp_max_ct` - max Ct value (ignoring NA) of RVP panel (NA in case of none)~~
    * `rvp_min_ct` - min Ct value (ignoring NA) of RVP panel (NA in case of none)
    * `rvp_[adeno | rv | hmpv | cov229 | covnl63 | flu_a | piv | rsv]_ct_imp_value` - Ct values with imputed NA: NA -> Inf
    * `rvp_[adeno | rv | hmpv | cov229 | covnl63 | flu_a | piv | rsv]_ct_imp_is_na` - 'Y'/'N', whether original Ct value is NA
* SARS-Cov Panel:
    * `any_sars` - 'Y'/'N' SARS-Cov
    * `sars_ct` - raw Ct value of any of the RVP viruses (mean of all the tests in case of multiple tests)
    * `sars_ct_imp_value` - Ct values with imputed NA: NA -> Inf (for computation where NA is removed automatically)
    * `sars_ct_imp_is_na` - 'Y'/'N', whether original Ct value is NA (meant to be used together with `sars_ct_imp_value`)
    * `sars_only` - Only COVID and no other virus (ignoring bacteria)
* Bacterial panel:
    * `any_bacteria` - 'Y'/'N', any of the bacteria
    * `bac_n` - number of bacteria coinfections
    * `bac_any_[pneu | influ | catarr]` - 'Y'/'N', presence of any of the bacteria
    * `bac_[pneu | influ | catarr]_ct` - raw Ct value of any of the RVP viruses
    * `albumin_ct` - Albumin
    * `bac_avg_ct` - average Ct value of RVP panel
    * `bac_max_ct` - max Ct value (ignoring NA) of RVP panel (NA in case of none)
    * `bac_min_ct` - min Ct value (ignoring NA) of RVP panel (NA in case of none)
    * `bac_[pneu | influ | catarr]_ct_imp` - Ct values with imputed NA: NA -> Inf
    * `bac_[pneu | influ | catarr]_ct_is_na` - 'Y'/'N', whether original Ct value is NA
* viral and bacterial coinfection:
    * `vir_bac_coinfect` - 'none' if no infection, 'only_[vir|bac]' if just viral or bacterial infection, 'both' if both viral and bacterial co-infection