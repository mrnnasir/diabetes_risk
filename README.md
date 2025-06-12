# Diabetes Risk Analysis

This project aims to analyze key factors influencing diabetes risk using health, lifestyle, and demographic data. By identifying significant predictors and building machine learning models, the project helps in assessing individuals' risk levels and supports preventive healthcare efforts.

# Business Objective

The project aims to develop a predictive analytics dashboard that leverages physiological and behavioral data—such as BMI, blood pressure, age, physical activity, gender, and weight—to evaluate and forecast diabetes risk levels among individuals. The primary business goal is to uncover key determinants of diabetes risk within a cardiovascular health dataset and construct a reliable model that classifies individuals into Low, Moderate, or High risk categories. This data-driven approach will empower healthcare providers and policymakers to implement proactive, personalized interventions, optimize resource allocation, and design more effective wellness strategies tailored to population health needs.

# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)


## Dataset

**Primary Source:** `cardio_data_processed.csv`. The dataset is available on Kaggle at [Cardiovascular Disease](https://www.kaggle.com/datasets/colewelkins/cardiovascular-disease/data). The size of the dataset is approximately 7 mb.

**Secondary Source:** I used ChatGPT to calculate the percentage of diabetes risk for individuals based on the cardio dataset in a separate notebook. Then I merged the diabetes risk percentage column to the cardio dataset.

**Key fields:** The Cardio dataset is a pre-processed dataset with over 68,000 rows.  This dataset contains 17 columns, including `BMI`, `Age`, `BP Category`, `Active`, and `Gender`. These are my key areas to investigate against `Diabetes Risk Percentage`, which is  a target variable.


## Business Requirements
* **Key Risk Factor Analysis:** Visualize relationships between clinical indicators (BP, BMI, age) and diabetes risk
* **Predict diabetes risk:** Develop a robust machine learning model to predict the category of diabetes risk (e.g., low, medium, high) for individuals.
* **Inform clinical decision-making:** Provide actionable insights that can assist healthcare professionals in early detection and management of diabetes risk.
* **Population Insights:** Highlight demographic patterns (gender, age groups) in risk distribution
* **Clinical Decision Support:** Provide statistically validated insights for preventive care
* **Scalability:** The solution should be scalable to handle larger datasets and potentially incorporate new data sources.


## AB Testing
* * ***Null Hypothesis (H<sub>0</sub>)***:
  * Percentage of diabetes risk is the same for both groups.
* ***Alternative Hypothesis (H<sub>1</sub>)***:
  * Percentage of diabetes risk is higher for the group with no physical activity.
* **Validation:**
  * **Normality Test:** Shapiro-Wilk test indicates that the data is not normally distributed.
  * **Mann-Whitney U Test:** The p-value is $p=0.0338$. Since the p-value is less than $0.05$, we reject the null hypothesis, indicating a significant difference in diabetes risk percentage between physically active and non-active individuals.
* **Conclusion:** The results suggest that there is a association between physical activity and diabetes risk. The Mann-Whitney U test results provide strong evidence to reject the null hypothesis and highlight the importance of physical activity in diabetes risk reduction.


## Hypotheses Validation
* In this project, I have investigated the following hypotheses to understand the associations between various factors and diabetes risk, validated primarily using Chi-square and Kruskal-Wallis tests:

**H1. Blood Pressure Category vs Diabetes Risk**
* $H_0$: There is no association between `bp_category` and `diab_risk_cat`.
* $H_1$: There is an association between `bp_category` and `diab_risk_cat`.
* **Validation:** Chi-square test (Pearson's $\chi^2 = 3353.43$, $p=0.0$) and Kruskal-Wallis test ($H = 3304.85$, $p=0.0$). The very low p-values indicate a strong association, leading to the rejection of the null hypothesis.

**H2. BMI Category vs Diabetes Risk**
* $H_0$ (Null): There is no association between `bmi_category` and `diab_risk_cat`.
* $H_1$ (Alt): There is an association between `bmi_category` and `diab_risk_cat`.
* **Validation:** Chi-square test (Pearson's $\chi^2 = 65193.12$, $p=0.0$) and Kruskal-Wallis test ($H = 52364.13$, $p=0.0$). The results show a very strong association, leading to the rejection of the null hypothesis.

**H3. Age Group vs Diabetes Risk**
* $H_0$: There is no association between `age_group` and `diab_risk_cat`.
* $H_1$: There is an association between `age_group` and `diab_risk_cat`.
* **Validation:** Chi-square test (Pearson's $\chi^2 = 6672.61$, $p=0.0$) and Kruskal-Wallis test ($H = 8515.77$, $p=0.0$). These results indicate a significant association, leading to the rejection of the null hypothesis.

**H4. Physical Activity vs Diabetes Risk**
* $H_0$: There is no association between `active` (physical activity) and `diab_risk_cat`.
* $H_1$: There is an association between `active` and `diab_risk_cat`.
* **Validation:** Chi-square test (Pearson's $\chi^2 = 12.80$, $p=0.001659$) and Kruskal-Wallis test ($H = 7.41$, $p=0.006478$). The p-values are less than $0.05$, suggesting a significant association, leading to the rejection of the null hypothesis.

**H5. Gender vs Diabetes Risk**
* $H_0$: There is no association between `gender` and `diab_risk_cat`.
* $H_1$: There is an association between `gender` and `diab_risk_cat`.
* **Validation:** Chi-square test (Pearson's $\chi^2 = 2128.41$, $p=0.0$) and Kruskal-Wallis test ($H = 1683.07$, $p=0.0$). The very low p-values confirm a strong association, leading to the rejection of the null hypothesis.


## Project Plan
* I used the following high-level steps for the analysis:
  1. I used Kanban board to plan the project and track progress. It's a robust tool to track the project progression, organize tasks and identify bottolenecks.
  2. Created five different notebooks for the purpose of ease of use, clarity and separation of concerns.
  3. Data Collection: Gathered the cardiovascular disease dataset from Kaggle. Used ChatGPT to calculate the diabetes risk percentage for individuals based on the cardio dataset.
  4. Data Preprocessing: Cleaned and preprocessed the data, including handling missing values and encoding categorical variables.
  5. Exploratory Data Analysis (EDA): Conducted EDA to understand the data distribution and relationships between variables.
  6. I used LMS and different OpenAI like, ChatGPT, Co-Pilot, Deepseek, Perplexity and Gemini across the project for various purposes. Additioninally, I also tried to gather some ideas from previous students project works.
  7. Feature Engineering: Created new features based on existing data to enhance model performance.
  8. Conducted A/B testing to compare diabetes risk percentages between physically active and non-active individuals, including normality tests and Mann-Whitney U test.
  9. Hypothesis Testing: Validated hypotheses using statistical tests (Chi-square and Kruskal-Wallis).
    * Perform Chi-square tests for independence between feature variables and `diab_risk_cat`.
    * Perform Kruskal-Wallis tests for numerical variables (converted to ordinal if applicable) against `diab_risk_cat_num`(encoded version of `diab_risk_cat`).
  10. Split Data: Divided the dataset into training and testing sets to prepare for model training.
  11. Cross-Validation: Implemented cross-validation to ensure model robustness, prevent overfitting and evaluate various machine learning models (Logistics Regression, Decision Trees & Random Forests) for selecting the best performing model to predict diabetes risk categories.
  12. Model Development: Developed machine learning models to predict diabetes risk categories.
  13. Model Evaluation: Evaluated model performance on both train and test sets using metrics such as precision, recall, F1-score, accuracy, confusion matrix and classification report.
  14. Insights and Reporting: Summarized key findings from hypotheses and predictive analysis
  15. Created Power BI dashboard to visualize insights

## The rationale to map the business requirements to the Data Visualisations

* **Identifying key risk factors:** Visualizations like bar charts showing `diab_risk_cat` distribution across `bp_category`, `bmi_category`, `age_group`, `gender`, and `active` can immediately highlight associations.
* **Communicating model performance:** Confusion matrix and classification reports, when visualized, provide a clear picture of how well the predictive model is performing in identifying each diabetes risk category.
* **Informing clinical and public health initiatives:** Interactive dashboards allow clinicians and public health officials to explore the data, filter by different demographics, and understand the impact of various factors, aiding in targeted interventions.
* **Promoting data-driven decision making:** By presenting complex information in an intuitive visual format, decision-makers can quickly grasp the key takeaways and make informed choices.


## Analysis techniques used

* **Descriptive Statistics:** I used `.describe()` to summarize key features of the dataset (e.g., mean, median, standard deviation, counts). Then I used `.info()` to get an overview of the dataset, including data types and missing values and `.isnull().sum()` to check for missing values in each column. I used `.duplicated()` to check for duplicate rows in the dataset. Though there are some duplicate rows in the dataset, but data of those rows are not exactly same, so I decided to keep them as they are.

* **Exploratory Data Analysis (EDA):**
    * **Group Creation:** Using function, I created new columns like `bmi_category`, `age_group`, `age_simp_group`, `bmi_simp_cat` and `diab_risk_cat` to categorize variables into meaningful groups.
    * **Value Counting:** I used `value_counts()` to understand the distribution of categorical variables.
    * **Encoding Categorical Variables:** I encoded `bmi_category`, `age_group`, `bp_category`, and `diab_risk_cat` into numerical values for analysis and modeling purposes.
    * **Skewness and Kurtosis:** I calculated skewness and kurtosis to understand the distribution of numerical variables.
    * **Feature Engineering:** I performed feature engineering to handle right skewed data for `weight` column using logarithmic transformation and outlier for `bmi`column using Winsorizartion technique as it is a useful technique to reduce the impact of outliers on the analysis without removing them entirely.
    * **Correlation Analysis:** I performed correlation analysis and visualized it using a heatmap to identify relationships between numerical variables.

* **A/B Testing:** From the correlation analysis, I noticed that there was a negative correlation between physical activity and diabetes risk. That seemed counterintuitive as we generally believe that increased physical activity reduces diabetes risk. To investigate this further, I performed A/B testing to compare the diabetes risk percentage between physically active and non-active individuals. This involved:
        * Split Diabetes Risk Percentage column into two sample sizes based on Physically Active and Non-Active individuals.
        * Conducting normality tests (Shapiro-Wilk) to check the distribution of the data.
        * Performing Mann-Whitney U test to assess if there is a significant difference in diabetes risk percentage between the two groups.

* **Inferential Statistics (Hypothesis Testing):** I formulated 5 more null and alternative hypotheses to validate the associations between various factors and diabetes risk.
    * **Chi-square Test of Independence:** I used it to determine if there is a significant association between two categorical variables (e.g., `bp_category` and `diab_risk_cat`).
    * **Kruskal-Wallis H-test:** Since the data is not normally distributed, I used this non-parametric test to determine if there are statistically significant differences between two or more groups of an independent variable on a continuous or ordinal dependent variable (e.g., `bmi_category_num` and `diab_risk_cat` that is the encoded version of `bmi_category`).

* **Visualizations:**
    * **Univariate Analysis:** I used histogram, pie chart, stacked bar chart, violin plot and box plot to visualize the distribution of individual variables like `bmi`, `age`, and `bp_category` and more.
    * **Bivariate Analysis:** I used scatter plots and correlation matrices to explore relationships between pairs of variables, such as `weight` vs. `diab_risk_percent` and `diab_risk_cat`

* **Predictive Analytics:**
    * **Random Forest Classifier:** After performing Cross-Validation, I saw that Random Forest produces comparatively best results. This model was chosen for its robustness, ability to handle non-linear relationships, and good performance as indicated by the provided matrix.
    * **Model Evaluation:** I evaluated the model using metrics such as accuracy, precision, recall, F1-score, and confusion matrix to assess its performance in predicting diabetes risk categories. Classification reports were also generated to provide a detailed breakdown of the model's performance across different classes.
    * **Visualizing Model Performance:** I used Heatmap to visualize the confusion matrix and Bar plot for classification report to visualize the model's performance.

* **Limitations and Alternative Approaches:**
    * **Data Limitations:** The dataset is relatively huge, but it has some limitations like,
      * First and foremost, the dataset had no Diabetes Risk column, which I could use.
      * The proportion of male and female individuals are not equal, which could introduce bias in the analysis.
      * There are more active individuals in the dataset compared to non-active individuals, which could also introduce bias in the analysis.
      * It does not include some important features like family history of diabetes, diet, and medication history, which could have provided a more comprehensive understanding of diabetes risk.
      * The dataset does not include any information on the socioeconomic status of individuals, which could also be an important factor in diabetes risk.
      * The dataset does not include any information on the geographical location of individuals, which could also be an important factor in diabetes risk.
    * **Alternative Approaches:**  To overcome the main challenge, which was the lack of a Diabetes Risk column, I had to calculate the diabetes risk percentage for individuals based on the cardio dataset in a separate notebook using ChatGPT and then merge it back with the cardio dataset. If the dataset had been larger or more diverse, I could have explored deep learning techniques for potentially better performance.

* **Generative AI Tools:** I used various generative AI tools like ChatGPT, Co-Pilot, Deepseek, Perplexity and Gemini for ideation, design thinking, code optimization and documentation. These tools helped me brainstorm ideas, generate code snippets, and optimize my code for better performance. For example, I used ChatGPT to calculate the diabetes risk percentage for individuals based on the cardio dataset in a separate notebook. I also used these tools to get suggestions for data analysis techniques, selecting best plot for visualizations, and model evaluation methods. Additionally, I used these tools to generate markdown documentation for my project, which helped me structure my thoughts and present my findings in a clear and concise manner.


## Ethical considerations
* **Data Privacy:** The dataset used in this project is publicly available on Kaggle and does not contain any personally identifiable information (PII). Additionally, This dataset dataset doesn't include any sensitive or race-related information, which helps mitigate potential bias in the analysis.


## Dashboard Design
* I have created single page dashboard using Power BI to visualize the insights from the analysis. The dashboard includes various visualizations like stacked bar charts, pie charts, swarm plot, box plot and scatter plot to represent the relationships between different variables and diabetes risk. The dashboard is designed to be interactive, allowing users to filter data based on different criteria like `bp_category`, `bmi_category`, `age_group`, `gender`, and `active`. This interactivity helps users explore the data and gain insights into the factors influencing diabetes risk.

  - I used slicers to allow users to filter the data based on different criteria like `gender`, `age_group` and `active`. This interactivity helps users explore the data and gain insights into the factors influencing diabetes risk. Slicer's filter functionality allows users to select specific categories, which dynamically updates the visualizations on the dashboard to reflect the selected data. This feature enhances user engagement and allows for a more personalized exploration of the data.

  - I used pie charts to represent the distribution of categorical variables like `gender`, `active` and `diabetes risk category`. Pie charts are effective for showing proportions and percentages, making it easy to understand the distribution of different categories at a glance.

  - I used stacked bar charts to visualize the relationship of `gender_char`, `bp_category`, `bmi__simp_cat`, `age_simp_group` with `diabetes risk category`. Stacked bar charts allow for easy comparison of multiple categories within a single bar, making it clear how different factors contribute to diabetes risk. I used this chart to visualize the distribution of `diabetes risk percentage` across `gender_char`, `active_char` and `age_group`. Stacked bar charts allow for easy comparison of multiple categories within a single bar, making it clear how different factors contribute to diabetes risk. It gives the option of drill down to see the distribution of `diabetes risk percentage` across different categories.

  - I used swarm plot to visualize the distribution of `diabetes risk category` across `bmi`. Swarm plots are useful for showing the distribution of a continuous variable across different categories, providing a clear view of how `bmi` varies within each diabetes risk category. I also used scatter plot to visualize the relationship between `diabetes risk percentage` and `bmi`. Scatter plots are effective for showing the correlation between two continuous variables, allowing users to see trends and patterns in the data.

  - I used box plots to visualize the distribution of `diabetes risk category` across `weight`. Box plots are effective for showing the spread and central tendency of a continuous variable, making it easy to identify outliers and understand the distribution of `weight` within each diabetes risk category.

  - I used a heatmap to visualize the correlation between predicted labels and actual labels of the confusion matrix for the test set. Heatmaps are useful for showing the strength of relationships between variables, making it easy to identify patterns and correlations in the data.

  - I created three cards to display the total number of high, medium and low risk individuals based on the test set predictions. Cards are effective for displaying key metrics and summary statistics, providing a quick overview of the data.

I believe that the dashboard effectively communicates the insights from the analysis and provides a user-friendly interface for exploring the data. The use of interactive visualizations, slicers, and various chart types helps users understand the relationships between different variables and diabetes risk, making it a valuable tool for healthcare professionals and policymakers.

In most cases, I used built-in visualizations in Power BI, but I also used some custom visuals like `Swarm Plot` and `Heatmap` using python script and downloaded `Box Plot` from marketplace to enhance the dashboard's functionality and provide a more comprehensive view of the data. These custom visuals allow for better representation of the data and help users gain deeper insights into the factors influencing diabetes risk.


## Unfixed Bugs

- I don't have any unfixed bugs in this project.
- During the development of the project, if I stumbled upon any situation that I could not resolve, I went back to LMS or asked openai tools like ChatGPT, Co-Pilot, Deepseek, Perplexity and Gemini for help. I also tried to gather some ideas from previous students' project works or Vasi.


## Development Roadmap

- Initial challenge was to find out the right dataset for the project. Once I found the cardiovascular disease dataset, I realized that it would be a great if I could use it for diabetes risk analysis. Unfortunately, there was no direct diabetes risk information available, so I had to calculate the diabetes risk percentage for individuals based on the cardio dataset in a separate notebook using ChatGPT and then merge it back with the cardio dataset. This was a crucial step as the dataset did not have a Diabetes Risk column, which I could use.
- Another main challenge was to recall all I learned in the course and apply it to this project. I had to go back to LMS and review the concepts of data analysis, machine learning, and data visualization. It consumed a significant amount of time. Thanks to generative AI tools like ChatGPT, Co-Pilot, Deepseek, Perplexity and Gemini which assisted me for ideation, design thinking, code optimization and documentation.
- I hope to continue improving my skills in data analysis and machine learning by exploring more advanced techniques and tools. In this project, I cross-validated three models. I plan to improve my skills on other machine learning models like XGBoost, LightGBM, and CatBoost in the future. I also plan to explore deep learning techniques for potentially better performance and more advanced visualization.


## Input
* In the **RAW** folder, I have included 2 files
  - `cardio_data_processed.csv`: The main dataset used for the analysis.
  - `cardio_data_diabetes_risk.csv`: The dataset with diabetes risk percentage calculated using ChatGPT.


## Output
* In the **OUTPUT** folder, I have included 2 files
  - cardio_data_processed_cleaned.csv: The cleaned dataset after preprocessing.
  - cardio_data_diabetes_risk_cleaned.csv: The cleaned dataset with diabetes risk percentage calculated using ChatGPT.


## Notebooks
* In the **NOTEBOOKS** folder, I have included 6 notebooks
  - **`1. EDA.ipynb`**: The notebook for Exploratory Data Analysis.
  - **`2. diabetes_risk_calc.ipynb`**: The notebook for calculating diabetes risk.
  - **`3. visualization.ipynb`**: The notebook for basic data visualization.
  - **`4. AB_test.ipynb`**: The notebook for A/B Testing.
  - **`5. hypotheses_testing.ipynb`**: The notebook for Hypothesis Testing.
  - **`6. data_modeling.ipynb`**: The notebook for Predictive Analysis.


## Main Data Analysis Libraries
* **Pandas**: For data manipulation and analysis.
* **NumPy**: For numerical operations and handling arrays.
* **Matplotlib**: For creating static, animated, and interactive visualizations in Python.
* **Seaborn**: For statistical data visualization based on Matplotlib.
* **Scikit-learn**: For machine learning algorithms and model evaluation.
* **Pingouin**: For statistical analysis and hypothesis testing.
* **Feature-engineering**: For feature engineering and preprocessing tasks.
* **Plotly**: For creating interactive visualizations.
* **Power BI**: For creating interactive dashboards and visualizations.
* **OpenAI**: For using ChatGPT to calculate diabetes risk percentage and assist in various tasks throughout the project.


## Credits 

* On various occasions, I checked the LMS and used the resources provided by Code Institute to help me with this project. 
* I checked project works of previous students to gather ideas and inspiration. In particular, I found the project work of Iqra was very helpful since she also used medical dataset for her project, but completely different areas of focus.
* I used various openAI tools like ChatGPT, Co-Pilot, Deepseek, Perplexity and Gemini for ideation, design thinking, code optimization and documentation. These tools helped me brainstorm ideas, generate code snippets, and optimize my code for better performance.
* I checked Seaborn and Plotly color palettes to choose the best color palette for my visualizations.
* I used kaggle to find the dataset.


### Content 

- The text for the Home page was taken from Wikipedia Article A
- Instructions on how to implement form validation on the Sign-Up page was taken from [Specific YouTube Tutorial](https://www.youtube.com/)
- The icons in the footer were taken from [Font Awesome](https://fontawesome.com/)

### Media

- The photos used on the home and sign-up page are from This Open-Source site
- The images used for the gallery page were taken from this other open-source site



## Acknowledgements (optional)
* I would like to thank Vasi for his guidance and support throughout the project. His feedback and suggestions were invaluable in shaping the project and improving the analysis.
* I would also like extend my gratitude to my fellow students for their support and encouragement. Their insights and discussions helped me gain a deeper understanding of the project and its objectives.
* Finally, I would like to thank the Code Institute for providing the resources and support needed to complete this project. The course materials and lectures were instrumental in helping me understand the concepts of data analysis, machine learning, and data visualization.