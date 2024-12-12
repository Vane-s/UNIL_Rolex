# DSML-Rolex-Project-difficulty-analysis

# Team Members : (photo) 
-Vanessa Faller 
-Sasha Granelli 

# 1. Introduction
This project is part of a Data Science and Machine Learning course and focuses on developing a personalized recommendation system for a university library platform. The goal is to enhance the user experience by making it easier for users to discover books that align with their interests. Leveraging modern data science and machine learning techniques, this project highlights the role of recommendation technologies in improving digital services.

The project adopts a practical approach to address a common challenge in digital environments: tailoring content to meet users' specific needs. By analyzing interactions between users and the library’s catalog, we have designed a solution capable of predicting reading preferences and providing targeted suggestions.

This fictitious project, designed to reflect real-world challenges, provides an opportunity to explore various aspects of recommendation systems, from data preparation to model implementation, while considering the impact on user experience. It also demonstrates the critical role of data in designing innovative technological solutions.

# 2. Objectives
The main objectives of this project are:

**Build a functional solution by applying data science skills:** Use user-book interaction data to develop an effective recommendation model. This includes data processing, model training, and result optimization to ensure relevant recommendations.

**Tackle a concrete personalization challenge:** Develop a system capable of accurately predicting books that might interest a given user based on their history and the metadata of the library’s catalog. This challenge allows the application of advanced machine learning techniques while exploring their utility in a real-world context.

**Enhance user experience:** Provide recommendations that increase engagement with the platform and simplify the discovery of relevant content. This objective emphasizes the connection between technology and user satisfaction in an educational setting.

By working within a fictitious yet representative framework, this project provides a unique opportunity to apply theoretical methods in a practical context. It demonstrates how artificial intelligence technologies can be leveraged to solve practical problems while fostering an enriched user experience.

# 3. Méthodologie







#Project structure : ?

#Important link : 
Link to download the folder with our app and all the models : 

## Technique, Precision and Recall :
|   Technique          |   Precision@10   |   Recall@10   |  
|----------------------|------------------|---------------|  
| User-to-User CF      | 0.0565           | 0.2906       |  
| Item-to-Item CF      | 0.0556           | 0.2639       |  
| Optimized Model      | 0.1452           | 0.1452        |  

##Data Exploration (EDA):
##1. Interaction Summary:
-Users in the Platform: 7,838
-Books with Interactions: 15,109
-Total Books Available: 15,291
-Total User Interactions: 87,047

##2. Data Visualization:
In order to investigate user engagement trends, different types of visualizations were developed:
-Interaction Heatmap: This heatmap highlights the distribution of interactions between users and books. It reveals both sparse and dense areas of engagement, providing insights into which books are most frequently interacted with and where user interest is concentrated.
-Histogram of Interactions: This histogram visualizes the number of books interacted with by each user. It shows a highly uneven distribution, with a large number of users engaging with only a small subset of books, while a few users interact with a significantly larger number. This pattern highlights the variability in user behavior and engagement.

##3. Key Findings:
-Popular books tend to receive more interactions, resulting in their overrepresentation in the dataset compared to less frequently interacted-with books.
-Some users interact with the same book multiple times, suggesting repeated engagement or interest.
-The dataset is extensive, covering a large number of books, but occasionally lacks certain details, such as author information. This underscores the importance of developing a strong recommendation model that can still deliver effective suggestions despite these gaps.

#Best Model : ?

#Data enhancement: 
To enriche prediction accuracy, we can augment our dataset by using an API to gather additional details, such as book descriptions. This will allow the model to access a more comprehensive set of information, facilitating the use of text embedding for more accurate and insightful recommendations.

#Leaderboard : 
After implementing and testing these different models, we achieved a score of 0.1452 upon submitting our CSV file on Kaggle. This marks a noticeable improvement compared to our earlier score of 0.1241, which was obtained prior to training our model on the complete dataset. The increase in performance highlights the impact of using the full dataset for training, allowing the model to better capture the underlying patterns and improve its predictions.

#Steps to follow:
-Clean the data
-Try different algorithms
-Calculate the accuracy of each algorithm using the train and test datasets
-Select the algorithms with the best accuracy
-Test the algorithms individually (submit the predictions for each algorithm separately on Kaggle)
-Test the combination of the two algorithms with the best accuracy (hybrid model)
-Submit the hybrid model's predictions

#Future work: 
-Text embedding / API
-Neural Network 
-Classification ? 

# Video Presentation:
[Insert link to your presentation video]


