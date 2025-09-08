# Labguru Schema

This page documents the schema used in PMLB’s Labguru instance.  
Each entity has its fields listed in a structured table.  

Columns:  
- **Required**: Is this field mandatory? (`Yes/No`)  
- **Field Type**: Data type (e.g., string, integer, date)  
- **Input Hint**: Guidance for data entry  
- **Permissible Values**: Allowed controlled vocabulary, if any  

---

## PMLB_case

**Children:** `PMLB_specimen`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique identifier | |
| name | Yes | string | Case name | |
| case_PPID | Yes | string | Patient PPID | |
| stem_PPID | No | string | Stem PPID if applicable | |
| primary_study_id | Yes | string | Study ID | |
| sex | Yes | categorical | Male/Female/Other | Male, Female |
| oncotree_code | Yes | string | Oncotree cancer code | Oncotree codes |
| primary_tumor_site | Yes | string | Tumor site | |
| cancer_type_detailed | Yes | string | Detailed cancer type | |
| smoke_history | No | categorical | Smoking history | Yes/No |
| smoke_pack_year(PY) | No | numeric | Pack-years smoked | |
| ethnicity_self_assessed | No | string | Self-reported | |
| ethnicity_genome | No | string | Genomic inferred | |
| alias.id | No | string | Alternate identifier | |

---

## PMLB_specimen

**Parent:** `PMLB_case`  
**Children:** `PMLB_organoid`, `PMLB_xenograft`, `WGS`, `WES`, `RNAseq`, `ATAC`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique specimen ID | |
| name | Yes | string | Specimen name | |
| associate_study | No | string | Related study | |
| alias.id | No | string | Alternate identifier | |
| sample_class | Yes | categorical | Sample class | Tumor, Normal |
| tumor_normal_designation | Yes | categorical | Tumor/Normal | Tumor, Normal |
| primary_recurrence_metastasis | No | categorical | Clinical designation | Primary, Recurrence, Metastasis |
| TNM_stage | No | string | TNM staging | |
| specimen_collection_site | No | string | Collection site | |
| specimen_collection_date | No | date | yyyy-mm-dd | |
| procedure | No | string | Collection procedure | |
| distributed_specimen_label | No | string | Label | |
| specimen_barcode | No | string | Barcode | |
| specimen_processor | No | string | Person/role | |
| SNAP_status | No | categorical | Frozen in SNAP | Yes/No |
| history_blockID | No | string | Block ID | |
| specimen_weight(g) | No | numeric | Weight in grams | |
| specimen_volume(mL) | No | numeric | Volume in mL | |
| cell_yield(x10^6) | No | numeric | Cell count in million | |
| specimen_comment | No | text | Free text | |

---

## PMLB_organoid

**Parent:** `PMLB_specimen`  
**Children:** `growth_assay`, `pathogen_assay`, `flow_assay`, `STR_assay`, `histology_assay`, `WGS`, `WES`, `RNAseq`, `ATAC`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique organoid ID | |
| name | Yes | string | Organoid name | |
| organoid_PPID | Yes | string | Organoid PPID | |
| primary_study_name | Yes | string | Study name | |
| associate_studies | No | string | Related studies | |
| alias.id | No | string | Alternate ID | |
| sample_class | Yes | categorical | Sample class | |
| source_xenograft_modeID | No | string | Source xenograft model ID | |
| source_xenograft_passage | No | numeric | Passage number | |
| source_xenograft_collection_date | No | date | yyyy-mm-dd | |
| source_xenograft_collection_note | No | text | Notes | |
| sample_SNAP_status | No | categorical | SNAP frozen | Yes/No |
| sample_histo/blockID | No | string | Block ID | |
| sample_weight(g) | No | numeric | Weight in g | |
| sample_volume(mL) | No | numeric | Volume in mL | |
| sample_cell_yield(x10^6) | No | numeric | Cell count (million) | |
| model_generated_by | No | string | Lab/PI | |
| model_generation_date | No | date | yyyy-mm-dd | |
| media | No | string | Culture medium | |
| split_ratio | No | numeric | Ratio | |
| passage_interval(day) | No | numeric | Days | |
| culture_note | No | text | Notes | |
| long_term_organoid | No | categorical | Stored long term | Yes/No |
| PMLB_banked_status | No | categorical | Banking status | Banked, Not Banked |
| PMLB_banked_location | No | string | Location | |
| PMLB_banked_comments | No | text | Notes | |
| PMLB_banked_date | No | date | yyyy-mm-dd | |
| PMLB_banked_by | No | string | Person | |
| deposit_distribution_permission | No | categorical | Permission flag | Yes/No |
| tumor_normal_designation | No | categorical | Tumor/Normal | |
| organoid_comment | No | text | Notes | |

---

## PMLB_xenograft

**Parent:** `PMLB_specimen`  
**Children:** `pathogen_assay`, `STR_assay`, `histology_assay`, `WGS`, `WES`, `RNAseq`, `ATAC`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique xenograft ID | |
| name | Yes | string | Xenograft name | |
| xenograft_PPID | Yes | string | Xenograft PPID | |
| primary_study_name | Yes | string | Study name | |
| associate_studies | No | string | Related studies | |
| alias.id | No | string | Alternate ID | |
| sample_class | Yes | categorical | Sample class | |
| source_organoid_modeID | No | string | Source organoid model ID | |
| source_organoid_passage | No | numeric | Passage number | |
| source_organoid_collection_date | No | date | yyyy-mm-dd | |
| sample_SNAP_status | No | categorical | SNAP frozen | Yes/No |
| sample_histo/blockID | No | string | Block ID | |
| sample_weight(g) | No | numeric | Weight in g | |
| model_generated_by | No | string | Lab/PI | |
| model_generation_date | No | date | yyyy-mm-dd | |
| host_strain_name | Yes | string | Host strain | |
| host_strain_nomenclature | No | string | Standard strain name | |
| engraftment_site | No | string | Engraftment site | |
| engraftment_type | No | string | Engraftment type | |
| engraftment_material | No | string | Material used | |
| engraftment_material_status | No | string | Status | |
| pubmed_ID | No | string | PubMed reference | |
| certis_id | No | string | Vendor ID | |

---

## flow_assay

**Parent:** `PMLB_organoid`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique ID | |
| name | Yes | string | Assay name | |
| passage_number | Yes | integer | Passage | |
| flow_assay_date | Yes | date | yyyy-mm-dd | |
| flow_assay_technician | No | string | Technician | |
| CD326 | No | numeric | Expression | |
| mH2K | No | numeric | Expression | |
| CD133 | No | numeric | Expression | |
| flow_assay_comment | No | text | Notes | |

---

## growth_assay

**Parent:** `PMLB_organoid`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique ID | |
| name | Yes | string | Assay name | |
| passage_number | Yes | integer | Passage | |
| doubling_rate | No | numeric | Rate | |
| growth_assay_date | Yes | date | yyyy-mm-dd | |
| growth_assay_technician | No | string | Technician | |
| growth_assay_comment | No | text | Notes | |

---

## histology_assay

**Parent:** `PMLB_organoid`, `PMLB_xenograft`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique ID | |
| name | Yes | string | Assay name | |
| passage_number | Yes | integer | Passage | |
| histology_assay_date | Yes | date | yyyy-mm-dd | |
| block_number | No | string | Block ID | |
| histology_results | No | text | Results | |
| IHC | No | string | Immunohistochemistry | |
| histology_assay_technician | No | string | Technician | |
| histology_assay_comment | No | text | Notes | |

---

## pathogen_assay

**Parent:** `PMLB_organoid`, `PMLB_xenograft`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique ID | |
| name | Yes | string | Assay name | |
| passage_number | Yes | integer | Passage | |
| pathogen_assay_order_number | No | string | Order number | |
| pathogen_assay_type | Yes | string | Type | |
| pathogen_assay_date | Yes | date | yyyy-mm-dd | |
| pathogen_assay_technician | No | string | Technician | |
| pathogen_result | No | string | Result | |
| pathogen_assay_comment | No | text | Notes | |

---

## STR_assay

**Parent:** `PMLB_organoid`, `PMLB_xenograft`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique ID | |
| name | Yes | string | Assay name | |
| passage_number | Yes | integer | Passage | |
| STR_assay_date | Yes | date | yyyy-mm-dd | |
| control | No | string | Control used | |
| control_type | No | string | Control type | |
| %match | No | numeric | Match percentage | |
| STR_assay_technician | No | string | Technician | |
| STR_assay_comment | No | text | Notes | |

---

## ATAC / RNAseq / WGS / WES

**Parent:** `PMLB_specimen`, `PMLB_organoid`, `PMLB_xenograft`

| Field | Required | Field Type | Input Hint | Permissible Values |
|-------|----------|------------|------------|--------------------|
| sysid | Yes | string | Unique ID | |
| name | Yes | string | Assay name | |
| passage_number | Yes | integer | Passage | |
| library_kit | Yes | string | Library prep kit | |
| sequencing_platform | Yes | string | Platform used | Illumina, etc. |
| sequencing_company | No | string | Vendor | |
| quote_number | No | string | Quote reference | |
| expected_depth | No | numeric | Expected sequencing depth | |
| actual_depth | No | numeric | Achieved sequencing depth | |
| humam_genome_depth | No | numeric | Coverage | |
| read_length | Yes | numeric | Read length | |
| single_or_paired_end | Yes | categorical | PE/SE | Single-end, Paired-end |
| sequencing_submitter | No | string | Person | |
| sequencing_submission_date | No | date | yyyy-mm-dd | |
| sequence_pass_qc | No | categorical | QC flag | Pass/Fail |
| fastq_directory | No | string | Directory | |
| fastq_path | No | string | Path | |
| sequence_sample_id | No | string | Sample ID | |

---

