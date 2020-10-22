---
layout: post
title: K-Nearest Neighbors algorithm from scratch
subtitle: KNN a step by step guide  
image: img/KNN.png
---
**KNN** can be used for both classification and regression predictive poblems. Mostly it’s more used in classification problems.

Start by building class **KNN**. It will include **Standard Scaler**, **Euclidean distance**, **predict** and **accuracy score** for an outcome. You can find the code and some extra [on my GitHub page](https://github.com/Edudeiko/CS-Data-Science-Build-Week-1)

**1)** Create the class KNN. I will use target_classes to specify the number of classes.

```javascript
class KNN:
    '''K-Nearest Neighbour Classifier'''
    def __init__(self, target_classes):
      '''Specify a number of target classes'''
      self.target_classes = target_classes
```
**2)** Then I created a load dataset function to load data

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
    self.mean_X = np.mean(X, axis=0)
    self.scaled_X = np.std(X - self.mean_X, axis=0)
    return self

def transform(self, X):
    '''transform data'''
    return (X - self.mean_X) / self.scaled_X

def fit_transform(self, X):
    '''fit_transform data'''
    return self.fit(X).transform(X)
```

Shortend version. From dataset substract mean dataset, devide the result on standard deviation of the dataset

```javascript
def scale(X):
    X_scaled = X - np.mean(X)
    return X_scaled / np.std(X)
```

**4)** fit_ the train data before predict

```javascript
def fit_(self, X, y_train):
    '''fit train data before predict'''
    self.X_train = X
    self.y_train = y_train
```

**5)** Create Euclidean distance function = sqrt(sum i to N (x1_i – x2_i)^2)

```javascript
def euclidean_distance(self, row1, row2):
    '''Euclidian distance'''
    return np.sqrt(np.sum((row1 - row2) ** 2))
```

You can print out the results of the Euclidean distance to look at the results.

```javascript
row0 = dataset[0]
'''you can compare any row in the dataset'''
for row in dataset:
    distance = euclidean_distance(row0, row)
    print(distance)
```

**6)** Predict function. We iterate through the test data and each row of training data to calculate the distance between them. I used the Euclidean distance as a distance metric. You can explore the other metrics. Sort the result from in ascending order based on distance values. For each neighbor find the target class. 

```javascript
def predict(self, X_test):
    '''predict the distance of KNN'''
    y = np.zeros(len(X_test))

    '''iterate through the test set'''
    for ii in range(len(X_test)):

        '''distance between test indices and all of the training set indices'''
        distance = np.array([self.euclidean_distance(X_test[ii], x_ind) for x_ind in self.X_train])

        '''sort index from ascending to descending order of target classes'''
        distance_sorted = distance.argsort()[:self.target_classes]

        '''for each neighbor find the target_class'''
        nearest_label = [self.y_train[ii] for ii in distance_sorted]

        y[ii] = max(set(nearest_label), key = nearest_label.count)

    return y
```

**7)** Perform an accuracy score.

```javascript
def accuracy(self, y_test, y_pred):
    '''print an accuracy score'''
    return f'Accuracy score: {np.mean(y_test==y_pred)}'
```

If you’ve been reading for these long here is the whole code from the above.

<script
src="https://gist.github.com/Edudeiko/abbbcf0e70b8b638191f7acb197924b7.js">
</script>

## Now we can test created KNN algorithm on a breast cancer dataset

#### Features are computed from a digitized image of a fine needle aspirate of a breast mass. They describe characteristics of the cell nuclei present in the image.

a) radius (mean of distances from center to points on the perimeter)

b) texture (standard deviation of gray-scale values) 

c) perimeter 

d) area 

e) smoothness (local variation in radius lengths) 

f) compactness (perimeter^2 / area - 1.0) 

g) concavity (severity of concave portions of the contour)

h) concave points (number of concave portions of the contour) 

i) symmetry 

j) fractal dimension ("coastline approximation" - 1)

**The mean, standard error and "worst" or largest (mean of the three largest values) of these features were computed for each image, resulting in 30 features:**

- 1 - mean radius
- 2 - mean texture
- 3 - mean perimeter
- 4 - mean area
- 5 - mean smoothness
- 6 - mean compactness
- 7 - mean concavity
- 8 - mean concave points
- 9 - mean symmetry
- 10 - mean fractal dimension
- 11 - radius error
- 12 - texture error
- 13 - perimeter error
- 14 - area error
- 15 - smoothness error
- 16 - compactness error
- 17 - concavity error
- 18 - concave points error
- 19 - symmetry error
- 20 - fractal dimension error
- 21 - worst radius
- 22 - worst texture
- 23 - worst perimeter
- 24 - worst area
- 25 - worst smoothness
- 26 - worst compactness
- 27 - worst concavity
- 28 - worst concave points
- 29 - worst symmetry
- 30 - worst fractal dimension 

#### the diagnosis of breast tissues
**2 classes:**
- malignant
- benign


<script 
src="https://gist.github.com/Edudeiko/0da50c3878fc510661d08124755e11dd.js">
</script>

---
**accuracy score of 0.976**

#### Classification report

<img src="https://i.ibb.co/DC9Xj6M/classification-report-KNN.png" alt="classification-report-KNN" border="0">

#### Confusion matrix

<img src="https://i.ibb.co/2SmNFrm/confusion-matrix-KNN.png" alt="confusion-matrix-KNN" border="0">
