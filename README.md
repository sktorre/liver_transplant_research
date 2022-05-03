# Predicting Short-term Outcomes of Liver Transplants with an
Emphasis on the role of Body Composition


*Does body composition play a role in liver transplant outcomes?*

Below is a summary of this project, but a full report can be found [here](https://github.com/sktorre/liver_transplant_research/blob/main/Deliverables/predicting_liver_transplant_outcomes.docx).

## Purpose: 

The purpose of this research is to understand how body composition effects short-term outcomes of liver transplants through predicting the status of patients for 90 days post-liver transplant. 

Two different methods were used to perform this analysis: one of a statistical nature (proportional odds regression) and one pertaining to machine learning (neural networks). A secondary interest of this work was to compare and contrast these two methods to understand which might be better at tackling different components of the problem. 

## Background

Patients with end-stage liver disease require liver transplant surgery from a living or deceased donor. As this is a very serious condition, outcomes can include infections, complications and even death. Most patients spend a few days in the ICU, around a week in the hospital and possibly even time in an inpatient rehabilitation facility post-liver transplant. Being able to predict the outcome status and journey of a liver transplant patient can help with resourcing and reducing costs. Further understanding what factors are associated with liver transplant outcomes can assist in patient recovery and preventative care to decrease the need of liver transplant surgery. 

## Data

The data set used for this research was collected from 422 adult patients who underwent liver transplant surgery between 2009-2019 at Vanderbilt University Medical Center. The original dataset includes 140 variables including demographic information, pre-transplant and post-transplant comorbidities, surgical variables, and outcome information including days in various statuses, infections and mortality. Additionally, pre-transplant and post-transplant follow up CT scans were taken and analyzed for measures of body composition. Some patients have follow-up CT scans for up to 10 years, but many have only a few years of follow-up. It is important to note that the dates of liver transplants span from 01/09/2009 – 12/23/2018 while follow-up data was continued to be collected until summer 2021. As short-term outcomes were the focus of this analysis, many follow up measurements from annual checkups were not included in this work.

A data dictionary can be found [here](https://github.com/sktorre/liver_transplant_research/blob/main/Data%20Dictionary.docx)

Notes: All data is saved privately on Box as is not publicaly available.

## Methods

Two models were fit, a portportional odds model and a neural network. There are pros and cons to each of the models and the combination of the two approaches provides for a robust analysis of short-term outcomes of liver transplants based on many factors but more specifically body composition. As mentioned before, the outcome status is ordinal with 4 levels, 0: home/IPR, 1: Hospital, 2: ICU/Vent, 3: Dead. Because the difference between being at home/IPR and being Dead is much different from either being at home/IPR and being in the hospital, the models must account for ordinality and be able to factor in these levels of differences in categories in assessing model performance. Additionally, as the outcome is not a single value for each patient, but a predicted status outcome for each of the 90 days post-liver transplant, the models must be able to handle the dimensions of time, previous day state and intra-patient correlation between observations for the same patient.

The data processing, data reduction and proportional odds model can be found [here](https://github.com/sktorre/liver_transplant_research/blob/main/Analysis/05_liver_transplant_analysis.html) as well as the raw code [here](https://github.com/sktorre/liver_transplant_research/blob/main/Analysis/05_liver_transplant_analysis.Rmd).

The code for the neural network can be found [here](https://github.com/sktorre/liver_transplant_research/blob/main/Analysis/05_modeling_nn.ipynb).

## Results

The proportional odds model has an adjusted R2 value of 0.913 and a χ2 equal to 31314.66. The rank discrimination index ρ has a value of 0.576. The figure below shows feature importance from this model.

<img width="226" alt="image" src="https://user-images.githubusercontent.com/69755309/166525959-7cd333c6-d2cd-427a-a370-81ee03068cfe.png">

The neural network has an accuracy of 97.77%, a mean absolute error of 0.023 and a root mean squared error of 0.16. 

<img width="280" alt="image" src="https://user-images.githubusercontent.com/69755309/166526094-0625f14c-0947-4299-924d-0341f69f38e6.png">

## References

1.	Mayo Foundation for Medical Education and Research. (2021, June 2). Liver transplant. Mayo Clinic. Retrieved April 15, 2022, from https://www.mayoclinic.org/tests-procedures/liver-transplant/about/pac-20384842. 
2.	Hegyi PJ, Soós A, Hegyi P, Szakács Z, Hanák L, Váncsa S, Ocskay K, Pétervári E, Balaskó M, Eröss B, Pár G. Pre-transplant Sarcopenic Obesity Worsens the Survival After Liver Transplantation: A Meta-Analysis and a Systematic Review. Front Med (Lausanne). 2020 Dec 16;7:599434. doi: 10.3389/fmed.2020.599434. PMID: 33392221; PMCID: PMC7772841.
3.	Kuo SZ, Ahmad M, Dunn MA, Montano-Loza AJ, Carey EJ, Lin S, Moghe A, Chen HW, Ebadi M, Lai JC. Sarcopenia Predicts Post-transplant Mortality in Acutely Ill Men Undergoing Urgent Evaluation and Liver Transplantation. Transplantation. 2019 Nov;103(11):2312-2317. doi: 10.1097/TP.0000000000002741. PMID: 30985575; PMCID: PMC6783339.
4.	Irwin NEA, Fabian J, Hari KR, Lorentz L, Mahomed A, Botha JF. Myosteatosis, the More Significant Predictor of Outcome: An Analysis of the Impact of Myosteatosis, Sarcopenia, and Sarcopenic Obesity on Liver Transplant Outcomes in Johannesburg, South Africa. Exp Clin Transplant. 2021 Sep;19(9):948-955. doi: 10.6002/ect.2021.0083. Epub 2021 Aug 9. PMID: https://github.com/ck3734387151.
5.	T.A. Williams, K.M. Ho, G.J. Dobb, J.C. Finn, M. Knuiman, S.A.R. Webb, Effect of length of stay in intensive care unit on hospital and long-term mortality of critically ill adult patients, British Journal of Anaesthesia, Volume 104, Issue 4, 2010, Pages 459-464, ISSN 0007-0912, https://doi.org/10.1093/bja/aeq025.
6.	Harrell, F. E., Jr. (2016). Regression modeling strategies. Springer International Publishing.
7.	Harrell, F. E., Jr.  (2022, March 9). Assessing the Proportional Odds Assumption and Its Impact. Assessing the proportional odds assumption and its impact. Retrieved April 15, 2022, from https://www.fharrell.com/post/impactpo.
8.	Harrell, F. E. (2021, February 27). Longitudinal Ordinal Analysis for Violet2. Longitudinal ordinal analysis for Violet2. Retrieved April 15, 2022, from http://hbiostat.org/proj/covid19/violet2.html#gee-type-proportional-odds-modeling. 
9.	Cao, W., Mirjalili, V., & Raschka, S. (2019). Rank-consistent ordinal regression for neural networks. arXiv preprint arXiv:1901.07884, 6.
10.	Kennedy, C. (2022) Ordinal regression in Tensorflow Keras, Git-Hub repository, https://github.com/ck37/coral-ordinal.


## Acknowledgements

I could not have completed this project without the help of some amazing individuals. I would first like to thank my academic advisor Dr. Heidi Silver for not only providing me access to this data set and problem, but also assisting me along the way with domain knowledge insights on how the data was collected, what type of similar research has already been done in this field and hypotheses on how variables might interact. I would also like to thank Chiara Di Gravio for her extensive statistical knowledge, consistent support and patience through all my questions. Additionally, I would like to acknowledge Dr. Frank Harrell for pushing me throughout his class and empowering me to explore ordinal longitudinal data outcomes through proportional odds models. Finally, I would like to thank Dr. Jesse Blocher and all faculty and peers at the DSI for helping me grow as a data scientist over the last couple of years.

