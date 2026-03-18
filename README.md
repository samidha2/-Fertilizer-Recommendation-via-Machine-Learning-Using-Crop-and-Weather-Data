# -Fertilizer-Recommendation-via-Machine-Learning-Using-Crop-and-Weather-Data
This project develops a machine learning model to recommend fertilizers based on soil, crop, and environmental data. It is a multi-class classification problem using features like nutrients, pH, climate, and crop type. Challenges include mixed data and imbalance. Performance is evaluated using precision, recall, and F1-score.
METHODOLOGY 
1. Data Acquisition 
The success of any machine learning project relies heavily on the quality and comprehensiveness of 
the data used. This project utilizes two primary data sources critical for fertilizer recommendation:

1.1. Fertilizer Recommendation Dataset 
The main dataset comprises 3,100 observations of crop-specific fertilizer applications, collected 
from regional agricultural records. Each sample contains critical soil and environmental 
parameters, including temperature, moisture, rainfall, pH levels, and concentrations of key 
nutrients such as nitrogen, phosphorous, potassium, and carbon. Additionally, categorical 
attributes such as soil type, crop variety, fertilizer applied, and expert remarks are included. 
This dataset represents a rich multispectral view of agronomic factors influencing fertilizer usage, 
providing the foundation for supervised machine learning classification. 

1.2. Weather Data Enrichment 
Recognizing the dynamic influence of weather on soil nutrient availability and fertilizer efficacy, 
the dataset is enriched with current meteorological data sourced via the OpenWeatherMap API. 
Weather indicators including temperature, humidity, rainfall in the past hour, atmospheric 
pressure, and wind speed were collected for 14 major Indian regions relevant to the crop data. 
This real-time weather data integration aims to capture temporal variability and regional climate 
effects to improve fertilizer recommendation accuracy. 
The enriched dataset thus combines static soil and crop information with timely environmental 
measurements, creating a robust input space for machine learning algorithms. 

2. Data Pre-Processing 
Effective preprocessing is pivotal for preparing the raw and enriched datasets for machine learning 
model training and evaluation. The preprocessing pipeline included multiple stages focusing on 
data integrity, completeness, and usability.

2.1. Cleaning and Imputation 
Initial data inspection revealed no missing values across primary dataset columns, indicating 
well-maintained agronomic records. Nonetheless, routine cleaning steps were applied to handle 
potential inconsistencies:
● Whitespace trimming: All categorical text fields such as Soil type, Crop, Fertilizer, and 
Remark were stripped of leading and trailing whitespace to avoid encoding discrepancies. 
● Numeric conversion: Variables suspected of containing string forms of numerics (e.g., with 
commas) were sanitized and converted to floating-point types for proper quantitative 
analysis. 
● Outlier identification: Numerical distributions were visualized using histograms and 
boxplots to detect and understand extreme values which could skew models. While a few 
outliers were identified, they were retained initially to preserve real-world variability. 
● Imputation: Given zero missing values, no imputation was necessary. For robustness, the 
methodology includes median imputation for any future missing numeric data and 
'Unknown' class assignment for categorical gaps. 

2.2. Feature Engineering and Encoding 
Given the mix of numeric and categorical features, proper encoding was necessary for 
compatibility with machine learning models: 
● Label Encoding: Categorical variables (Soil, Crop, Fertilizer, Remark, Region) were 
label-encoded into integer codes using scikit-learn's LabelEncoder. This approach 
facilitated efficient multi-class classification, though it assumes ordinal treatment of 
categories. 
● Target Variable Encoding: Both Crop and Fertilizer target variables were label encoded, 
enabling consistent mapping between string class names and numeric labels. 
● Feature Selection: Features that captured key soil nutrients, environmental conditions, and 
agronomic identifiers were retained. Derived weather features from the API were integrated 
directly, augmenting the original data with contemporaneous environmental context. 
This preprocessing resulted in a clean, numerically encoded dataset of 19 columns, ready for 
downstream model training and evaluation. 
3. Exploratory Data Analysis (EDA) 
Exploratory Data Analysis (EDA) is a critical step designed to improve understanding of the 
complex relationships and distributions within the dataset. This facilitates informed feature 
selection and aids in interpreting subsequent model results. 

3.1. Crop and Soil Characteristics 
The dataset includes 31 distinct crop types evenly distributed with approximately 100 observations 
each, ensuring balanced representation to the extent possible. Popular crops such as rice, wheat, 
and mung bean form a significant portion of the data. Soil types are classified into five main 
categories: Acidic Soil, Peaty Soil, Neutral Soil, Loamy Soil, and Alkaline Soil, with Acidic and Peaty 
soils being the most prevalent. 
Numerical features including Temperature, Moisture, Rainfall, pH, and major nutrient 
concentrations (Nitrogen, Phosphorous, Potassium) display varied distributions. Histograms reveal 
normal-like distributions for temperature and pH, while rainfall and nutrient concentrations show 
right-skewed profiles with outliers reflecting diverse agricultural environments. 
A correlation heatmap unveiled moderate correlations among some nutrients — notably between 
Rainfall and Nitrogen, and Phosphorous and Potassium — suggesting interdependent fertilization 
effects. Carbon and Soil pH exhibit weaker correlations, indicating their independent roles in the 
system. 
Crop frequency bar plots and fertilizer usage heatmaps visualize crop prevalence and associated 
fertilizer patterns. These visualizations expose distinct fertilizer preferences for specific crops and 
soil types, which the model aims to capture. 

3.2. Weather Influence on Crop Patterns 
Weather variables are essential determinants of crop health, nutrient uptake, and consequently, 
fertilizer requirements. To understand how climatic factors influence crop distribution and 
fertilizer application patterns, weather data spanning temperature, humidity, rainfall, pressure, and 
wind speed were integrated and analyzed. 
A stacked bar chart depicting normalized crop distribution across 14 Indian regions reveals spatial 
heterogeneity in crop prevalence likely driven by regional climate and soil conditions. For instance, 
staple crops like rice and wheat dominate in certain regions, while pulses and horticultural crops 
are abundant elsewhere. 
Heatmaps of fertilizer usage across crops display preferences varying with regional environmental 
factors, suggesting farmers adapt fertilizer choices based on local weather patterns and crop 
needs. This influence is reflected in the enrichment of the model’s feature set with dynamically 
retrieved weather parameters through the OpenWeatherMap API. 
Box and swarm plots of temperature and rainfall distributions stratified by crop illustrate 
significant variability. Crops like tea and coffee occur predominantly in moderate temperature 
zones with specific rainfall ranges, aligning with known agro-climatic requirements. 
Further, analysis of non-zero rainfall distributions by crop class improves understanding of 
moisture-related nutrient availability, reinforcing the importance of real-time weather data in 
fertilizer decision-making. 
Correlation among weather variables and soil nutrients was moderate, underscoring that both sets 
provide complementary information to the model, enabling nuanced fertilizer recommendations 
sensitive to prevailing environmental conditions. 
6 
These insights substantiate the integration of weather data into the fertilizer recommendation 
pipeline, enhancing predictive robustness and agronomic relevance. 
