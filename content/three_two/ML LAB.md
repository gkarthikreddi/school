- [[#Find S]]
- [[#Candidate Elimination]]
- [[#Linear Regression]]
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

def predict(sample, specific_hypothesis):
    for i in range(len(sample)):
        if specific_hypothesis[i] != '?' and specific_hypothesis[i] != sample[i]:
            return False
    return True

specific_hypothesis = train(sample, target)
print("Specific Hypothesis: ", specific_hypothesis)
example = ["Night", "Sunny", "Moderate", "Yes", "Normal", "Low"]
ans = predict(example, specific_hypothesis)
print("Prediction for ", example, " is ", ans)
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
x_label = "Pizza Diameter"
y_label = "Pizza Price"

class Linear_regression:
    def __init__(self, x, y, x_label, y_label):
        self.x = x
        self.y = y
        self.x_label = x_label
        self.y_label = y_label
        mean_x = sum(x) / len(x)
        mean_y = sum(y) / len(y)
        deviation_x = [i-mean_x for i in x]
        deviation_y = [i-mean_y for i in y]
        product_deviation = [i*j for i, j in zip(deviation_x, deviation_y)]
        square_deviation_x = [i**2 for i in deviation_x]
        self.slope = sum(product_deviation) / sum(square_deviation_x)
        self.intercept = mean_y - (self.slope * mean_x)

    def plot(self):
        upperbound = max(self.x) + 10
        lowerbound = min(self.x) - 10
        X = [i for i in range(lowerbound, upperbound)]
        Y = [i*self.slope + self.intercept for i in X]
        plt.scatter(self.x, self.y)
        plt.plot(X, Y)
        plt.xlabel(self.x_label)
        plt.ylabel(self.y_label)
        plt.title("Linear Regression")
        return plt

    def predict(self, value):
        return value*self.slope + self.intercept

line = Linear_regression(x, y, x_label, y_label)
graph = line.plot()
graph.show()
ans = line.predict(20)
print(ans)
```