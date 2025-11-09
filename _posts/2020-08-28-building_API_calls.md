---
layout: post
title: Building an API
subtitle: Create an easy-to-use Spotify API
image: img/Spotify.jpg
gh-repo: Edudeiko/dj_helper_search_api
gh-badge: [star, fork, follow]
tags: [API, Flask, Machine Learning, Python, KNN, Spotify, Heroku]
comments: true
---

While working on this project, I couldn't find the Spotify API calls I needed. At the time, I was looking for the following: 

**1)** Search function that returns **Artist Name**, **song name**, **song ID**, **external URL** (handy for listening to the full song), **explicit** flag (True or False), **preview** (30-second clip), and a cover **image** for each song. 

**2)** All of the above plus **audio features** for the searched songs. Audio features include acousticness, danceability, energy, instrumentalness, key, liveness, etc. These features can be used to create visualizations and predict similar songs. 

**3)** I was also asked to create a prediction model to retrieve a desired number of similar songs. The model needed to use audio features to suggest similar songs.

All results needed to be in a readable JSON format for the backend team to use.

### Register Spotify for Developers account
Before getting into the code you have to register an account at [Spotify for Developer](https://developer.spotify.com) and create an app in order to get **Client ID** and **Client Secret** keys. In edit settings add **Redirect URIs**. I added http://127.0.0.1:5000/callback/ and
https://sp-search.herokuapp.com/callback/. 

{: .box-note}
**Note:** You need to change URIs to your own localhost and to the host you will deploy your APIs to.

By the end of the project, I created 3 APIs. The [first](https://sp-search.herokuapp.com/track_search_ready/test) searches for a track, the [second](https://sp-search.herokuapp.com/audio_features/in-to-the-sun) searches for a track and returns 10 tracks with audio features, and the [third](https://sp-search.herokuapp.com/predict/4R2kfaDFhslZEMJqAFNpdd) returns the 4 most similar songs based on audio features using K-Nearest Neighbors. I deployed the APIs on Heroku and shared them with the backend team.

You can find the full code [here](https://github.com/Edudeiko/dj_helper_search_api/blob/master/run.py)

