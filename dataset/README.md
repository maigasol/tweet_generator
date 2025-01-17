# Tutorial: Extracting Tweets Using Tweepy and Saving in JSONL Format

This tutorial walks you through extracting tweets from a specific user's timeline using the Tweepy library and saving the extracted tweets in **JSON Lines (JSONL)** format. JSONL is a convenient format for handling large datasets where each line is a valid JSON object.

## Prerequisites
**1. Install Tweepy** library using pip:
   
```bash
pip install tweepy
```

**2.** Set Up a Twitter Developer Account:
- Sign up at the [Twitter Developer Platform](https://developer.x.com/en).
- Recent updates to the twitter api have significatly reduce the free tier limits. So you may search kaggle to see if the dataset you are looking for is publicly avialable, before paying for a monthly subscription.
- Create a new project and generate your API keys and access tokens.

```python
import tweepy

# Replace with your API keys
API_KEY = "your_api_key"
API_SECRET = "your_api_secret"
ACCESS_TOKEN = "your_access_token"
ACCESS_TOKEN_SECRET = "your_access_token_secret"

# Authenticate with Tweepy
auth = tweepy.OAuth1UserHandler(API_KEY, API_SECRET, ACCESS_TOKEN, ACCESS_TOKEN_SECRET)
api = tweepy.API(auth)
```

