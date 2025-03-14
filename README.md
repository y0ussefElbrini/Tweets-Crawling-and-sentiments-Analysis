 # Project: Crawling and Sentiment Analysis

 ## 1️⃣ Prerequisites

Before you begin, ensure you have the following installed on your system:
- Python 3.x
- Jupyter Notebook (optional but recommended for interactive development)
- Git (optional for version control)

## 2️⃣ Setting up a Twitter Developer Account

To use the Twitter API with Tweepy, you need to create a developer account and obtain API credentials:

1. Go to [Twitter Developer Portal](https://developer.twitter.com/).
2. Sign up and create a new application.
3. Once approved, navigate to the **Keys and Tokens** section.
4. Generate the following credentials:
   - API Key
   - API Secret Key
   - Access Token
   - Access Token Secret
5. Store these securely, as they will be required for authentication in Tweepy.

## 3️⃣ Installing Required Libraries

To install the required libraries in jupyter notebook, use the following command:

```bash
!pip install tweepy nltk numpy scikit-learn pickle-mixin
```

# Partie 1 : Algorithme de crawling de données:

![image](https://user-images.githubusercontent.com/94408863/141861457-180cea9c-9de2-4e97-9bb2-4508e3eccc5c.png)

1. The **Tweepy** library is used for web scraping. After authentication, I retrieved **600 tweets** using `tweepy.Cursor` to iterate over Twitter pages with `api.search`.
2. The data from each tweet was written to a separate text file.
3. Then, I manually labeled **400 tweets** based on the information they contained (this step was quite tedious but worth it 😃!):

- Positive Opinion
- Negative Opinion
- Question-based Opinion
- Neutral Opinion (includes tweets that are neutral, unclear, or difficult to classify)
- Sarcasm
- Repetitive (if a tweet was repeated): only 3 tweets were duplicated due to the use of the filter `-filter:retweets` in the hashtag search, which excluded retweeted tweets.
- Tweets containing only a link

**The result was as follows:**

![image](https://user-images.githubusercontent.com/94408863/141862644-6f24403f-b1e2-4c3c-a483-858016249f76.png)

**And inside each folder, there are multiple tweets saved as text files. For example, the folder for positive tweets:**

![image](https://user-images.githubusercontent.com/94408863/141862694-ac3c9fb4-6ad7-435d-a9e2-86dfa98d515e.png)

# Part 2: Model for Predicting Tweet Sentiments

For this part, I built a model to classify tweets into **two classes: positive and negative**. (Handling more classes would be difficult with only 400 tweets, and most tweets were tagged as "Neutral Opinion" or other categories.)

I chose to use the **RandomForestClassifier**, with **RandomizedSearchCV** for hyperparameter optimization. **RandomizedSearchCV** is faster than **GridSearchCV** because it explores only a subset of parameters rather than testing all combinations.

**The model follows this approach:**

![image](https://user-images.githubusercontent.com/94408863/141862866-b44a84a0-b454-40a2-a15b-a1493cc76103.png)

**The result is as follows:**

![image](https://user-images.githubusercontent.com/94408863/141862906-9b98e4eb-ce5c-4aa1-93df-6ace108bb026.png)

This project provides a complete pipeline for **collecting, labeling, and classifying sentiment from tweets**. Future improvements could involve deep learning models for enhanced accuracy.
