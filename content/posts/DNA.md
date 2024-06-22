---
title: Machine Learning with DNA
date: 2022-05-10T00:09:00-06:00
draft: false
projects: biomolecules
featuredImage: /images/dna.png

---

## Predicting Colon Cancer Using Clustering Models based on DNA Microarray Data
**Abstract**

Colon cancer is a significant public health concern and leading cause of death in the older human population. The healthcare burden can be significantly reduced with earlier detection and preventative measures. Although genetic information has been shown to be altered in the early stage of the disease, DNA sequencing data is highly dimensional and must be analyzed using predictive algorithms. This study analyzes a DNA microarray dataset of 62 tissue samples (normal and cancerous) and 92 genes from the **Princeton University Gene Expression Project**. To analyze the dataset, the Rand index was compared for clustering models based on DBSCAN, kmeans and hierarchal clustering algorithms (single and ward). The kmeans model performed the best clustering of the data and had the highest Rand index of 0.796.

See my [report](/docs/saraogee-research-report4.pdf) <i class="fa-solid fa-arrow-up-right-from-square"></i> and [Jupyter notebook](/docs/Assignment4.html) <i class="fa-solid fa-arrow-up-right-from-square"></i> for further details. 

## Classification Models for Gene Families based on DNA Sequencing
**Abstract**

The volume of DNA sequencing data has been growing at an unprecedented pace. Predictive algorithms can help leverage this data for useful applications such as gene family classification by using new sequencing data. This study analyzes a dataset for protein coding DNA
sequences of 7 different gene families across three different species – **human, chimpanzee and dog**. Naïve Bayes, random forest, convolutional neural networks and recurrent neural networks were used to classify each gene family with a k-mer count encoding. The Naïve Bayes classifier performed the best on the holdout test dataset with F-1 scores of 0.982, 0.993 and 0.983 for human, chimpanzee and dog respectively. Overfitting was seen with the other models used in the study.

See my [report](/docs/saraogee-research-report6.pdf) <i class="fa-solid fa-arrow-up-right-from-square"></i> and [Jupyter notebook](/docs/Assignment6.html) <i class="fa-solid fa-arrow-up-right-from-square"></i> for further details. 

## References

Miller, Tom. "DNA Microarray Data". MSDS 422: Practical Machine Learning. Course at Northwestern University, Chicago, IL, May 20, 2022.

Miller, Tom. "DNA Sequencing". MSDS 422: Practical Machine Learning. Course at Northwestern University, Chicago, IL, May 20, 2022.
