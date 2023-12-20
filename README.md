
# FORECASTING INDIVIDUALS' UPTAKE OF H1N1 AND SEASONAL FLU VACCINES
![](/images/H1N1.jpeg)


## Project Overview
In the early 21st century, global health has been profoundly impacted by emerging viruses and widespread outbreaks. About a decade apart, the World Health Organization declared two major pandemics: the H1N1 influenza in 2009 and COVID-19 starting in 2020. Additionally, outbreaks of non-respiratory viruses like Zika, Chikungunya and Ebola have also commanded global attention. It's clear that viruses will continue to shape infectious disease patterns going forward. Unexpectedly, 2020 was overwhelmed by the COVID-19 pandemic which first arose in Wuhan, China in late 2019. This pandemic is caused by a novel coronavirus, SARS-CoV-2, which leads to severe acute respiratory syndrome (SARS), explaining its SARS classification. Notably, prior warnings suggested coronaviruses could trigger pandemics as evidenced by the 2002-2003 SARS-CoV event and Middle East Respiratory Syndrome emerging in 2012.

In summary, the two major pandemics of this century were prompted by different viruses that shared common traits like enveloped RNA genomes and spherical morphologies. Also remarkable is the frequent genetic shifts these viruses undergo and their broad host ranges. Appreciating the value of unraveling the epidemiology underlying these pandemics and grasping the interplay of people's backgrounds, beliefs, and health behaviors regarding their vaccine choices provides vital perspectives to inform future public health approaches around pandemics.

Gaining clarity on the intricate connections and trends within data, particularly from the lens of data categorization and examination, delivers meaningful perspectives for multiple reasons:

**Historical Context:** By analyzing data from previous pandemics, we can identify patterns and trends that have emerged over time. This can provide a historical context to understand how and why certain populations reacted to vaccination campaigns in specific ways.

**Customized Initiatives:** Recognizing personal immunization tendencies as related to perspectives and backgrounds enables tailored public health efforts. If certain cultural or economic subsets harbor particular worries or misbeliefs around vaccines, interventions could be fashioned to speak to those precise concerns.

**Predictive Worth:** Discernments gleaned from previous data may forecast future conduct. For example, if specific demographic segments persistently displayed vaccine hesitancy during past outbreaks, tailored informational efforts could be crafted for those subsets moving forward.

**Resource Distribution:** Discernments from data grouping may direct effective resource allocation like awareness drives, inoculation sites, or community health workers.

**Stakeholder Partnerships:** Exhibiting comprehension of diverse groups' worries and actions enables public health leaders to cultivate trust and productive community partnerships.

**Historical Backdrop:** Examining data from prior pandemics reveals patterns and tendencies materializing over time. This furnishes historical perspective to comprehend how and why certain groups responded to immunization drives in particular ways.

**Strategy Refinement:** Evaluating previous data may refine future pandemic approaches. By distinguishing effective and ineffective tactics, strategies could be tailored for enhanced future impact.


## Research Questions:
This challenge entails predicting if individuals were inoculated for H1N1 and seasonal influenza based on National 2009 H1N1 Flu Survey data. This constitutes a binary classification dilemma with two possible outcomes: whether the respondent obtained the seasonal vaccine or the H1N1 vaccine.


**DATA SOURCE:** DrivenData. (2020). Flu Shot Learning: Predict H1N1 and Seasonal Flu Vaccines. Retrieved [10 /17/2023] from https://www.drivendata.org/competitions/66/flu-shot-learning.

## Data Exploration
Two data sets were merged
features_df

contains information about the respondents, such as their level of concern about the H1N1 virus, knowledge about H1N1, behavioral habits, and demographic details. 

labels_df

provides the target variables for each respondent, indicating whether they received the H1N1 vaccine (h1n1_vaccine) and the seasonal vaccine (seasonal_vaccine).

## MISSING VALUES AND DUPLICATES

From our merged data set we have no duplicates

Multiple columns have absent data. The categories employment_occupation, employment_industry, and health_insurance especially exhibit considerable missing percentages at 50.44%, 49.91%, and 45.96% respectively. To address this, potential techniques include:

For categorical factors: Substitute missing points with the modal value or generate a label like "Unknown" or "Not Provided".

For numerical elements: Replace with the mean, median, or a placeholder. Apply a model such as KNN to estimate missing content.

## Visualising categorical data
![](/images/h1%20concern%20and%20knowledge.png)


![](/images/behavioral.png)



Observation: Most respondents demonstrate moderate concern (Level 2) regarding H1N1. The count with high apprehension (Level 3) is slightly under those with moderate unease. Fewer participants express low anxiety or none (Levels 0 and 1) about H1N1.

H1N1 Understanding: Most respondents have moderate comprehension (Level 2). Numerous display high grasp (Level 1). Few exhibit no insight (Level 0).

Antiviral Medication Use: Majority did not take antivirals.

Health Coverage: Many have insurance, but a substantial portion lack it.

Perceived H1N1 Risk Without Vaccine: Numerous view moderate illness risk without immunization. Fewer see high risk, while some believe low risk or are uncertain.

## Bivariate analysis for h1n1_concern', 'h1n1_knowledge', 'behavioral_antiviral_meds', 'health_insurance', 'opinion_h1n1_risk'


## Bivariate analysis for Age Group, Education, Income Poverty, Race and Sex
![](/images/age.png)

![](/images/agegroup.png)

![](/images/antiviral.png)

![](/images/agegroup.png)

## CORRELATION ANALYSIS

![](/images/contingency.png)

H1N1 Vaccine Correlations:

Doctor H1N1 recommendations (doctor_recc_h1n1) have the highest positive association with H1N1 immunization. This implies greater inclination to get vaccinated if a healthcare provider endorses it. Perceived H1N1 vaccine risk, efficacy, and side effect opinions (opinion_h1n1_risk, opinion_h1n1_vacc_effective, opinion_h1n1_sick_from_vacc) also exhibit notable correlations.

Seasonal Vaccine Correlations:

Respondent age group (age_group) has a robust positive correlation with seasonal vaccine uptake. Doctor guidance and perspectives on seasonal vaccine risk and efficacy are also substantially correlated. Interestingly, h1n1_vaccine correlates with the seasonal vaccine too, affirming our earlier observation that the two are interdependent.
## MODELLING
## FIRST MODEL: LOGISTIC REGRESSION
The model shows commendable performance for both vaccines, though it could benefit from enhancements, particularly in improving the recall for h1n1_vaccine. The current lower recall suggests the model may not be identifying a considerable number of individuals who did receive the H1N1 vaccine. For the seasonal_vaccine, the performance metrics are more evenly distributed, with precision and recall both around the mid-70s. This balance offers a well-rounded perspective on the model's overall effectiveness.

![](/images/class%20imbalance.png)

## SECOND MODEL: LOGISTIC REGRESSION AFTER HANDLING CLASS IMBALANCE h1n1_vaccine
![](/images/logreg%20confusion.png)

![](/images/logreg%20roc.png)



After implementing SMOTE, the model shows a slight decrease in overall accuracy compared to its performance on the initially imbalanced dataset. However, the recall for Class 1 (those who received the vaccine) has significantly improved, rising from 43% in the original to 72% in the SMOTE-enhanced model. This indicates an enhanced ability of the model to correctly identify individuals who were vaccinated.

A consequence of this improvement is a reduction in precision for Class 1, now at 49%. This lower precision reflects an increase in false positive predictions (wrongly indicating vaccination), a trade-off for the model's improved detection of true positives (accurately identifying vaccination).

This scenario underscores the effectiveness of addressing class imbalances in data modeling.

## THIRD MODEL: RANDOM FOREST CLASSIFIER

![](/images/rf%20confusion.png)

![](/images/rf%20roc.png)


The accuracy of the model in identifying those who did not get the H1N1 vaccine (Class 0) is notably high, marked by superior precision, recall, and F1-score metrics. Conversely, for those who did receive the vaccine (Class 1), the model shows adequate precision but a lower recall. This suggests a considerable presence of false negatives, where individuals who were vaccinated are incorrectly predicted as unvaccinated. This issue is highlighted by the Class 1 F1-score being only 53%, indicating a need for a better balance between precision and recall for this particular class.

## Final Model (Gradient Booster Classifier)
![](/images/gb%20confusion.png)

![](/images/gb%20roc.png)


The model exhibits a commendable performance for H1N1 Flu predictions, achieving an 84% accuracy rate. Its strength lies more in correctly identifying cases where the flu vaccine wasn't taken (true negatives) rather than in cases where it was taken (true positives).

For Seasonal Flu predictions, the model's accuracy drops to 63%. It excels at pinpointing instances where individuals did not receive the vaccine (indicating a high recall for the negative class) but shows considerable difficulty in accurately identifying those who did get vaccinated (evidenced by a low recall for the positive class).

In both scenarios, the model demonstrates a tendency to favor predictions of the negative class (no vaccination), as reflected by the higher recall rates for class 0 in both H1N1 and Seasonal Flu models.
## RESULTS AND CONCLUSIONS
### Predict probabilities and plot their distribution
![](/images//probabilities.png)

![](/images/comparison.png)

H1N1 Flu:

Overall, for predicting h1n1_vaccine, all three models offer competitive performance, with slight variations in precision, recall, and F1-score.

For predicting seasonal_vaccine, while Gradient Boosting offers the highest precision, its recall is significantly lower than that of Logistic Regression and Random Forest, leading to a much lower F1-score and overall accuracy.

## RECOMMENDATIONS
**Public Awareness and Education:**
H1N1 Concern & Knowledge: A significant portion of the survey respondents display moderate to high levels of concern and knowledge regarding H1N1. This indicates a certain effectiveness of public awareness campaigns, yet highlights the need for further efforts. Strategies should be designed to:

1. Address and inform individuals with moderate to high levels of concern to ensure they receive accurate information.
2. Reach out to those with low or no awareness, enhancing their understanding and awareness.

**Education Level:**

Higher vaccination rates are observed in individuals with advanced education. It's crucial to direct educational campaigns towards those with lower educational levels, using formats that are both accessible and comprehensible.

Income and Poverty: Focused campaigns in high-poverty regions are essential, potentially integrating free vaccination services or subsidies, to promote vaccination among these populations.

**Health Infrastructure and Support:**

Health Insurance: A notable portion of respondents lack health insurance. Policymakers need to focus on expanding access to affordable health insurance, which may indirectly boost vaccination rates and overall health.

**Targeted Interventions:**

Race: There is a clear discrepancy in vaccination rates across different racial groups. Customized interventions and awareness programs are needed to address unique challenges and barriers encountered by racial groups with lower vaccination rates.
Sex: Although the difference is marginal, it's important to ensure that both men and women equally receive information and access to vaccination services.
