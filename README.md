# COVID-19 Computational Drug Discovery

# INTRODUCTION

<div style="text-align: justify">
This project is a computational drug discovery project that attempts to find a compound or a molecule that will inhibit the function of SARS-CoV2, hence its name, COVID-19-CDD.
</div>

# METHODS

<div style="text-align: justify">
The Chembl Database, a database containing curated bioactivity data of more than 2 million FDA-approved compounds, was the source of the initial bioactivity data for the organism of interest. Replicase Polyprotein 1ab in SARS-CoV-2 was used as the target protein. Replicase Polyprotein 1ab is the key polyprotein that is vital for virus replication as it contains the key proteinases responsible for the cleavage of the polyprotein. Christopher Lipinski's Lipinski descriptors (Rule-of-Five or Lipinski's Rule) were used to calculate the molecular descriptors for compounds acquired from Chembl. The dataset generated was then split into two bioactivity classes, active and inactive, by a pIC50 threshold value of 6, and tested for statistical significance using the Mann-Whitney U test with a significance level observed at 0.05 P-Value.

</br></br>

From here, the canonical smiles, which were used to calculate Lipinski's descriptors, were used to calculate PubChem fingerprint descriptors using PaDEL. PaDEL Descriptor is a software for calculating molecular descriptors and fingerprints. PubChem is the world's largest collection of freely accessible chemical information. These descriptors are essentially quantitative descriptions of the compounds in the dataset. The difference between Lipinski's descriptors and PubChem descriptors is that Lipinski's descriptors provide a set of simple molecular descriptors that essentially give us a quick overview of the drug-like properties of the molecule. Basically, compounds that pass the rule-of-five will make good oral drugs. The PubChem fingerprints describe the local features of the molecules. Lipinski's descriptors describe the global features of the molecules, particularly the molecular size, solubility, and also the number of hydrogen bond donors and acceptors. By local features for PubChem, we mean that each molecule will be described by its unique building blocks. The next step after acquiring PubChem fingerprint descriptors was model building. A radom forest regressor was built with the descriptors as the features and the output variable as pIC50 values. Before model building, low variance features were removed from the dataset. Lazy predict was also used to compare different models.It helps you quickly build machine learning models at scale and choose the best suitable model without any parameter tuning.
</div>

# RESULTS AND DISCUSSION
<div style="text-align: justify">
Taking a look at pIC50 values, the actives and inactives displayed a statistically significant difference, which is to be expected since threshold values (IC50 < 1,000 nM = Actives while IC50 > 1,000 nM = Inactives, corresponding to pIC50 > 6 = Actives and pIC50 < 6 = Inactives) were used to define actives and inactives. The LogP and NumHAcceptors showed no difference between actives and inactives among the four Lipinski descriptors (MW, LogP, NumHDonors, and NumHAcceptors), whereas the other two descriptors (MW and NumHDonors) showed a statistically significant difference between actives and inactives. With regards to the models, all their performances were quite bad. No iteration of the process gave a good coefficient of determination, mean square error, or adjusted r-squared values. A comparison of several regression models using lazy prediction also depicted similar behavior. This could be attributed to the small dataset that was used for this experiment, as it has around 110 rows of data. Another factor that could have played a part in the model's performance could have been the outliers that were not dropped.
</div>
  
# CONCLUSION
<div style="text-align: justify">
It is worth noting that this analysis included several outliers for the features (molecular descriptors) examined herein. Therefore, they may have shifted the statistical power of this experiment. Thus, the differences in the EDA part found may be attributed to them. Since the results of this experiment are very critical, the outliers were not dropped. Although outliers do not modify the probability of Type I errors of the Mann-Whitney-Wilcoxon test, they nevertheless increase the probability of Type I errors and reduce power. On the machine learning model part, the conclusion is that the dataset is not enough and it is probable that that hypothesis and the outliers mentioned above were both detrimental to the model's performance. The next step in this experiment was to create a streamlit application and deploy it to Heroku to allow users to make inferences using their own canonical smiles, but due to the model's performance on our dataset and lack of data, this project was abandoned.
</div>
  
# ABBREVIATIONS

1) CDD : Computational Drug Discovery
2) SARS-CoV2: Severe Acute Respiratory Syndrome Coronavirus 2
