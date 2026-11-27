# How to upload data to Labguru

Use this guide to add PMLB cases, specimens, models, assay records, and banked stocks. Use the single-record Labguru form for one entry and the collection or Stocks Excel template for a batch. See the [Naming Convention](../naming_convention/index.md) for record IDs and the [Labguru schema](../schema/index.md) for field definitions.

!!! note "Create parent records first"
    Follow **Case → Specimen → Model**. Search for the parent before creating a new record. For a model derived from another model, make sure the source model already exists. Assays and stocks can be added once the record they attach to exists.

!!! note "Check required fields where you enter the data"
    The schema describes what Labguru stores. On a single-record form, check the required markers on that form. In Excel, use the asterisks and header notes in the current template. Leave **System ID** blank for a new collection item and keep the existing ID when updating an item.

## Add a case if it doesn't exist

**Before you start.** The case is the first record for a patient; specimens and models all link back to it. Look up the case using its PMLB case alias or identifier. If the case is missing, create it.

**Where.** Go to **Dashboard → PMLB Case** and open the **Add New PMLB case** form.

**Required fields.** The form marks `Name`, `sex`, `oncotree_code`, `primary_tumor_site`, and `cancer_type_detailed` as required. See the [case schema](../schema/index.md#pmlb_case).

**Steps**

1. Enter the PMLB case name and relevant identifiers from the approved case record. The form has separate fields for `case_PPID`, `stem_PPID`, `primary_study_id`, `alias.id`, and `patient_ID`. Enter the identifiers that have already been assigned to the case.
2. Complete the required fields using the case information and select **Save**.
3. Reopen the case and verify the name and identifiers before adding a specimen.

**Linking.** The case has no parent in this workflow. Link its specimens from their own records.

## Add a specimen

**Before you start.** Confirm the source case exists and check for an existing specimen record.

**Where.** Go to **Dashboard → PMLB Specimen → Add New Specimen**.

**Required fields.** <!-- TODO: Verify the single-record form. --> The Excel template marks `Name`, `sample_class`, `tumor_normal_designation`, `specimen_collection_site`, and `Parent PMLB_case` as required for the specimen record. See the [specimen schema](../schema/index.md#pmlb_specimen).

**Steps**

1. Enter the specimen name using the [Naming Convention](../naming_convention/index.md).
2. Enter the specimen class, tumor or normal designation, and collection site from the specimen record.
3. Link the case, save the specimen, and confirm the saved record opens the correct case.

**Linking.** Link to the existing `PMLB_case` record. In Excel, enter the exact case **Name** or **SysID** in `Parent PMLB_case`. <!-- TODO: Confirm how to select the case in the form. -->

## Add an organoid model

**Before you start.** Confirm the source specimen exists. For a xenograft-derived organoid (XDO), also find the source xenograft and confirm its model ID.

**Where.** Go to **Dashboard → PMLB Organoid → Add New Organoid**.

**Required fields.** <!-- TODO: Verify the single-record form. --> The Excel template marks `Name`, `sample_class`, and `Parent PMLB_specimen` as required for the model record. It also includes `organoid_PPID` and `primary_study_name`. See the [organoid schema](../schema/index.md#pmlb_organoid).

**Steps**

1. Search for the full model ID to check whether it already exists. Enter the model ID as the name, for example `PHLC0053.TXO1`. See the [Naming Convention](../naming_convention/index.md) for model and sample ID formats.
2. Set the sample class. The Excel dropdown uses `PO` for patient-derived organoids and `XO` for xenograft-derived organoids. <!-- TODO: Confirm the form labels and what to enter in `organoid_PPID` and `primary_study_name`. -->
3. Link the specimen. For an XDO, enter the source xenograft’s model ID in `source_xenograft_modeID`. Save and check the specimen and source details on the saved record.

**Linking.** In Excel, enter the specimen record’s exact **Name** or **SysID** in `Parent PMLB_specimen`. The column is marked required with no XDO exception shown. The workbook also has a separate `Parent PMLB_xenograft` column that accepts the source xenograft’s **Name** or **SysID**. <!-- TODO: Confirm when PMLB fills this separate parent link and how staff select both records in the form. -->

## Add a xenograft model

**Before you start.** Confirm the source specimen exists. For an organoid-derived xenograft (ODX), also find the source organoid and confirm its model ID.

**Where.** Go to **Dashboard → PMLB Xenograft → Add New Xenograft**.

**Required fields.** See the [xenograft schema](../schema/index.md#pmlb_xenograft). The schema field list includes `name`, `xenograft_PPID`, `primary_study_name`, `sample_class`, and `host_strain_name`. <!-- TODO: Verify which fields and parent links are required in the form and in the current Excel template. -->

**Steps**

1. Search for the model ID to check for an existing record. Enter the model ID as the name, following the [Naming Convention](../naming_convention/index.md).
2. Complete the required fields from the xenograft record. <!-- TODO: Confirm the sample class options and the expected PPID, study, and host strain values. -->
3. Link the specimen. For an ODX, record the source organoid’s model ID. Save and verify the source details.

**Linking.** The specimen is the model’s source record. For an ODX, enter the source model ID in `source_organoid_modeID`. <!-- TODO: Confirm the specimen selector and whether the form has a separate parent organoid link. -->

## Add assay or sequencing records

**Before you start.** Find the specimen, organoid, or xenograft that the result belongs to. Confirm the passage where applicable.

**Where.** Open the collection for the assay or sequencing method. <!-- TODO: Confirm the collection names and click paths. -->

**Required fields.** Use the following field list to prepare the assay data. <!-- TODO: Verify the required markers for each form and import template. -->

| Collection | Fields to check |
| --- | --- |
| [Flow](../schema/index.md#flow_assay), [growth](../schema/index.md#growth_assay), [histology](../schema/index.md#histology_assay), [STR](../schema/index.md#str_assay) | `name`, `passage_number`, assay-specific date |
| [Pathogen assay](../schema/index.md#pathogen_assay) | `name`, `passage_number`, `pathogen_assay_type`, `pathogen_assay_date` |
| [ATAC, RNAseq, WGS, WES](../schema/index.md#atac-rnaseq-wgs-wes) | `name`, `passage_number`, `library_kit`, `sequencing_platform`, `read_length`, `single_or_paired_end` |

**Steps**

1. Open a new record in the relevant collection. Enter the assay or sequencing information from the source data.
2. Link the record to the correct specimen or model. Save and check the link and passage on the saved record.

**Linking.** Select the parent appropriate to the assay. <!-- TODO: Verify the parent choices and how to enter the link for each collection. -->

## Add banked inventory

**Before you start.** Confirm the model exists and match each vial label to its passage, box, and position on the freezing or transfer sheet.

**Where.** For one vial, open the model record and choose **Add Stock**. For a batch, use the Excel template from **Storage → Stocks → Import**.

**Required fields.** The Stocks template marks `Stock name`, `Inventory collection`, and `collection_protocol` as required. Its notes also require a box or storage location. <!-- TODO: Verify the single-vial form and which collection protocol to select for each PMLB banking workflow. --> See the [Labguru schema](../schema/index.md) for model-level fields such as `PMLB_banked_location`, `PMLB_banked_date`, and `PMLB_banked_by`.

**Steps**

1. Enter the stock name and set the stock type to **Vial** when recording a vial. Record the passage and collection protocol.
2. For a batch, enter one row per vial. Select the model’s collection and enter the existing model’s **SysID** in `Inventory item sysID`. Leave **Stock ID** blank for a new vial.
3. Enter the exact **Box name** and numeric **Stock position** for each boxed vial. Confirm the box and slot against the physical inventory before saving or importing. A box name that doesn’t match an existing box can create a new one.
4. Check the saved or imported stock records against the inventory sheet, including the model, vial count, box, and position.

**Linking.** **Inventory item sysID** identifies the parent model. **Stock ID** identifies an individual vial and is used when updating that vial.

## Import or update records in bulk

Use the collection’s Excel template to **add new records**. To **change existing records**, export the affected records, edit the workbook, and re-import it.

### Add new records

1. Download the blank Excel template from the relevant collection (**⋯ → Import/Update** on the collection’s index page) or the **Stocks** page.
2. Enter one row per new record and preserve the column headers. Leave **System ID** blank for new cases, specimens, and models. Leave **Stock ID** blank for new vials and enter the existing model’s **SysID** in `Inventory item sysID` to link each vial.
3. Upload the workbook from the same page. Review the import summary and verify the IDs, parent links, and storage positions as applicable. When creating parent and child records in separate imports, verify the parent import before starting the child import.

### Update existing records

1. Select the records to change in the relevant collection or **Storage → Stocks**. Choose **Export** and keep an untouched copy of the fresh export.
2. Edit only the intended values in a working copy. Keep the exported **System ID** for each collection record or **Stock ID** for each vial. Preserve the column headers. Values submitted in the workbook can overwrite values currently in Labguru.
3. Re-import the workbook from the same page using **Import/Update**. Review the import summary and check the updated records. If stocks moved, verify their actual box and position.
