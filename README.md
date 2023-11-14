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
