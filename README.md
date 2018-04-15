<Lending Club Statistics>

Part 1: Data wrangling and exploratory data analysis 
Data Download and pre-processing: 
Your first challenge is to programmatically download the data from
https://www.lendingclub.com/info/download-data.action
Your goal is to download the data programmatically from the website and create one dataset for the entire database.
Things to think about:
• Data download: How will you download all loan data and create one dataset? How can you timestamp the data so you know when the data was recorded?
• Missing data analysis: How will you handle missing data?
• Feature engineering: What variables do you need to predict interest rates? Ensure users would be
able to give you that information to help you predict rates
• You need to create one more pipeline to do this for the “Declined Loan data”. Repeat above steps
NOTE: NO HUMAN INTERVERSION SHOULD BE NEEDED AT ALL. YOUR LUIGI/AIRFLOW script SHOULD DO EVERYTHING.
Exploratory Data analysis: 
• Write a Jupyter notebook using R/Python to graphically represent different summaries of data. Summarize your findings in this notebook.
• Summarize your key insights about different user profiles, states, loan amounts etc.


Part II: Building and evaluating models. 
Your next goal is to build a model to predict interest rates. You will get leads from people with different profiles and you must decide if you will give loans or not and if you will give a loan, how much interest you would charge for those loans.
Classification 
Use the “Loan Data” and the “Declined Loan Data” datasets to build classification models that will generate a flag whether to give a loan or not.
Copyright QuantUniversity LLC. 2017 – Cannot be reused/quoted without written permission
• Start with logistic regression using Jupyter and Python/R
• Compute ROC curve and Confusion matrices for training and testing datasets and comment on the
results.
• Repeat this using Random Forest, Neural Network models algorithms.
• Choose one model you will deploy and implement this model on the Microsoft azure machine
learning studio and create a REST API
• You should be able to a new record (You can define what features you will use) and the result will be
a flag whether you would give a loan or not.
Clustering 
Once you have decided to give a loan, you should build models to decide what interest rate to give. You are debating whether to create one model for all customer prospects or segment data into clusters and then build prediction models specific to each cluster. You think of creating segments or clusters and build models one for each cluster. Your brainstorm with your team and come up with 3 possibilities:
1. Segment data into clusters (you define how many) manually using categorical or numerical features. For example, you can segment by state, by ownership of home, by average dti or a combination of features.
2. You use a clustering algorithm (that can factor both numerical and categorical variables) and segment data into k clusters. You will then build prediction models for each cluster.
3. No clusters; Just use data as is
Once you do the clustering use t-sne to visualize your clusters for some sample test data. See
http://distill.pub/2016/misread-tsne/ for guidance on using t-sne Prediction 
• Write a prediction script in a Jupyter notebook in R/Python that builds a Regression model for the interest rate using data from the 3 clustering methodologies you worked
o Tryvariableselectionandbuildthebestmodelforeachsegment/cluster(Note:Youmay have many segments and each model may have different coefficients based on the clusters used to train. You should automate it. You could try parallel computing libraries to make things go faster)
o ComputeMAE,RMS,MAPEfortrainingandtestingdatasets
o Repeat this using Random Forest, Neural Network models and KNN algorithms.
o Choose the best model amongst the 4 types of algorithms.
o Deploy the best algorithm/algorithms on Azure ML studio
o You will have a bunch of Rest APIs you should be able to choose from based on the cluster
the record belongs to
Deployment 
Design the following workflow:
• Given a record, use a pre-trained clustering model to cluster the record to a segment.
• You will have 3 cluster assignments (1-manual, 2-based on your clustering algorithm, 3-default 1-
cluster for all data)
• For each cluster, there should be a RestAPI which is linked to a chosen prediction model. Look up
that API and use it to predict the 3 distinct interest rates.
• Select the highest interest rate and return it as your prescribed interest rate.
