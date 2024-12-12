# DSML-Rolex-Project-difficulty-analysis

# Team Members : (photo) 
-Vanessa Faller 
-Sasha Granelli 

# 1. Introduction
In today’s digital age, recommendation systems have become indispensable tools for personalizing user experiences and making vast collections of content or products more accessible. This project, part of a Data Science and Machine Learning course, focuses on developing a personalized recommendation system for a university library. The goal is to enhance the user experience by helping students and researchers discover books that align with their interests and academic needs.

Recommendation systems analyze user preferences and interactions to provide tailored suggestions. They are widely used across industries, from streaming platforms (Netflix, Spotify) to e-commerce (Amazon) and social media (YouTube, TikTok). These systems leverage powerful techniques, such as collaborative filtering, which identifies patterns in user behavior, and content-based filtering, which recommends items with similar attributes. By addressing challenges like information overload and offering personalized suggestions, these systems play a critical role in enriching user satisfaction.

This project applies these principles to a university library setting, where students and researchers often face the difficulty of navigating extensive catalogs. By analyzing interactions between users and the library’s collection, the system predicts reading preferences and delivers targeted book suggestions. This real-world-inspired challenge demonstrates the importance of recommendation systems in improving user engagement and highlights the critical role of data science in designing innovative solutions.

# 2. Objectives
The primary objectives of this project are:

Develop a functional recommendation system using data science techniques:
Leverage user-book interaction data to design an efficient recommendation model. This includes data preprocessing, training algorithms, and optimizing results to ensure accuracy and relevance in the suggestions.

Address a personalization challenge in a real-world scenario:
Build a system capable of accurately predicting books that align with a user’s interests based on their interaction history and the metadata of the library’s catalog. This objective explores the potential of machine learning techniques in tackling personalization problems within an academic environment.

Improve the user experience for library users:
Enhance engagement with the library’s platform by delivering recommendations that simplify the discovery of relevant content. By creating a user-friendly system, the project emphasizes how technology can bridge the gap between massive digital catalogs and individual user needs.

Demonstrate the role of recommendation systems in modern platforms:
Highlight the importance of advanced algorithms, such as collaborative filtering and content-based techniques, in addressing challenges like information overload. This project aims to illustrate how such systems can transform the way users interact with and explore large collections of resources.

# 3. Méthodologie
## 3.1 Data Analysis
Before predicting the books that might interest users, we thoroughly cleaned and preprocessed the data to ensure its quality and suitability for training the model. The dataset columns were renamed for better clarity, and key columns such as identifiers (user_id, item_id) and timestamps were converted into appropriate formats. Invalid data, such as incorrect timestamps or rows with missing values in essential columns, were removed. Text fields, such as titles and subjects, were also standardized to enhance the overall consistency of the data. This cleaning process was a key step in preparing reliable and usable data for the recommendation model.

Before starting the processing steps, we reviewed the Excel files to familiarize ourselves with the structure and content of the data, which helped us better understand the available features. Finally, the Kaggle competition required a specific format for submitting predictions. At each stage, we ensured that our results strictly adhered to this format to guarantee compatibility with the evaluation system.

Here are the three datasets we received at the start of the project : 
**DATAAAAAAAAAAA sous forme de tableau comme chez Dimitri !!!!!!!!!!!!!!!!!!!!!!!!!!!**

# Analyse de la progression à travers les codes. 

We improved our predictions by moving from the first code, based on user-to-user similarity, to the second code, which uses a user-item matrix built from interaction timestamps. The first code only accounted for binary interactions (1 or 0), which overly simplified the data and did not truly reflect user behaviors, leading to approximate similarities and less relevant recommendations. In the second code, the timestamps indirectly prioritize items with multiple interactions, even though summing them is not ideal for capturing real interest since they only represent the dates and times of interactions. However, this method is more effective because it does not rely on user similarity calculations, which are often biased or computationally expensive, and better highlights frequently accessed items. While this code represents an improvement, there are still areas to refine, such as accounting for recent interactions or incorporating content-based approaches to diversify recommendations.



(0.1592 --> (pour la compréhension à supprimer !!)
En regroupant les interactions multiples par utilisateur et item, puis en additionnant les timestamps, on capture l'intensité d'intérêt de chaque utilisateur pour chaque item, ce qui reflète son engagement. Si un utilisateur interagit plusieurs fois avec le même item à différents moments, cela indique un intérêt plus fort pour cet item. En attribuant un score basé sur cette somme, on donne plus d'importance aux items avec lesquels les utilisateurs ont été fortement engagés, ce qui améliore la pertinence des prédictions dans les recommandations.)






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


