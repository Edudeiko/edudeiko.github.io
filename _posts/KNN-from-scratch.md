---
layout: post
title: KNN from scratch
subtitle: KNN step by step guide  
image: img/KNN.jpg
gh-repo: Edudeiko/CS-Data-Science-Build-Week-1
---

Start with building class KNN. It will include Standard Scaler, Euclidean distance, predict and accuracy score for an outcome. 
**1)** Create the class KNN itself.
```javascript
class KNN:
  '''K-Nearest Neighbour Classifier'''
  def __init__(self, target_classes):
    '''Specify a number of target classes'''
    self.target_classes = target_classes
```
**2)** Then I created a small load dataset function to load data.
{: .box-note}
**Note:** It takes a list of arrays. You might want to modify it if you'll load it from another source.
```javascript
def load_data(self, filename):
  '''loads array list'''
  dataset = list()
  for row in filename:
    dataset.append(row)
  return dataset
```
**3)** Create a step-by-step Standard Scaler function
#### StandardScaler
```javascript
    def fit(self, X):
        '''scale the data'''
        self.mean_X = np.mean(X, axis=0)  # compute mean
        self.scaled_X = np.std(X - self.mean_X, axis=0)  # compute standard deviation
        return self

    def transform(self, X):
        '''transform data'''
        return (X - self.mean_X) / self.scaled_X

    def fit_transform(self, X):
        '''fit_transform data'''
        return self.fit(X).transform(X)
```
Shortend version would be
```javascript
  def scale(X):
    X_scaled = X - np.mean(X)  # from dataset substract mean dataset
    return X_scaled / np.std(X)  # above result devide on standard deviation of the dataset
```




at [Spotify for Developer](https://developer.spotify.com) and create an app in order to get **Client ID** and **Client Secret** keys. In edit settings add **Redirect URIs**. I added http://127.0.0.1:5000/callback/ and
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

