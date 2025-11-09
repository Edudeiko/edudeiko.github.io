---
layout: post
title: K-Nearest Neighbors algorithm from scratch
subtitle: KNN a step by step guide
image: img/KNN.png
---
**K-Nearest Neighbors (KNN)** is one of the simplest yet most effective machine learning algorithms. It works on the intuition that similar data points tend to have similar labels. While it can be used for both classification and regression tasks, it's most commonly applied to classification problems.

In this tutorial, we'll build a KNN classifier from scratch to understand how it works under the hood. Our implementation will include **Standard Scaler** for feature normalization, **Euclidean distance** calculation, **predict** function for making predictions, and **accuracy score** for evaluation.

You can find the complete code and additional examples [on my GitHub page](https://github.com/Edudeiko/CS-Data-Science-Build-Week-1)

## Building the KNN Class

Start by building class **KNN** with the following components. First, import the necessary libraries:

```python
import numpy as np
from typing import Optional
```

**1)** Create the class KNN. The parameter `k` specifies how many nearest neighbors to consider when making predictions.

The choice of `k` is crucial:
- **Small k** (e.g., k=1): More sensitive to noise, can lead to overfitting
- **Large k**: Smoother decision boundaries, but may underfit
- **Rule of thumb**: Start with k = sqrt(n) where n is the number of training samples, and use cross-validation to find the optimal value

```python
class KNN:
    """K-Nearest Neighbors Classifier.

    Parameters:
        k (int): Number of nearest neighbors to consider for classification.
    """

    def __init__(self, k: int = 5):
        """Initialize KNN classifier with k neighbors."""
        self.k = k
        self.X_train: Optional[np.ndarray] = None
        self.y_train: Optional[np.ndarray] = None
```

**2)** Create a step-by-step Standard Scaler function

Before calculating distances between data points, we need to scale our features. KNN is sensitive to the scale of features, so standardization ensures all features contribute equally to distance calculations.

#### StandardScaler

```python
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

**Alternative simplified version:** If you don't need separate fit/transform steps (i.e., you're scaling all your data at once), you can use this condensed function. Note that `axis=0` ensures it scales each feature column independently.

```python
def scale(X):
    X_scaled = X - np.mean(X, axis=0)
    return X_scaled / np.std(X, axis=0)
```

**3)** Fit the training data before making predictions

Now we need to store the training data so we can compare test samples against it.

```python
def fit(self, X: np.ndarray, y: np.ndarray) -> 'KNN':
    """Store training data.

    Args:
        X: Training features of shape (n_samples, n_features).
        y: Training labels of shape (n_samples,).

    Returns:
        self: The fitted classifier.
    """
    self.X_train = X
    self.y_train = y
    return self
```

**4)** Create Euclidean distance function = sqrt(sum i to N (x1_i – x2_i)^2)

```python
def euclidean_distance(self, row1: np.ndarray, row2: np.ndarray) -> float:
    """Calculate Euclidean distance between two points.

    Args:
        row1: First data point.
        row2: Second data point.

    Returns:
        float: Euclidean distance.
    """
    return np.sqrt(np.sum((row1 - row2) ** 2))
```

You can print out the results of the Euclidean distance to look at the results.

```python
row0 = dataset[0]
'''you can compare any row in the dataset'''
for row in dataset:
    distance = euclidean_distance(row0, row)
    print(distance)
```

**5)** Create the predict function. Iterate through the test data and each row of training data to calculate the distance between them. Use Euclidean distance as the distance metric (you can explore other metrics). Sort the results in ascending order based on distance values. For each neighbor, find the target class and use majority voting to determine the prediction.

```python
def predict(self, X_test: np.ndarray) -> np.ndarray:
    """Predict class labels for test data.

    Args:
        X_test: Test features of shape (n_samples, n_features).

    Returns:
        np.ndarray: Predicted labels of shape (n_samples,).
    """
    y_pred = np.zeros(len(X_test))

    for i in range(len(X_test)):
        # Calculate distances to all training points
        distances = np.array([
            self.euclidean_distance(X_test[i], x_train)
            for x_train in self.X_train
        ])

        # Get indices of k nearest neighbors
        k_nearest_indices = distances.argsort()[:self.k]

        # Get labels of k nearest neighbors
        k_nearest_labels = [self.y_train[idx] for idx in k_nearest_indices]

        # Vote: most common label wins
        y_pred[i] = max(set(k_nearest_labels), key=k_nearest_labels.count)

    return y_pred
```

**6)** Calculate the accuracy score.

```python
def accuracy(self, y_test: np.ndarray, y_pred: np.ndarray) -> float:
    """Calculate accuracy score.

    Args:
        y_test: True labels.
        y_pred: Predicted labels.

    Returns:
        float: Accuracy score between 0 and 1.
    """
    return np.mean(y_test == y_pred)
```

If you've read this far, here's the complete code from above:

<script
src="https://gist.github.com/Edudeiko/abbbcf0e70b8b638191f7acb197924b7.js">
</script>

## Testing the KNN Algorithm

Now that we've built our KNN classifier from scratch, let's test it on a real-world dataset. We'll use the breast cancer dataset, which is a binary classification problem to predict whether a tumor is malignant or benign based on various features.

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
