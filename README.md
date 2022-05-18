# COVID-19-CDD 

# INTRODUCTION

<div style="text-align: justify">
  This project is a computational drug discovery project which attempted to find a compound or a molecule that will inhibit the function of SARS-CoV2 hence its name, COVID-19-CDD.  
</div>

# METHODS

<div style="text-align: justify">
Chembl Database, a database containing curated bioactivity data of more than 2 million FDA-approved compounds, was the source of the initial bioactivity data for the organism of interest. Replicase Polyprotein 1ab in SARS-CoV-2 was used as the target protein. Replicase Polyprotein 1ab is the key polyprotein that is vital for virus replication as it contains the key proteinases responsible for the cleavages of the polyprotein. Christopher Lipinski's Lipinski descriptors (Rule-of-Five or Lipinski's Rule) were used to calculate the molecular descriptors for compounds acquired from Chembl. The dataset generated was then split into two bioactivity classes, active and inactive, by a pIC50 threshold value of 6, and tested for statistical significance using the Mann-Whitney U test with a significance level observed at 0.05 P-Value.
</div>

# RESULTS AND DISCUSSION

Taking a look at pIC50 values, the actives and inactives displayed statistically significant difference, which is to be expected since threshold values (IC50 < 1,000 nM = Actives while IC50 > 1000 nM = Inactives, corresponding to pIC50 > 6 = Actives and pIC50 < 6 = Inactives) were used to define actives and inactives. Of the 4 Lipinski descriptors (MW, LogP, NumHDonors, and NumHAcceptors), LogP, and NumHAcceptors exhibited no difference between the actives and inactives, while the other two descriptors (MW and NumHDonors) show a statistically significant difference between actives and inactives.

# CONCLUSION

It is worth noting that this analysis included several outliers for the features (molecular descriptors) examined herein. Therefore, they may have shifted the statistical power of this experiment. Thus, the differences found may be attributed to them. Since the results of this experiment are very critical, the outliers were not dropped. Although outliers do not modify the probability of Type I errors of the Mann-Whitney-Wilcoxon test, they nevertheless increase the probability of Type I1 errors and reduce power.

# ABBREVIATIONS

1) CDD : Computational Drug Discovery
2) SARS-CoV2: Severe Acute Respiratory Syndrome Coronavirus 2
