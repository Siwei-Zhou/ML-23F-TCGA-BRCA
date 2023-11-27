# ML-23F-TCGA-BRCA

## Data Preprocessing
### 0 - download data - clinical.tsv & gdc_sample_sheet.tsv & gdc_download (1231 files)
1. Get data according to the searching strategy: https://portal.gdc.cancer.gov/exploration?filters=%7B%22content%22%3A%5B%7B%22content%22%3A%7B%22field%22%3A%22cases.case_id%22%2C%22value%22%3A%5B%22set_id%3AYf1AzIsBuNAoDROPx1u7%22%5D%7D%2C%22op%22%3A%22IN%22%7D%5D%2C%22op%22%3A%22AND%22%7D&searchTableTab=cases
2. Add into cart. 
Project: TCGA-BRCA	
Cases: 1,095
Files: 1,231
File Size: 5.22 GB	
3. Click Clinical, Sample Sheet, Download to get all the data prepared.


### 1 - merge data - Merge_data.ipynb
1. Merge gdc_sample_sheet.tsv (Case ID) with clinical.tsv (case_submitter_id) 
2. Add File name from gdc_sample_sheet into clinical.tsv termed as file_id


### 2 - compile data - Data_compiling.ipynb
1. Extract tpm_unstranded column of 1231 sample and combine them into 1 csv file combined_tpm_unstranded.csv (not on github due to file size)
2. Name the column with the file name of each file
3. Add common column gene_name and gene_type



### 3 - Feature selection - Merge_data.ipynb, Merge_RNA_clinical.ipynb

1. Transpose on combined_tpm_unstranded.csv: delete gene_id, use gene name as the column name.
2. merged_clinical_gdc_sample_sheet.csv: 160  columns before selection
3. Delete columns that are all empty: 37 columns left (the empty cell is marked as “'--”)
4. Check frequency of each column one by one: found 'treatment_or_therapy' and 'treatment_type' are those not important and cause duplication. 1231 rows, 35 columns left. (filtered_clinical.csv) (Merge_data.ipynb)
5. Combine this (‘File ID’) with transposed version of combined_tpm_unstranded.csv(‘case_id’). 1231 rows, 60695 columns. (merge_RNA_clinical_df.csv)  (Merge_RNA_clinical.ipynb)
