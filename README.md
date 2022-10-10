<img src="images/health-insurance.jpg" alt="logo" style="zoom:100%;" />

<h1>Health Insurance Cross Sell</h1>

<p align="justify">This is a fictional project for studying purposes. The business context and the insights are not real. 
The dataset is from a Health Insurance company that sells various kinds of insurance. The dataset is available on <a href="https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction" target="_blank">Kaggle</a>.</p>

<h2>1. Description of the Business Problem</h2>

<p align="justify">An insurance company sells health insurance to its customers. They want to start selling vehicle insurance to these customers in order to diversify their products. The company will call these customers and offer this new type of insurance. The company surveyed its customers to get some data from them and find out which ones would be interested in vehicle insurance to make a cross sell. The company has availability to make only two thousand calls. They believe that one of the ways to reach as many customers as possible with the least amount of calls is to make a machine learning model that sorts the list of customers to maximize the amount of contracted services. It is a type of classification problem called learn to rank.</p>

<h3>The tools that were created:</h3>

<p align="justify"><b>Machine Learning Classification Model: </b>Using the dataset from <a href="https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction" target="_blank">Kaggle</a>, a machine learning classification model was created to be use for future predictions.</p>The notebook used to create the model is available <a href="https://github.com/m4theus4ndr4de/classification-health-insurance-cross-sell/blob/main/notebooks/model-development.ipynb" target="_blank">here</a>.</p>

<p align="justify"><b>Flask Prediction API: </b>The model is available on the cloud Heroku and can be acessible by an API created using Flask. The API source code is available <a href="https://github.com/m4theus4ndr4de/classification-health-insurance-cross-sell/blob/main/health-insurance-app-ma/handler.py" target="_blank">here</a>.</p>

<p align="justify"><b>Google Sheets Script: </b>A Google SHeets Script was developed to br used as a way to make predictions for several custumers at once. The spreadsheet is available <a href="https://docs.google.com/spreadsheets/d/1Rqe43njtijO54H-xon1Q3-XWC8ETXqPs3Qe4cGv3IhY/edit?usp=sharing" target="_blank">here</a>. There is a button on the top menu called "Health Insurance Prediction". To make predictions the user have to click there, click on "Get Prediction" and the predictions for all the rows in the spreadsheet will appear on the prediction column.</p>

<h2>2. Dataset Attributes</h2>

<p>Information about the attributes can be found <a href="https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction" target="_blank">here</a>.</p>

<table style="width:100%">
<tr><th>Attribute</th><th>Description</th></tr>
<tr><td>id</td><td>Unique ID for the customer</td></tr>
<tr><td>Gender</td><td>Gender of the customer</td></tr>
<tr><td>Age</td><td>Age of the customer</td></tr>
<tr><td>Driving_License</td><td>0 : Customer does not have DL, 1 : Customer already has DL</td></tr>
<tr><td>Region_Code</td><td>Unique code for the region of the customer</td></tr>
<tr><td>Previously_Insured</td><td>1 : Customer already has Vehicle Insurance, 0 : Customer doesn't have Vehicle Insurance</td></tr>
<tr><td>Vehicle_Age</td><td>Age of the Vehicle</td></tr>
<tr><td>Vehicle_Damage</td><td>1 : Customer got his/her vehicle damaged in the past. 0 : Customer didn't get his/her vehicle damaged in the past.</td></tr>
<tr><td>Annual_Premium</td><td>The amount customer needs to pay as premium in the year</td></tr>
<tr><td>PolicySalesChannel</td><td>Anonymized Code for the channel of outreaching to the customer ie. Different Agents, Over Mail, Over Phone, In Person, etc.</td></tr>
<tr><td>Vintage</td><td>Number of Days, Customer has been associated with the company</td></tr>
<tr><td>Response</td><td>1 : Customer is interested, 0 : Customer is not interested</td></tr>
</table>

<h2>3. Business Premises</h2>

<h3>The premises that were assumed for the development of the business problem solution are:</h3>

<ul>
<li>Cross-selling is a sales technique that involves selling an additional product or service to an existing customer.</li>
<li>Learn to rank is a kind of classification problem in which the objective is to order a datatable based on the probability of some data be of an specific class.</li>
<li>There is no Policy Sales Channel better than others, they should have the same weight to the model prediction.</li>
</ul>

<h2>4. Solution Strategy</h2>

<ol>
<li>Understand the Business problem.</li>
<li>Download the dataset from <a href="https://www.kaggle.com/competitions/rossmann-store-sales/data" target="_blank">Kaggle</a>.</li>
<li>Clean the dataset removing outliers, NA values and unnecessary features.</li>
<li>Explore the data to create hypothesis, think about a few insights and validate them.</li>
<li>Prepare the data to be used by the modeling algorithms encoding variables, splitting train and test dataset and other necessary operations.</li>
<li>Create the models using machine learning algorithms.</li>
<li>Evaluate the created models to find the one that best fits to your problem.</li>
<li>Tune the model to achieve a better performance.</li>
<li>Deploy the model in production so that it is available to the user.</li>
<li>Find possible improvements to be explored in the future.</li>
</ol>

<h2>5. Machine Learning Modeling</h2>

<p align="justify">The final result of this project is a classification model to rank the table. Therefore, six models were created: KNN (K-Nearest Neighbors), Logistic Regression, Extra Trees, Random Forest, XGBoost and LightGBM.</p>

<p align="justify">The Boruta algorithm was used to select features for the model and only one feature were selected by Boruta. The dataset features are not very good at explaining if the customers want or not a vehicle insurance. The features for the model were chosen based on the feature importance in an Extra Trees model, seven features were selected. 
The models were evaluated considering two metrics, Precision at K and Recall at K considering the two thousand first rows of the table the models should rank. The initial models performances are in the table below.</p>

<table style="width:100%">
<tr><th>Model Name</th><th>Precision at K</th><th>Recall at K</th></tr>
<tr><td>LightGBM</td><td>0.4153</td><td>0.0895</td></tr>
<tr><td>XGBoost</td><td>0.4078</td><td>0.0879</td></tr>
<tr><td>Random Forest</td><td>0.3363</td><td>0.0725</td></tr>
<tr><td>KNN</td><td>0.3338</td><td>0.0719</td></tr>
<tr><td>Extra Trees</td><td>0.3288</td><td>0.0709</td></tr>
<tr><td>Logistic Regression</td><td>0.3028</td><td>0.0653</td></tr>
</table>

<h2>6. Final Model</h2>

<p align="justify">To decide which would be the final model, a cross-validation was carried out to evaluate the performance of the algorithms in a more robust way. These metrics are represented in the table below.</p>

<table style="width:100%">
<tr><th>Model Name</th><th>Precision at K</th><th>Recall at K</th></tr>
<tr><td>LightGBM CV</td><td>0.4222 +/- 0.0037</td><td>0.1128 +/- 0.0007</td></tr>
<tr><td>XGBoost CV</td><td>0.4120 +/- 0.0055</td><td>0.1102 +/- 0.0013</td></tr>
<tr><td>Random Forest CV</td><td>0.3526 +/- 0.0106</td><td>0.0942 +/- 0.0031</td></tr>
<tr><td>KNN CV</td><td>0.3374 +/- 0.0059</td><td>0.0904 +/- 0.0015</td></tr>
<tr><td>Extra Trees CV</td><td>0.3216 +/- 0.0039</td><td>0.0860 +/- 0.0011</td></tr>
<tr><td>Logistic Regression CV</td><td>0.2958 +/- 0.0111</td><td>0.0792 +/- 0.0032</td></tr>
</table>

<p align="justify">The LightGBM model was the best among all the models created. It was the one selected to be deployed. After choosing which would be the final model, a random search hyperparameter optimization was used to improve the performance of the model. The final model evaluation metrics are in the table below.</p>

<table style="width:100%">
<tr><th>Model Name</th><th>Precision at K</th><th>Recall at K</th></tr>
<tr><td>LightGBM</td><td>0.433 +/- 0.0067</td><td>0.1158 +/- 0.0018</td></tr>
</table>

<h2>7. Conclusion</h2>

<p align="justify">Although the dataset is not very good at creating classification models to predict whether or not customers would like vehicle insurance, a model was created that managed to sort the table better than a random sort. The model can help the company achieve a higher success rate when calling customers. However, it would be of great help to have more features to enhance the model predictability.</p>

<h2>8. Future Work</h2>

<ul>
<li>Improve model prediction capabilities by adding new features.</li>
<li>Explore the dataset to find possible insights.</li>
<li>Try other machine learning algorithms.</li>
</ul>
