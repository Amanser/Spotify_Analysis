![alt text](https://github.com/Amanser/Spotify_Analysis/blob/master/SongMetrics_Presentation/Images/spotify_logo.png)

# Spotify Song Metric Analysis

* A collaborative effort between Austen Manser, [William Nash](https://github.com/wwenash), and Cody Braun

* Data analysis exploring the relationship between the audio features of songs that made it to the number one spot on the Billboard 100 list and songs that did not.


## Song Metrics Explained

All metrics are scored based on a confidence measure from 0.0 to 1.0

**Acousticness:** A measure of whether the track is acoustic (i.e. not having electrical amplification). The higher the value, the more acoustic the song.

**Danceability:** Describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. The higher the value, the easier it is to dance to the song. 

**Energy:** Represents a perceptual measure of intensity and activity - the higher the value, the more energetic the song. Typically, energetic tracks feel fast, loud, and noisy. For example, death metal has a high energy, while a Bach prelude scores low on the scale. Perceptual features contributing to this attribute include dynamic range, perceived loudness, timbre, onset rate, and general entropy.

**Valence:** Describes the musical positiveness conveyed by a track. Tracks with a higher valence sound more positive (i.e. happy, cheerful, euphoric), while tracks with low valence convey a more negative sound (i.e. sad, depressed, angry).

**Instrumentalness:** Predicts whether a track contains no vocals. Sounds such as "ooh" and "aah" are treated as instrumental in this context. Rap or spoken word tracks are clearly "vocal". The higher the value, the greater the likelihood that the track contains no vocal content. Values above 0.5 are intended to represent instrumental tracks, but the confidence is higher as the value approaches 1.0.

**Speechiness:** Detects the presence of spoken words in a track. The more exclusively speech-like the recording (i.e. talk show, audio book, poetry), the closer the attribute value is to 1.0.

**Liveness:** Detects the presence of an audience in the recording. Higher liveness values represent an increased probability that the track was performed live. A value above 0.8 provides a strong likelihood that the track is live.
