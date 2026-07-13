<h1>Online shopper intent prediction</h1>
<p>Predicting if a visitor will purchase from a website based on their browsing behavior during that session. No purchase history or demographics needed.</p>
<h2>Overview</h2>
<p>E-commerce sites can’t wait until checkout to find out if a visitor is going to buy — by then it’s too late to do anything about it. The project leverages session-level browsing signals (such as pages visited, time spent, bounce/exit rates, etc.) to predict purchase intent, a model that could serve as the basis for real-time interventions such as a discount pop-up, a live chat prompt, or a personalized recommendation before a visitor departs empty-handed.</p>
<h3>Features fall into four categories</h3>
<ol>
  <li><b>Page Engagement: </b>number of Administrative, Informational, and Product-Related pages and total time spent on them
  <li><b>Google Analytics Metrics: </b>'BounceRates', 'ExitRates', 'PageValues'
  <li><b>Temporal Context: </b>'Month', 'SpecialDay' (proximity to holiday), 'Weekend'
  <li><b>Technical / traffic metadata: </b>'OperatingSystems', 'Browser', 'Region', 'TrafficType', 'VisitorType'</ol>
  <h2>Tech Stack</h2>
<p>'Python', 'Pandas', 'Numpy', 'Seaborn', 'Scikit-learn'</p>
<h2>Workflow</h2>
<ol>
  <li>Load Data from a raw CSV URL (no need to download it manually)
  <li>Clean & document: rename ambiguous columns, print full data dictionary, check for zero missing values
  <li>Exploratory analysis: Distribution plots for each numeric feature, purchase-rate breakdowns by month / OS / browser /   region / traffic type / visitor type / weekend, count plots for categorical variables, correlation heatmap, and box plots for outlier identification
    <li>Preprocessing: label encoding binary columns ('Weekend', 'Revenue'), one-hot encoding 6 categorical columns, 80/20 stratified train/test split ('random_state=42'), 'StandardScaler' feature scaling
      <li>Modeling: Logistic Regression as baseline, Random Forest ('n_estimators=400, max_depth=17, max_samples=0.7, min_samples_split=5') as the tuned comparison model
        <li>Evaluation: log loss, accuracy, precision / recall / F1, confusion matrix 
</ol>
<h2>Model Comparison</h2>
<p>On the important metrics, Random Forest performs better overall. The accuracy of both models is similar (90.0% for Random Forest vs. 88.1% for Logistic Regression), but the bigger difference is in identifying customers who actually purchase.<br>
Random Forest correctly identifies half of the buyers while Logistic Regression identifies only one third of the buyers. This is crucial as buyers are in the minority with only 15.5% of sessions leading to a purchase.<br>
Logistic Regression is more cautious and misses out potential buyers rather than misclassifying a buyer. Hence Random Forest is more suitable, when the objective is to detect as many potential buyers as possible, while Logistic Regression is still a useful and less complex baseline model to compare against.</p>
<h2>Repository Structure</h2>
<p>
  online-shopper-intent-prediction/<br>
  ├── Shopper_Intent_Prediction.ipynb #Complete analysis: EDA → preprocessing → modeling → evaluation<br>
  ├── LICENCE<br>
  └── README.md
</p>
<h2>Data Source</h2>
<p>Sakar, C. & Kastro, Y. (2018). *Online Shoppers Purchasing Intention Dataset* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5F88Q</p>
