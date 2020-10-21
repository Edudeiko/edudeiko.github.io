---
layout: post
title: KNN from scratch
subtitle: KNN step by step guide  
image: img/KNN.jpg
gh-repo: Edudeiko/CS-Data-Science-Build-Week-1
---

Start with building class KNN. It will include Standard Scaler, Euclidean distance, predict and accuracy score for an outcome. 
First I created a small load dataset function to load data.

```javascript
def load_data(self, filename):
  '''loads array list'''
  dataset = list()
  for row in filename:
    dataset.append(row)
  return dataset
```

**1)** Search function which will deliver **Artist Name**, **song name**, **song ID**, **external URL** is handy to listen for a whole song, **explicit** has two values True or False, **preview** gives you 30 seconds to listen a song and a cover **image** for the specific song. 

**2)** All of the above plus the **audio features** for the searched songs. Audio features contain acousticness, danceability, energy, instrumentalness, key, liveness etc. The audio features can be used to create visualizations and to predict similar songs. 

**3)** Also I was requested to create a predicting model in order to get the desired amount of similar songs. The model had to use audio features to suggest similar songs.

All of the results had to be in a nice readable json format for the backend team to use.

### Register Spotify for Developers account
Before getting into the code you have to register an account at [Spotify for Developer](https://developer.spotify.com) and create an app in order to get **Client ID** and **Client Secret** keys. In edit settings add **Redirect URIs**. I added http://127.0.0.1:5000/callback/ and
https://sp-search.herokuapp.com/callback/. 

{: .box-note}
**Note:** You need to change URIs to your own localhost and to the host you will deploy your APIs to.

## To be continued

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

