---
title: Healthcare-Based Machine Learning
date: 2022-05-28T00:09:00-06:00
draft: false
projects: artificialintelligence
featuredImage: /images/health.png

---

## Prediction of Bodyfat using a Linear Regression Model and Body Measurements
**Abstract**

Bodyfat percentage is an important estimator for health. The most accurate method for measuring bodyfat is by underwater weighing which is time-intensive. Predictive analytics (linear regression) using indirect measurements offer a faster method to compute bodyfat percentage. This study analyzes bodyfat data determined by underwater weighing with their corresponding indirect measurements. To predict the bodyfat using these measurements, we compare a traditional linear model, regularized model, subset models (indicator, dichotomous, piecewise, polynomial), and feature engineering models (principal components analysis). The correlation coefficients (R^2^) are analyzed for each ten-fold cross-validated model. The best R^2^ value (0.67) is found with a traditional linear model, keeping as much information as possible.

See my [report](/docs/saraogee-research-report1-2.pdf) <i class="fa-solid fa-arrow-up-right-from-square"></i> and [Jupyter notebook](/docs/Assignment1.html) <i class="fa-solid fa-arrow-up-right-from-square"></i> for further details. 

## Prediction of Heart Disease using a Logistic Regression Model based on Framingham Heart Study
**Abstract**

Heart disease is one of the leading causes of mortality among people across the world. Different demographic, behavioral and physiological factors are studied as indicators for coronary heart disease in the Framingham Heart Study (FHS). Predictive classification models can help in the early detection of heart disease as well as inform lifestyle prevention techniques at an affordable cost. This study analyzes 3658 observations of 16 variables from the FHS using a binary classification logistic regression model. Subset models for males and females are evaluated using ten-fold cross-validation with receiver operator characteristic area  under the curve (AUC ROC) scores of 0.65 and 0.67 respectively.

See my [report](/docs/saraogee-research-report2.pdf) <i class="fa-solid fa-arrow-up-right-from-square"></i> and [Jupyter notebook](/docs/Assignment2.html) <i class="fa-solid fa-arrow-up-right-from-square"></i> for further details.

## Prediction of Diabetes using Classification Models based on Pima Indians study
**Abstract**

Diabetes is a chronic health condition that is a significant contributor to the worldwide healthcare burden. The healthcare burden can be drastically reduced with precise early detection and preventative measures. Predictive analytics (tree-based methods) using medical measurements including glucose level and others offer a useful method to diagnose diabetes early. This study analyzes a dataset of female individuals of Pima Indian heritage near Phoenix, Arizona with a high incidence of diabetes. To predict the diagnosis of diabetes using these measurements, we compare traditional logistic regression classification models with and without interactions and tree-based
classification methods such as random forest. The areas under the receiver operating characteristic curve (ROC AUC) is analyzed for each five-fold cross-validated model. The best ROC AUC of 0.84 is found using random forest model which naturally takes interactions into account.

See my [report](/docs/saraogee-research-report3.pdf) <i class="fa-solid fa-arrow-up-right-from-square"></i> and [Jupyter notebook](/docs/Assignment3.html) <i class="fa-solid fa-arrow-up-right-from-square"></i> for further details. 

## References

Andersson, Charlotte, Andrew D. Johnson, Emelia J. Benjamin, Daniel Levy, and Ramachandran S. Vasan. 2019. “70-Year Legacy of the Framingham Heart Study.” Nature Reviews Cardiology 2019 16:11 16 (11): 687–98. https://doi.org/10.1038/s41569-019-0202-5.

Smith, Jack W, J E Everhart, W C Dicksont, W C Knowler, and R S Johannes. 1988. “Using the ADAP Learning Algorithm to Forecast the Onset of Diabetes Mellitus.” https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2245318/pdf/procascamc00018-0276.pdf.

Miller, Tom. "Machine Learning Foundations: Bodyfat". MSDS 422: Practical Machine Learning. Course at Northwestern University, Chicago, IL, April 24, 2022.

Miller, Tom. "Regression and Classfication: Framingham". MSDS 422: Practical Machine Learning. Course at Northwestern University, Chicago, IL, April 30, 2022.

Miller, Tom. "Tree-structured Models: Pima Indians". MSDS 422: Practical Machine Learning. Course at Northwestern University, Chicago, IL, April 30, 2022.

Penrose, Keith W, Arnold G Nelson, and Arnold Garth Fisher. 1985. “Generalized Body Composition Prediction Equations for Men Using Simple Measurement Techniques.” Medicine and Science in Sports and Exercise 17: 189. https://doi.org/10.1249/00005768-198504000-00037.