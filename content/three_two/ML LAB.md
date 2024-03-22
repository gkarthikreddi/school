## Find S
```python
import numpy as np
import pandas as pd

data = pd.read_csv("dataset1.csv")
sample = np.array(data)[1:,:-1]  # Removes the header and last coloumn of data
target = np.array(data)[1:,-1]  # Removes the header and gives the last coloumn

def train(sample, target):
    # Initializing specific_hypothesis
    for i in range(len(target)):
        if target[i] == "Yes":
            specific_hypothesis = list(sample[i])
            break

    # Tuning specific_hypothesis
    for i in range(len(sample)):
        if target[i] == "Yes":
            for j in range(len(specific_hypothesis)):
                if sample[i][j] != specific_hypothesis[j] and specific_hypothesis[j] != '?':
                    specific_hypothesis[j] = '?'

    return specific_hypothesis


specific_hypothesis = train(sample, target)
print("Specific Hypothesis: ", specific_hypothesis)
```
## Candidate Elimination
```python
import numpy as np
import pandas as pd

data = pd.read_csv("dataset1.csv")
sample = np.array(data)[1:,:-1]  # Removes the header and last coloumn of data
target = np.array(data)[1:,-1]   # Removes the header and gives the last coloumn

def train(sample, target):
    specific_hypothesis = list(sample[0]) # assumes first sample is positive
    num_atb = len(specific_hypothesis)
    generic_hypothesis = [['?' for i in range(num_atb)] for j in range(num_atb)]

    for i in range(len(sample)):
        if target[i] == "Yes":
            if specific_hypothesis != list(sample[i]):
                for j in range(num_atb):
                    if sample[i][j] != specific_hypothesis[j] and specific_hypothesis[j] != '?':
                        specific_hypothesis[j] = '?'
                        generic_hypothesis[j][j] = '?'
        else:
            for j in range(num_atb):
                if sample[i][j] != specific_hypothesis[j]:
                    generic_hypothesis[j][j] = specific_hypothesis[j]
                else:
                    generic_hypothesis[j][j] = '?'

    tmp = ['?' for _ in range(num_atb)]
    generic_hypothesis = [i for i in generic_hypothesis if i != tmp]

    return specific_hypothesis, generic_hypothesis

specific_hypothesis, generic_hypothesis = train(sample, target)
print(f"Specific Hypothesis: {specific_hypothesis}\nGeneric Hypothesis: {generic_hypothesis}")
```
## Linear Regression
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

data = pd.read_csv("dataset.csv")
x = list(np.array(data)[:,0])
y = list(np.array(data)[:,-1])

mean_x = sum(x) / len(x)
mean_y = sum(y) / len(y)

deviation_x = [i-mean_x for i in x]
deviation_y = [i-mean_y for i in y]

product_deviation = [i*j for i, j in zip(deviation_x, deviation_y)]
square_deviation_x = [i**2 for i in deviation_x]

slope = sum(product_deviation) / sum(square_deviation_x)
intercept = mean_y - (slope * mean_x)


X = [i for i in range(-1, 20)]
Y = [i*slope + intercept for i in X]

plt.scatter(x, y)
plt.plot(X, Y)
plt.show()
```
## K-Nearest Neighbor (KNN)
```python
from sklearn.model_selection  import train_test_split
from sklearn.neighbors import KNeighborsClassifier as kn
from sklearn import datasets

iris = datasets.load_iris()

x_train, x_test, y_train, y_test = train_test_split(iris.data, iris.target, test_size = 0.1)

for i in range(len(iris.target_names)):
	print("Label ", i, '- ', str(iris.target_names[i]))

k = 3
classifier = kn(n_neighbors = k)
classifier.fit(x_train, y_train)
y_pred = classifier.predict(x_test)
print("Accuracy for k:",k,"is ", classifier.score(x_test, y_test))
```