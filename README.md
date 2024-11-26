# UNIL_Rolex

#Team Members : 
-Vanessa Faller 
-Sasha Granelli 

#Project Description : 
As part of our Data Mining and Machine Learning project, we are tasked with enhancing a university's library platform by developing a personalized book recommendation system. The system will use collaborative filtering techniques to analyze implicit feedback data and generate book suggestions based on the individual books preferences. By delivering more relevant and tailored recommendations, the system aims to boost user engagement and help users effortlessly discover books that align with their interests.

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


