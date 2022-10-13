# Project: Wrangling and anlysing Twitter Data

## By (Yaninthé Tiomene)

### Introduction
>Real-world data rarely comes clean. The aim of this project is: by using Python and its libraries, we will gather data from a variety of sources and in a variety of formats, assess its quality and tidiness, then clean it. We will document our wrangling efforts in a Jupyter Notebook, plus showcase them through analyses and visualizations using Python (and its libraries) and/or SQL.


### Dataset
>The dataset that we will be wrangling (and analyzing and visualizing) is the tweet archive of Twitter user _@dog_rates_, also known as [WeRateDogs](https://en.wikipedia.org/wiki/WeRateDogs). WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because [_"they're good dogs Brent."_](https://knowyourmeme.com/memes/theyre-good-dogs-brent) WeRateDogs has over 4 million followers and has received international media coverage. The WeRateDogs [_Twitter archive_](https://help.twitter.com/fr/managing-your-account/how-to-download-your-twitter-archive)  contains basic tweet data (tweet ID, timestamp, text, etc.) for all 5000+ of their tweets as they stood on August 1, 2017. Additional data will be gathered from Twitter's API. These include:

1. The tweet image predictions file : every image in the WeRateDogs Twitter archive went through a neural network that can classify breeds of dogs. 
2. tweet_json.txt file :Using the tweet IDs in the WeRateDogs Twitter archive, we query the Twitter API for each tweet's JSON data using Python's Tweepy library and store each tweet's entire set of JSON data in a file.


### Quality issues
1. In `twitter_archive` and `images` datasets `tweet_id` is in int64 datatype

2. There are retweets rows in the `twitter_archive` table

3. `in_reply_to_status_id`, `in_reply_to_user_id`, `retweeted_status_id`, and `retweeted_status_user_id`, contain more than 80% of nulls values 

4. `name`, `doggo`, `flooter`, `pupper` and `puppo` have *None* values

5. `timestamp` variable is in object datatype not in datetime

6. `source` contains 4 unique values containing : *iPhone*, *Vine*, *Web* and *TweetDeck* .

7. Some `name` are incorect, and start in lowercase.

8. Minimum `rating_denominator` is 0 instead of 10, and the maximum is 170 istead of 10 - Multiple `rating_denominator` instead of one unique. 

9. Minimum `rating_numerator` is 0, and the maximum is 1176. There are `rating_numerator` bigger than 15.


### Tidiness issues
1. `tweet_count` and `images` tables should be part of the `twitter_archive` table.

2. `expanded_urls`, `jpg_url`, and `img_num` are useless column.

3. `doggo`, `floofer`, `pupper` and `puppo` should be grouped in one column `age_stage`.

4. `p1`, `p2`, `p3`, `p1_conf`, `p2_conf`, `p3_conf`, `p1_dog`, `p2_dog`, `p3_dog`, should be used to extract the only one `bread` column. 

5. `rating_numerator` and `rating_denominator` should be grouped in one column `rating`. 


### Keys Insights for presentations:
1. The most favorite and retweeted tweet from the dataset has the tweet_id **744234799360020481** posted on an iPhone, on the 2016-06-18 at 18:26:18, the dog was at the `doggo` age_stage and was rated **13/10**

2. The top 10 rated names are: `Sundance`, `Laika`, `Clifford`, `Iggy`, `Smiley`, `General`, `Emmy`, `Kuyu`, `Cermet`, `Doobert` with an average rating of `14/10` each

3. The top 10 rating breads are `Bouvier_des_Frandes`, `Saluki`, `Tibetan_mastiff`, `briard`, `Border_terrier`, `silky_terrier`, `standard_schnauzer`, `Irish_setter`, `Gordon_setter`, and `Samoyed` with rating from `13/10` to `12/10` respectively

4. There is a positive but not high correlation between `rating` and `favorite_count`, then `rating` and `retweet_count`.

5. The top 10 most used names in tweet are `Charlie`, `Cooper`, `Oliver`, `Tucker`, `Lucy`, `Penny`, `Winston`, `Sadie`, `Lola`, and `Toby`
6. The most used source of tweet is `iPhone` with more than 98% users