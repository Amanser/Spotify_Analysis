![alt text](https://github.com/Amanser/Spotify_Analysis/blob/master/SongMetrics_Presentation/Images/spotify_logo.png)

# Spotify Song Metric Analysis

* An exploratory data analysis delving into the relationship between the audio features of songs that made it to the number one spot on the Billboard Hot 100 list and songs that did not.

* A collaborative effort between Austen Manser, [William Nash](https://github.com/wwenash), and [Cody Braun](https://github.com/codybraun1)

## Song Metrics Explained

All metrics are scored based on a confidence measure from 0.0 to 1.0

**Acousticness:** A measure of whether the track is acoustic (i.e. not having electrical amplification). The higher the value, the more acoustic the song.

**Danceability:** Describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. The higher the value, the easier it is to dance to the song. 

**Energy:** Represents a perceptual measure of intensity and activity - the higher the value, the more energetic the song. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has a high energy, while a Bach prelude scores low on the scale. Perceptual features contributing to this attribute include dynamic range, perceived loudness, timbre, onset rate, and general entropy.

**Valence:** Describes the musical positiveness conveyed by a track. Tracks with a higher valence sound more positive (i.e. happy, cheerful, euphoric), while tracks with low valence convey a more negative sound (i.e. sad, depressed, angry).

**Instrumentalness:** Predicts whether a track contains no vocals. Sounds such as "ooh" and "aah" are treated as instrumental in this context. Rap or spoken word tracks are clearly "vocal". The higher the value, the greater the likelihood that the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but the confidence is higher as the value approaches 1.0.

**Speechiness:** Detects the presence of spoken words in a track. The more exclusively speech-like the recording (i.e. talk show, audio book, poetry), the closer the attribute value is to 1.0.

**Liveness:** Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live. A value above 0.8 provides a strong likelihood that the track is live.


## Hypothesis

**H<sub>0</sub>:** There is no difference in Spotify song features between songs that have been number one and have not been number one on the Billboard Hot 100 list since 1958.

**H<sub>1</sub>:** There is a correlation between Spotify song metrics (Popularity, Danceability, Valence, etc.) on number one songs on the Billboard Hot 100 since 1958 and songs that did not make number one on Billboard Hot 100.


## Quick Summary

Through our analysis, we strongly believe that there is no overall significant difference in the song metrics between songs that claimed the number one spot on the Billboard Hot 100 and songs that were on the Billboard Hot 100, but never reached number one.


## Data Mining, Cleanup, and Exploration


* Utilized wrappers for Billboard API(Billboard.py) and Spotify API (Spotipy)

* The full list of songs (excluding duplicates) pulled from the Billboard API was over 28,000.

* As Spotify does not have a universal naming system for tracks/artists, **fuzzy matching** was utilized in order to match up the data from the Billboard Hot 100 into the Spotify API.
  * Fuzzy matching is a method that provides an improved ability to process string-based matching queries to find matching phrases or sentences from a database.
  * Fuzzy ratio is based on Levenshtein distance (LD) which is a measure of the similarity between two strings, which we will refer to as the source string (s) and the target string (t). The distance is the number of deletions, insertions, or substitutions required to transform s into t.
  * A fuzzy ratio threshold of 75 was used for our matching.

```
from fuzzywuzzy import fuzz

for x in range(len(results["tracks"]["items"])):
            song = results["tracks"]["items"][x]["name"]
            artist = results["tracks"]["items"][x]["artists"][0]["name"]
            search_song_name.append(song+", "+artist)
            search_match_score.append(fuzz.ratio(test_song,song+","+artist))
            search_match_score_song.append(fuzz.ratio(csv_df.iloc[i,1],song))
            search_match_score_artist.append(fuzz.ratio(csv_df.iloc[i,2],artist))
```

* Further issues arose with the Spotify API timing out while trying to request metrics for so many tracks. The retrieval process was broken into separate loops and different API keys needed to be swapped in to continue.


* The Billboard non-number one list was parsed down from 28,00 to 20,040 songs of which were able to retrieve metrics from the Spotify API. The final Billboard number one list with metrics was 857 songs.


## Findings

Overall, our Null hypothesis was confirmed in that there is no statistical difference in song metrics of tracks that were number one on the Billboard Hot 100 and those songs that never reached the number one position.
 * The only metric that returned a p-value of less that 0.005 was Acousticness.

![Image](https://github.com/Amanser/Spotify_Analysis/blob/master/SongMetrics_Presentation/Images/Dataframe_pvals.PNG)


When the songs are binned by decade, there arises some statistical significance among the different metrics.


![Image](https://github.com/Amanser/Spotify_Analysis/blob/master/SongMetrics_Presentation/Images/Decades_pvals.png)


Box and whisker plots of the data ranges of the confidence measures for the entire history of the Billboard Hot 100


![Image](https://github.com/Amanser/Spotify_Analysis/blob/master/SongMetrics_Presentation/Images/number1_vs_non_overall.png)







