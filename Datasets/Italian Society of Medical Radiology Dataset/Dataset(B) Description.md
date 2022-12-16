url: https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/LQDFSE

This dataset contains COVID-19 cases that we can test the classification algorithms on. 
First, we composed a dataset of 68 COVID-19 cases from the Italian society of medical and 
intervention radiology society (SIRM) database. Second, for Non-COVID-19 cases, we 
composed a dataset of 62 Flu cases from the influenza research database (IRD). 
Then we merged the two datasets and shuffled them randomly to obtain an IHC dataset with 
two decision subsets; {COVID-19, Flu}. It should be noted that we faced a problem with 
data of the 68 COVID-19 cases obtained from SIRM. Specifically, that data was unstructured, 
in the sense that the features of each case were described verbally in a separate paragraph. 
Therefore, we had to first structure the data in a matrix format consistent with that 
of the Flu cases. The resulting mixed dataset contains features that are categorical, 
such as cough, and features that are numerical, such as partial pressure of oxygen (PO2).
Additionally, since not all patients undertook the same medical tests (for example, some
patients had a blood test and others did not), there were missing feature values. 
As such, the dataset used in the present work is heterogeneous with some of the feature 
values are missing.

