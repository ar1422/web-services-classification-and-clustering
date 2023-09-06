# web-services-classification-and-clustering

designed web service data analysis system using python which performs web service classification and web service clustering using the ProgrammableWeb data.

# Features of the System – 
•	System provides option to classify web services. The system provides TF-IDF, Topic-modeling, and word embedding modeling approaches and decision tree, naïve bayes classifier and nearest neighbor classifier for classification methods.
•	System provide option to cluster web-services. The system provides TF-IDF, Topic-modeling, and word embedding modeling approaches and K-Means and DBSCAN for clustering methods.
# Technical details of the application – 

# Data Processing Steps – 
•	All the web API data is loaded from MongoDB. 
•	Any entries containing NaN or missing values are dropped. 
•	Only features which are considered for modelling approaches are kept. Remaining columns are dropped. Currently I am considering columns – combined_tags, label, summary, and description.
•	The tags are combined into single column for easier conversion to tokens in next steps.
•	All the features are string concatenated into a single column for easier conversion to tokens in next steps.
# Data Modeling – 
•	The data is split into training set and testing set by 70% and 30%. 
•	TF – IDF - 
o	The 750 max features from all the columns mentioned above are considered. 
o	Stop words, Lemmatization is applied on the features and vectorized using TfidfVectorizer
•	Topic-Modeling – 
o	The 750 max features from all the columns mentioned above are considered.
o	Stop words and Lemmatization is applied on the features and vectorized using CountVectorizer.
o	The vector is then fed into LatentDirichletAllocation to choose the topic and resultant vector is used for Classification.
•	Word2Vec – 
o	Each service’s 500 max features are converted into TaggedDocument.
o	The Doc2Vec is built using Training data vocabulary and trained for 50 epochs.
o	The train data and test data are vectorized and fed to classifier

# Classification – 
•	Decision tree, Nearest Neighbor, Naive Bayes classifier is used for classification.
•	The training and testing data are modelled using all 3 models described in previous section is fed to the classifier. The accuracy is measure against the ground truth and Accuracy value is displayed for the user.
# Clustering – 
•	K-Means and DBSCAN are used for Clustering.
•	The complete data is modelled using all 3 models described in previous section is fed to the clustering process. The accuracy is measure against the ground truth and Accuracy value is displayed for the user.

# Requirements – 
•	gensim==3.8.3
•	nltk==3.4.5
•	pandas==1.3.5
•	pymongo==4.3.3
•	scikit_learn==1.2.2

# Usage – 
To run web service classification, please run - python service_classification.py      
To run web service clustering, please run - python service_clustering.py
Accuracy and performce is measured using Cross validation in classification. In clustering, I am using Unsupervised Internal Index method of average silhouette coefficient.
