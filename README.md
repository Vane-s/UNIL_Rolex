# DSML-Rolex-Project-Recommendation System 

 ![image](https://github.com/user-attachments/assets/e2aa8bb9-04f7-4775-9cda-a53d75bcb4c9)



# 1. Introduction

In today’s digital age, recommendation systems have become indispensable tools for personalizing user experiences and making vast collections of content or products more accessible. This project, part of a Data Science and Machine Learning course, focuses on developing a personalized recommendation system for a university library. The goal is to enhance the user experience by helping students and researchers discover books that align with their interests and academic needs.

Recommendation systems analyze user preferences and interactions to provide tailored suggestions. They are widely used across industries, from streaming platforms (Netflix, Spotify) to e-commerce (Amazon) and social media (YouTube, TikTok). These systems leverage powerful techniques, such as collaborative filtering, which identifies patterns in user behavior, and content-based filtering, which recommends items with similar attributes. By addressing challenges like information overload and offering personalized suggestions, these systems play a critical role in enriching user satisfaction.

This project applies these principles to a university library setting, where students and researchers often face the difficulty of navigating extensive catalogs. By analyzing interactions between users and the library’s collection, the system predicts reading preferences and delivers targeted book suggestions. This real-world-inspired challenge demonstrates the importance of recommendation systems in improving user engagement and highlights the critical role of data science in designing innovative solutions.

# 2. Objectives

The primary objectives of this project are:

- **Develop a functional recommendation system using data science techniques:** Leverage user-book interaction data to design an efficient recommendation model. This includes data preprocessing, training algorithms, and optimizing results to ensure accuracy and relevance in the suggestions.

- **Address a personalization challenge in a real-world scenario:** Build a system capable of accurately predicting books that align with a user’s interests based on their interaction history and the metadata of the library’s catalog. This objective explores the potential of machine learning techniques in tackling personalization problems within an academic environment.

- **Improve the user experience for library users:** Enhance engagement with the library’s platform by delivering recommendations that simplify the discovery of relevant content. By creating a user-friendly system, the project emphasizes how technology can bridge the gap between massive digital catalogs and individual user needs.

- **Demonstrate the role of recommendation systems in modern platforms:** Highlight the importance of advanced algorithms, such as collaborative filtering and content-based techniques, in addressing challenges like information overload. This project aims to illustrate how such systems can transform the way users interact with and explore large collections of resources.

# 3. Methodology

## 3.1 Data Analysis
Before predicting the books that might interest users, we thoroughly cleaned and preprocessed the data to ensure its quality and suitability for training the model. The dataset columns were renamed for better clarity, and key columns such as identifiers (user_id, item_id) and timestamps were converted into appropriate formats. Invalid data, such as incorrect timestamps or rows with missing values in essential columns, were removed. Text fields, such as titles and subjects, were also standardized to enhance the overall consistency of the data. This cleaning process was a key step in preparing reliable and usable data for the recommendation model.

Before starting the processing steps, we reviewed the Excel files to familiarize ourselves with the structure and content of the data, which helped us better understand the available features. Finally, the Kaggle competition required a specific format for submitting predictions. At each stage, we ensured that our results strictly adhered to this format to guarantee compatibility with the evaluation system.

Here are the three datasets we received at the start of the project : 

**interactions_train.csv** : interactions between a user and a book and the timestamp of the interaction 

|      u               |      i           |   t           |  
|----------------------|------------------|---------------|  
| 4456                 | 8581             | 1687541086.0  |  
| 142                  | 1964             | 1679585406.0  |  
| ...                  | ...              | ...           | 

**items.csv** : books metadata 

| Title | Author | ISBN Valid | Publisher | Subjects | i |
|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|
|Classification décimale universelle : édition abrégée | NaN | 9782871303336; 2871303339 | Ed du CEFAL | Classification décimale universelle; Indexation (documentation); classification | 0|
| Les interactions dans l'enseignement des langues : agir professoral et pratiques de classe | Cicurel, Francine, 1947- | 9782278058327; 2278058320 | Didier | didactique--langue étrangère - enseignement; didactique--langue - | 1 |
| ... | ... | ... | ... | ... | ... |

**sample_submission-csv** : exemple of submission for the Kaggle competition 

| user_id | recommendation |
|:---------:|:---------:|
| 0 | 3758 11248 9088 9895 5101 6074 9295 14050 10961 8240 |
| 1 | 3263 726 1589 14911 6432 10897 6484 7961 8249 3567 |
| ... | ... |

## 3.2 Model Exploration
The code implements a recommendation system based on collaborative filtering. It starts by importing essential libraries such as NumPy, Pandas, and sklearn, followed by loading two datasets: user-book interactions and book information. The interactions are sorted by user and timestamp to maintain chronological order, allowing the model to capture the evolution of user preferences.

The dataset was then split into training and test sets in a specific way: a new column called pct_rank was created to compute the relative rank of each interaction for a user based on the timestamps. This ensures that the most recent interactions for each user are included in the test set, simulating a realistic scenario where recent interactions are used to evaluate the model’s ability to predict future interactions.- 

A user-item matrix was then constructed from the data. Each row represents a user, each column a book, and the values indicate a binary interaction (1 for an interaction, 0 otherwise). This matrix is the foundation of the collaborative filtering algorithms, as it encodes the interaction history between users and books.

Two types of similarity matrices were calculated using cosine similarity:

- **The item-item similarity matrix**, which measures the similarity between books based on user interactions. The idea is that books with similar interaction patterns are likely to be enjoyed by the same users.
- **The user-user similarity matrix**, which measures the similarity between users based on their interactions with books. This helps identify users with similar tastes.

Two prediction methods were used to estimate future interactions:
- **Item-based predictions**, which calculate the likelihood of interaction by taking a weighted sum of interactions with similar books.
- **User-based predictions**, which estimate interactions based on the preferences of other users with similar behaviors.

To evaluate the quality of the recommendations, the **Precision@K** and **Recall@K** metrics were calculated to compare the performance of the item-based and user-based approaches. The **user-based approach** performed slightly better on both metrics, as shown in the table below.

|   Technique          |   Precision@10   |   Recall@10   |  
|----------------------|------------------|---------------|  
| User-to-User CF      | 0.0565           | 0.2906       |  
| Item-to-Item CF      | 0.0556           | 0.2639       |    

Next, we attempted an initial prediction by training the model only on the training data. The generated predictions were saved in a CSV file and submitted to the competition, which calculated a precision score of **0.1241** for our predictions. In response, we decided to retrain the model on the entire dataset (including both training and test sets). Once the new predictions were submitted, the resulting CSV file achieved an improved precision score of **0.1452**. This improvement is due to the model having access to the full dataset, which allowed it to learn better and make more accurate predictions.

Finally, the top 10 most relevant recommendations for each user were generated by sorting the prediction scores in descending order. These recommendations were exported to a CSV file, adhering to the requirements of a Kaggle submission or other external evaluations. This recommendation system demonstrates an efficient and well-structured solution for delivering personalized recommendations based on user preferences.

## 3.3 Advancing to a More Sophisticated Model
We improved our predictions by moving from the first code, based on user-to-user similarity, to the second code, which uses a user-item matrix built from interaction timestamps. The first code only accounted for binary interactions (1 or 0), which overly simplified the data and did not truly reflect user behaviors, leading to approximate similarities and less relevant recommendations. In the second code, the timestamps indirectly prioritize items with multiple interactions, even though summing them is not ideal for capturing real interest since they only represent the dates and times of interactions. This approach better highlights frequently accessed items and led to a significant improvement in our score, moving from **0.1452** with the first code to **0.1592** with the second. While this code represents an improvement, there are still areas to refine, such as accounting for recent interactions or incorporating content-based approaches to diversify recommendations.

In the third code, we introduced several improvements to enhance the prediction quality compared to the second code. One of the major enhancements is the use of **time decay**, which incorporates the notion of recency into interactions. Unlike the second code, which relied solely on the raw sum of timestamps to measure interaction intensity, the third code applies an exponentially decreasing weighting based on the age of interactions. This approach prioritizes recent interactions, which are more representative of users' current preferences, while reducing the influence of older interactions. By combining this weighting with the frequency of interactions, the model reflects both users' overall engagement and their current tastes, making the recommendations more dynamic and relevant.

Additionally, we adopted a **hybrid approach** that combines two types of similarities: **user-to-user** and **item-to-item**. User-to-user similarity identifies users with similar preferences, while item-to-item similarity highlights items often consumed together or sharing similar characteristics. These similarities, calculated using **cosine similarity**, enrich the recommendations by capturing both collective behaviors and direct relationships between items.

To balance the contributions of these two approaches, we introduced a **weighted hybrid model**. This model dynamically adjusts the weights assigned to each similarity type (e.g., 70% for user-to-user and 30% for item-to-item), allowing us to optimize recommendations based on the available data. We also manually fine-tuned these weights to assess their impact on prediction quality, achieving our best prediction score of 0.1694 with a specific weighting. This highlights the importance of precise adjustments to maximize performance.

These improvements allowed us to increase the prediction score from **0.1592** in the second code to **0.1694** with the third model. This progress demonstrates the importance of incorporating factors such as interaction recency, fine-grained user and item similarities, and a flexible balance between the two approaches. While this model is effective, there are still opportunities for improvement, such as integrating item metadata or exploring advanced machine learning models to achieve even better results.

## 3.4 Our Best Model

To improve prediction quality, we focused on leveraging item textual metadata and incorporating textual similarities into the recommendation model. First, we cleaned and standardized the item metadata (e.g., title, author, subjects) by removing special characters, normalizing uppercase and lowercase letters, and eliminating unnecessary spaces. This step ensured uniformity and reduced noise in the data, making relationships between items more coherent. Then, we initially used a pre-trained model, DistilRoBERTa, to generate semantic embeddings from the cleaned metadata, enabling the capture of subtle textual relationships between items that were not visible through user-item interactions alone.

By testing another pre-trained model, **"multi-qa-MiniLM-L6-cos-v1"**, we achieved a slight improvement in the prediction score, increasing it from **0.1695 to 0.1696**. This model provided slightly more accurate embeddings to evaluate textual similarities between items. These similarities helped identify items sharing semantic features, such as books in the same genre, by the same author, or addressing similar themes. However, the improvement in prediction quality was not as significant as initially expected with the addition of embeddings to our code. This indicates that, while leveraging metadata enhances recommendations, further adjustments or complementary approaches might be necessary to maximize the impact of these embeddings on the overall model.



# 4. Challenge

# 5. Conclusion

## 5.1 Kaggle Competition Results


## 5.2 YouTube Video :
[Insert link to your presentation video]

# 6. Team
Our project was led by Sasha Granelli and Vanessa Faller, Master's students specializing in Law, criminality and security of information.




