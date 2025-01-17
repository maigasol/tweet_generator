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

**3.** Extract Tweets from a User

```python
# Function to fetch all tweets from a user
def fetch_all_tweets(username):
    all_tweets = []
    try:
        # Initial request for the most recent tweets
        new_tweets = api.user_timeline(screen_name=username, count=200, tweet_mode="extended")
        all_tweets.extend(new_tweets)
        
        # Keep fetching until no more tweets are left
        while len(new_tweets) > 0:
            print(f"Fetched {len(all_tweets)} tweets so far...")
            # Get tweets older than the oldest tweet in the last batch
            max_id = all_tweets[-1].id - 1
            new_tweets = api.user_timeline(screen_name=username, count=200, max_id=max_id, tweet_mode="extended")
            all_tweets.extend(new_tweets)
        
        print(f"Total tweets fetched: {len(all_tweets)}")
        return all_tweets

    except tweepy.TweepError as e:
        print(f"Error: {e}")
        return all_tweets

# Fetch tweets from a specific user and save them to a file
username = "realDonaldTrump"  # Replace with the Twitter username
tweets = fetch_all_tweets(username)
```

```python
username = "realDonaldTrump"
tweets = fetch_all_tweets(username)
save_path = "tweets.jsonl"
with open(save_path, "w", encoding="utf-8") as file:
    for tweet in tweets:
        json_tweet = tweet._json  # Convert Tweepy Status object to JSON
        file.write(json.dumps(json_tweet) + "\n")
print(f"Tweets saved to {filename}")
```
