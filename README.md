A study into the impact of advertising restrictions on food consumption 

Andrei Sandu 791981- Chiara Barontini 807411– Yanheng Li E04708 

  1. Problem

     Concerns about public health, particularly the link between obesity and food marketing, have been 
growing. Children are especially susceptible to developing unhealthy eating habits influenced by TV and digital 
platforms, which contribute to obesity. Our evaluation focuses on the UK’s efforts to tackle this issue. The 
Office of Communications (OFCOM) oversees TV and radio advertising policies in the UK. Between 2007 
and 2009, OFCOM introduced new restrictions on advertising foods high in fat, salt, and sugar (HFSS) to 
children aged 4 to 15. According to the Advertising Standards Authority, compliance with these restrictions 
was high, reaching about 98% during the designated times and channels. The primary goal of the policy was 
to limit young children’s exposure to unhealthy food advertising and reduce their consumption of such products. 
Our project examines whether these restrictions were effective and how the policy impacted children’s 
unhealthy food consumption.

  2. Data

     The data used in this project is secondary data sourced from the Expenditure and Food Survey (EFS). 
It was gathered from a sample of UK households over a span of 12 years, with an effort to track the same 
families each year (longitudinal data). The dataset includes self-reported purchases of HFSS foods recorded 
over two weeks. It comprises 29 variables and 74,117 observations. Key variables of interest include:  
• q_conf: Quantity of confectionery (chocolate, sweets) consumed in 2 weeks (numeric).  
• p_conf: Price of confectionery products in pounds (numeric).  
• OFCOM: Binary treatment variable, which takes value 0 before 2007 and 1 after 2007 (numeric). 
• age (num, [16,90]), child (factor), educ (num), male (factor), married (factor), income (num). 
The dataset included quantities of confectionery, soft drinks, and snacks, respectively, but our analysis 
primarily focused on confectionery due to its more comprehensive data. To account for consumption, we 
created a new variable by multiplying the quantity of confectionery by its respective price. Our study aimed to 
evaluate the policy’s impact on unhealthy food consumption. So, our response variable is the consumption of 
confectionery, while the main predictor is the treatment variable (OFCOM) and its interaction with the binary 
variable child.

  3. Method

     The method focuses on exploring the policy’s impact by regression analysis. Combining 
exploratory data analysis, we first use the OFCOM binary variable to express “post” (OFCOM=1) and before 
(OFCOM=0) the policy and extract observations aged 16-45 with children (child=1) as treatment group 
(treated=1). Then, we regress log_consumption on selected variables along with the interaction term (post × 
treated). The coefficient of the “treated” term reflects the difference between treatment and control groups in 
consumption, while the interaction coefficient measures the effect in the treatment group of the policy, and the 
coefficient of “post” measures the total difference before and after the policy. Correlated variables are added 
to the model as covariates.

  4. Implementation:

     4.1Data Exploration: The data exploration section of this report aims to investigate the structure of the data 
and identify key characteristics within the sample. This is achieved through correlation matrices, visualizations 
and summary statistics. To better understand our data set, it is crucial to understand the characteristics that 
define the individuals in our sample. To do so, we evaluated the age distribution of the households within the 
data. Figure A3 showcases said age distribution through a Kernel Density plot. What we can observe from the 
Figure is a concentration of density in the 30-50 age range, peaking around the middle of this range, indicating 
that most individuals in the sample are adults of working age. The left tail of the distribution indicates a smaller 
proportion of the sample is comprised of individuals under the age of 20, whilst the right tail of the distribution 
showcases a great spike in individuals older than 75. To further examine the variables in the data set, we 
conducted a correlation analysis. A correlation analysis is appropriate as it allows for exploration of the 
relationship between the variables as well as for detecting any potential presence of multicollinearity in the 
sample, which might affect the credibility of the regression. Figure 2 presents the results of the correlation 
analysis. A strong positive correlation between education and income showcases how higher level of education 
has a positive impact on household income. A very strong correlation between year and OFCOM is also present, 
this was to be expected as OFCOM was introduced in 2007, meaning a portion of observations in 2007 and all 
observations post 2007 include OFCOM = 1. Figure A4 presents statistics on the distribution of OFCOM 
observations, where 55.8% of observations in the sample are Non-OFCOM observations, with the other 44.2% 
being OFCOM observations. An interesting observation in Figure A4 is the very strong negative correlation 
between age and education. This value suggests the presence of generational differences in access to formal 
education among individuals in the sample. Overall, besides the presence of the aforementioned correlations, 
which were to be expected, the correlation matrix did not identify other anomalies which would potentially 
jeopardize the reliability of our data.
4.2Regression Analysis: This analysis evaluates the impact of policy implementation on log-transformed 
consumption (log_consumption) while controlling demographic and economic variables. Firstly, rows where 
the dependent variable consumption equals 0 were removed to avoid biases caused by extreme outliers. The 
variable consumption was log-transformed (log_consumption) to stabilize variance and meet regression 
assumptions. Secondly, the treatment group (treated=1) is extracted corresponding to observations aged 16-45 
with children (child=1), setting the remaining ones as control groups. Thirdly, a linear regression model was 
fitted to the entire dataset to evaluate the effects in the treatment group of the policy implementation (treated: 
post) on log_consumption. The model also includes “treated” (captures overall difference between groups), 
“post” (captures overall difference before and after policies). And in the big model, we also fixed demographic 
and economic factors, e.g. age, education (years), gender (male), marital status and income, to achieve a more 
convincing inference. Additionally, a QQ plot (Appendix Figure A1) of residuals in the big model was 
generated to evaluate their normality, which validates the effectiveness of the regression. All regression results 
are manifested in figure 1, which is generated by LaTex. Considering the large number of observations (68401), 
we set the p-value 0.05, 0.01 and 0.001 to be noted. The overall running time could be less than 1 minute. 
Figure 1: Difference in Difference Regression Results.  <img width="493" height="477" alt="image" src="https://github.com/user-attachments/assets/790318d0-e798-497f-8895-54361bbfe8ce" />
                                
Figure 2: Variable Correlation Matrix. <img width="489" height="475" alt="image" src="https://github.com/user-attachments/assets/df100768-9272-4ea1-977a-086f7e0a6284" />


                                    
  5. Evaluation:

     a) R-squared: In this analysis, the adjusted R^2 values are 0.019 and 0.116 for the first and second models, 
respectively. The higher adjusted R^2 of the second model indicates that the expanded version, which includes 
more predictors, provides a better fit to the data. While these values are low, it is essential to note that in 
inference-focused studies, the primary goal is to understand the relationships between variables rather than to 
achieve high predictive accuracy.  
b) F-Statistics and P-Values: Most coefficients are significant at the 5% level, except for the "Male" 
coefficient in the second model, which is not statistically significant. The key Difference-in-Differences (DiD) 
estimate, represented by the coefficient of the interaction term ("treated × post"), is approximately -0.04 in both 
models. This suggests that the policy led to a 4% reduction in food consumption for families with children. 
Although the effect is statistically significant at the 5% level, it is relatively small, implying limited practical 
impact despite statistical validity. The F-statistic tests the null hypothesis that all regression coefficients (except 
the intercept) are equal to zero. With F-statistics of 433.870 and 1,125.213, both models are highly statistically 
significant overall, with the second model demonstrating a stronger fit. 
c) Cohen’s D and Independent T-Test: An independent T-test was conducted to compare the post-policy log
transformed consumption between the treated and control groups. The results revealed a statistically significant 
difference (t (9,660) =11.406, p <2.2×10^−16), with the treated group exhibiting a higher mean log
consumption (M=9.121) compared to the control group (M=8.842). The 95% confidence interval for the 
difference in means [0.231, 0.327] does not include zero, further confirming the significance of this difference. 
When transformed back to the original scale, the treated group consumed approximately 32.2% more than the 
control group on average. These findings highlight a statistically significant and meaningful difference in 
consumption levels between the two groups during the post-policy period. As measured by Cohen's D, the 
effect size of the difference in post-policy log consumption between the treated and control groups was 
estimated at 0.273 (95% CI: [0.226, 0.320]). According to Cohen's conventions, this represents a small effect 
size (d=0.2: small, d=0.5: medium, d=0.8: large). The confidence interval does not include zero, reinforcing 
the presence of a statistically significant difference. However, the small effect size suggests that, while the 
treated group consumed more than the control group post-policy, the magnitude of the difference is modest in 
practical terms. It is important to note that Cohen’s D reflects the average post-policy difference in log 
consumption between the two groups at a specific point in time. It does not account for changes over time or 
the causal effect of the policy. Thus, while Cohen’s D quantifies the magnitude of the observed post-policy 
difference, it does not isolate the policy’s impact, which is better captured by the DiD analysis. 
d) Parallel Trends Analysis: To validate the parallel trends assumption, a critical requirement for DiD analysis, 
we focused on the period from 2002 to 2008. Our analysis revealed that mean consumption trends for the 
control and treated groups were stable and closely aligned prior to 2007 (see Figure A2). This observation 
supports the assumption that any post-2007 differences in the treated group relative to the control group can 
reasonably be attributed to the policy implementation, allowing us to proceed with the DiD analysis with 
confidence.

  6. Interpretation:

     Our research suggests that the Ofcom policy, aimed at reducing children's exposure to and consumption of 
unhealthy foods through advertising restrictions, was not remarkably effective. The data indicates that 
consumption habits remained essentially unchanged; only a 4% decrease at 0.05 significant level was registered. 
This implies that advertising may not be the most influential factor in children’s dietary choices. Future policies 
could benefit from a more focused approach, such as direct school interventions, which could substantially 
impact children’s eating habits and health. The coefficient of “treated” indicates a significant overall difference 
between treatment group and control group, and the estimator of “post” shows a generally increasing 
consumption over the years. While the T-test and Cohen’s D indicate that treated families consumed more than 
control families post-policy, which is consistent with the estimator of “treated.” The DiD analysis suggests that 
the policy caused a relative reduction in log-consumption for treated families compared to their pre-policy 
trend. These results can coexist: the treated group may have higher absolute consumption, but the policy 
mitigated their consumption growth relative to the control group.

7. Appendix 
Figure A1: QQ plot for Overall Regression <img width="564" height="482" alt="image" src="https://github.com/user-attachments/assets/d03c1b2a-80cf-42cf-b5f1-f423a7836804" />

Figure A2: Parallel trend  <img width="953" height="386" alt="image" src="https://github.com/user-attachments/assets/c8e0e5fe-862c-4859-9c4d-72a782bf438c" />

Figure A3: Age Distribution <img width="563" height="603" alt="image" src="https://github.com/user-attachments/assets/2edc2f4c-ef3d-457b-bfda-c2fac4b5b572" />

Figure A4: Percentage of OFCOM and Non-OFCOM observations <img width="643" height="656" alt="image" src="https://github.com/user-attachments/assets/12589c75-6066-46fa-935d-b8bb1288f9d9" />

8. References: 
Adams, Jean, et al. “Effect of Restrictions on Television Food Advertising to Children on Exposure to 
Advertisements for ‘Less Healthy’ Foods: Repeat Cross-Sectional Study.” PLOS ONE, vol. e31578, no. 2, 15 
Feb. 2012.  
Boyland, Emma, et al. “The Extent of Food Advertising to Children on UK Television in 2008.” Pediatric 
Obesity, vol. 455–461, no. 5–6, 1 Oct. 2011.  
“Regulation of Advertising for Less Healthy Food and Drink.” www.ofcom.org.uk, Ofcom, 2023, 
www.ofcom.org.uk/__data/assets/pdf_file/0016/264013/Regulation-of-advertising-for less-healthy-food-and
drink.pdf.  
“Television Advertising of Food and Drink Products to Children.” www.ofcom.org.uk, Ofcom, 2006.
