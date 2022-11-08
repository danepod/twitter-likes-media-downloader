# Twitter-Likes-Media-Downloader

Download all media from liked tweets from a Twitter account by using the Tweet IDs from a data export.

This is a fork of https://github.com/reinhartP/twitter-likes-media-downloader, which loaded the list of likes by
querying Twitter's API. This had the limitation that only the newest ~3000 liked tweets could be fetched. The data
export offered by Twitter however contains the IDs of _all_ liked tweets, so we can use that to download the media of
every liked tweet.

## Instructions

- Request a download of your Twitter data at https://twitter.com/settings/download_your_data
- Create an application at https://developer.twitter.com, try to answer the questionnaire in a way that makes them
  accept your request

- Replace the first line in `data/like.js` with `[` and filter out the tweet ids with `jq -r .[].like.tweetId like.js > like.txt`
- Install dependencies `pip install python-twitter pandas`
- Generate base config file with `python twitter_likes.py -g`
- Fill in config file `config.json` with API keys
- Run with `python twitter_likes.py -u "twitter username" --id-dump likes.txt`
