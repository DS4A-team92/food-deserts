<h1 align="center">TALE OF TWO CITIES</h1>

<p align="center">
<img src="https://github.com/DS4A-team92/food-deserts/blob/main/references/images/food-desert-cir-3.png"></img>
</p>

<h4 align="center">ANALYSIS OF FOOD ACCESS & ASSOCIATED FACTORS IN COOK COUNTY, ILLINOIS</h4>
<div align="center" style="padding: 10px">
	<a style="padding: 10px; text-decoration: none" href="https://foodaccessexplorer.weebly.com/"> Dashboard </a>
	<a style="padding: 20px; text-decoration: none" href="https://drive.google.com/file/d/1FGcx0UshepKNWd5-axSaMNf0Vc0jEn0V/view?usp=sharing">Datafolio</a>
	<a style="padding: 10px; text-decoration: none" href="https://voicethread.com/myvoice/thread/18127453">Pressentation</a>
	<a style="padding: 10px; text-decoration: none" href="https://www.canva.com/design/DAEj2YL2cgE/Khqs7uOOaWtwxBzyFiCICA/view?utm_content=DAEj2YL2cgE&utm_campaign=designshare&utm_medium=link&utm_source=sharebutton#2">Final-Report</a>
</div>
------------
------------

Problem statement
------------
Our team sort out to identify areas with low access to healthy food using metrics other than only income, vehicle ownership, and distance to the nearest grocery store that the USDA defines by including characteristics including social determinants of health. 

Local government and community organizations can use this information to determine additional areas in need of food access assistance outside of the USDA's somewhat ambiguous definition.

This problem is important, because Food Accessibility is a persistent issue across low-income communities. Food deserts affect 23.5 million people, and many residents are reliant upon public transportation, which is difficult to navigate toting around bags of groceries, so they make do with what’s available near them. 

The FDA/USDA definition of a food desert is rooted in metrics that may be leaving some of the most vulnerable members of a community out. While income and distance to a supermarket are important features of defining a food desert, food insecurity provides a lens through which we can expand food accessibility issues while including individuals/communities who may have been previously left out. Revisiting the idea/concept of food deserts by exploring key attributes associated with low access to healthy food is critical to identify areas of most need and in turn equip stakeholders with the knowledge of where to focus efforts on providing healthy, accessible food options.


Key Findings
------------
* Our EDA revealed how relationaships between features and mRFEI changed depending on whether census tracts where classified as low income or not
* Associations between low access to food, demographics and health-related outcomes are often income-stratified
* Models performance for predicting categories of healthy food access increased when income-stratified

Tools/Resources used
------------
* Jupyter notebook as our IDE
* Tableau for creating dashboard 
* Canva for our final report
* Voicethread for our presentation
* Python Liberies for data cleaning and analysis

EDA
----
Through our Exploratory Data Analysis (EDA), our team sought to explore potential relationships between our identified variables of interest, including health outcomes, with access to healthy food in Cook County, which includes the city of Chicago. We were also interested in exploring the differences in access to healthy food and health outcomes in highly segregated neighborhoods. While previous studies have looked at some health outcome disparities in Chicago, such as asthma, obesity, and mental health [5: interactive associated with 4], our team wanted to expand on these findings to include not only a wider range of health outcomes, but also other aspects that could affect health, such as potential patterns underlying access to and utilization of health care.

#### Modified Retail Food Environment Index (mRFEI)

Utilizing the modified Retail Food Index(mRFEI) dataset, our team created a visualized map of census tracts within Cook County with corresponding colors indicating access to healthy food retailers. Lower scores are indicative that a census tract contains many convenience stores and fast food restaurants in comparison to the number of healthy food retailers. A zero score indicates no healthy food retailers (grocery stores or supermarkets) within the census tract.

#### Income and mRFEI

An initial finding among the characteristics of the census tracts was the relationships of the Median Income and Proportion of the Census Tracts Living in Poverty to mRFEI. There appears to be a relationship between mRFEI and income, as median income of the census tract increases the mRFEI value increases, conversely as the proportion of those in a census tract that live in poverty increases the mRFEI values decreases. The visualization displays tracts with no healthy food options (mRFEI value of 0) are concentrated around lower median income values, where the concentration in the other plot is around tracts with lower proportions of those living in poverty. This may suggest that median income alone may not account for census tracts with lower mRFEI values. 

Statistical analysis visual / summary
-------------------------------------
Conclusion & Future Work
------------
We found interesting associations between mRFEI and characteristics of Cook County census tracts. Since low access to healthy food is associated with adverse health outcomes, our exploratory data analysis investigated associations between health outcomes, mRFEI, demographics, and socioeconomic indicators (i.e. income) for these census tracts. We found a positive association between mRFEI and a census tract’s median income, which is consistent with our hypothesis that higher income census tracts would be more likely to have higher access to healthy food. To explore potential associations between mRFEI and health outcomes, we investigated whether there were correlations between them. We found that higher shares of adverse health outcomes in a census tract were negatively associated with mRFEI, particularly in low-income census tracts. By contrast, higher utilization of healthcare in a census tract was positively associated with mRFEI. Next, we wanted to explore associations between health outcomes and demographics. We found that adverse health outcomes were more prevalent in low-income, highly segregated census tracts that were predominantly Black relative to census tracts that were predominantly non-Black. These disparities are partially mitigated when controlling for low-income but nonetheless persist. Finally, we explored relationships between mRFEI and census tract demographics. We found highly skewed, lower mRFEI values in census tracts that had a higher than median proportion of Black residents relative to census tracts with a lower than median proportion of Black residents. Finally, we decided to explore the relationship between mRFEI, the proportion of Hispanic/Latinx residents, and health outcomes. Surprisingly, some adverse health outcomes were positively associated with mRFEI in census tracts with greater than 80% Hispanic/Latinx residents relative to census tracts with less than 20% Hispanic/Latinx residents. Further work is warranted to make sense of this finding in the context of our other results and previous findings. Overall, the associations we found between mRFEI, health outcomes, demographics, and income are consistent with previous studies [1,2].

Our exploratory data analysis helped guide our approach to modeling. We used random forest classifiers to predict mRFEI categories associated with food deserts (mRFEI = 0), food swamps (0 < mRFEI < 6.85), and healthful census tracts (mRFEI > 6.85). We trained classifiers to predict whether a census tract was a food desert or healthful, or whether a census tract was a food swamp or healthful. Since we found mRFEI to be associated with income, we wanted to train models on census tracts stratified by income. 

The features between those designation of mrfei are not as clear cut. We approached the problem a little differently by now identifying Food Deserts and Food Swamps separately. Then predicting mRFEI values of census tracts. After this adjustment, the results improved dramatically with +90% predictive accuracy. We found similar results from our EDA where relationships with the dependent variable change depending on another variable. Accuracy was dramatically improved when we modeled tracts designated as ‘low income’ vs those not labeled as ‘low income’. 

In addition to re-defining our project question, we realized that based on our modeling results our team may want to explore further testing by segmenting the data by low income helped prediction dramatically, but, given that this flag was created by rules, investigation into alternate ways to segment this data may help prediction further.

We consistently found that our classifiers performed better when predictions were stratified this way; that is, our classifiers were better able to predict mRFEI categories for low-income only tracts and for non-low-income only tracts (relative to predicting mRFEI categories in all census tracts together). This suggests that the weights of features used to predict mRFEI depend on socioeconomic factors like level of income. We found that health outcome features were often heavily weighted for predicting mRFEI, such as the proportion of residents with tooth loss and the proportion of senior female residents utilizing preventative clinical services like getting a flu vaccine or health-related screenings. This is consistent with our findings from exploratory data analysis that highlighted associations between mRFEI and health-related outcomes. Also consistent with our findings from exploratory data analysis, we found that socioeconomic and demographic features, such as the share of low-income residents and the share of non-white residents in a census tract, were also predictive of mRFEI. Taken together, census tract features used to predict mRFEI categories in our models, which include health outcomes in addition to socioeconomic and demographic characteristics, are consistent with and expand on previous findings that focused on predicting mRFEI from socioeconomic and demographic characteristics alone [2]. 

Our findings from exploratory data analysis and modeling are represented in an interactive Tableau dashboard. We hope that non-profit organizations and community organizers can utilize this dashboard to not only gain a deeper understanding of factors associated with healthy food access in Cook County, but also to help drive data-driven strategies for mitigating lack of access to healthy food.

References
------------
* [Food Access Research Atlas](https://www.ers.usda.gov/data-products/food-access-research-atlas/download-the-data/)
* [Modified retail food environment index (mRFEI)](https://www.cdc.gov/nutrition/resources-publications/)
* [Underlying Cause of Death](https://wonder.cdc.gov/wonder/help/ucd.html)
* [500 Cities & Places](https://chronicdata.cdc.gov/500-Cities-Places/PLACES-Local-Data-for-Better-Health-Census-Tract-D/cwsq-ngmh)
* [Cartographic Boundary Files](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html)
* [Chicago Census Tracts](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Census-Tracts-2010/5jrd-6zik)
* [Chicago Cityscape GIS Data](https://github.com/ChicagoCityscape/gis-data)
* [CTA Open Data](https://www.transitchicago.com/data/)


