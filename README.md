# NotesOnCPDP
Notes on Cross-Project Defect Prediction

**Cleaning the NASA Dataset**

In their 2016 study, Petrić et al (Petrić, Bowes, Hall, Christianson, & Baddoo) tackled cleaning the NASA dataset by removing instances with improbable or illogical features. For example, they excluded instances where the number of operators was listed as -1, an impossible value. These erroneous values can often be corrected or inferred using related data. For instance, by using the formula N=N1+N2N=N1​+N2​ and knowing the values of NN and N2, one can determine N1, even if it initially appeared incorrect.

 Shepperd and his team also took on the task of refining the NASA dataset. They carefully reviewed it and produced two new versions, D’ and D” (Shepperd, Song, Sun, & Mair, 2013), for research purposes. In these versions, they removed features with constant values (like when all instances in a project have the same value for a feature, say x = 10) and features that were identical across instances (for example, when features x1 and x2 are the same in a project). While this may seem like a good cleanup practice, it can reduce accuracy in Cross-Project Defect Prediction (CPDP). This is because such features might be constant or identical only within a specific project but vary in others. Removing them can lead to the loss of valuable information, particularly since CPDP relies on training data from various projects.

A study by Zhou et al (Zhou et al., 2018) highlighted that nearly half (35 out of 71) of the studies in CPDP research used the NASA dataset. This dataset has multiple versions, each with a different number of records and features. Given the critical importance of data quality in machine learning, it’s essential to compare these datasets to identify the most suitable one for cross-project error prediction.

One significant issue with the NASA dataset is the large number of missing values. Common approaches to handling this include record deletion or imputation. Shepperd and his team opted for record deletion (Shepperd, Song, Sun, & Mair, 2013), but this can result in losing potentially useful information. Imputation, where missing data is predicted using a model, can also introduce errors since the imputed values may not be entirely accurate.

To address missing data, a proxy variable approach can be employed. In this method, a new feature is created for attributes with missing values. For instances with available data, a 0 is assigned to the new feature; for those with missing data, a 1 is assigned. For the missing values in the main attribute, either imputation or a default value of 0 can be used. This method works by creating two models: one for instances where the feature has a value and another for instances where it’s missing. During prediction, the appropriate model is selected based on the available data.

**Corrections Needed for Halstead Metrics Descriptions in NASA Dataset Projects**

In light of the definitions for Halstead metrics provided by Menzies in his article on static code attributes, some descriptions in the NASA dataset projects CM1, JM1, KC1, KC2, and PC1 (PROMISE version) require correction. Below are the necessary adjustments:

Inverse Relationship Between D and L: According to Menzies, the metrics D and L are inverses of each other (D=1/L). However, in line 282 of the mentioned projects, the metric meant to represent Halstead Program Level (L) has been mistakenly labeled as Program Length. This should be corrected to reflect the proper metric.

Formula Adjustment: The formula for Halstead Program Level should be V*/V, not what’s currently written in line 282. Updating this ensures the calculation aligns with the correct definition.

Clarifying L’: Line 284 suggests that L’=1/D. Since L and D are inverses, L’ is effectively the same as the metric L. This relationship should be clarified to avoid confusion.

Missing Metric Name: In line 302, the text references the Halstead Program Length metric but does not explicitly name it. Adding the name will make the description more precise and easier to understand.
