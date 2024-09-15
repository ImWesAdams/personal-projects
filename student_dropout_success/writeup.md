# Student Dropout, Graduation, and Still-Envollment Prediction

## Dataset
The dataset used for this project is the ["Predict Students' Dropout and Academic Success" dataset](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success) from the UCI Machine Learning Repository. It contains various student academic performance indicators, and the goal is to predict whether a student will drop out or succeed academically.

## Background
I've used both Neural Nets and Ensemble (Forest, XGBoost) models for some predictive analytics tasks before. In non-critical business tasks, I've tended to use Ensemble models for their ease of programming, training, and diagnosing. In this instance, I wanted to train models on the same (relatively straightforward) dataset and see which has a higher ceiling.

## Objective
I wanted to spend no more than 1 Sunday designing two models and testing their performance:
- **Feedforward Neural Network** implemented in PyTorch
- **XGBoost** classifier

### Feedforward Neural Network
- **Data Preprocessing**
    - Train-test splits are made (80% - 20%)
    - Numerical values are normalized (only against Training data)
    - Categorical variables are set up for embedding

- **Model Architecture**
    - Model takes an input of numerical data, and categorical data (which it embeds) concatenated together.
    - It then passes through a standard 2-Layer feedforward network with ReLU activation and dropout.
    - The output is 3-dimensional (Dropped out, Still enrolled, Graduated)

- **Training**
    - It's trained for 1,000 epochs on batch sizes of 32, with a Learning Rate Scheduler set to step down on plateau.
        - Training took about 20 minutes on my machine.
        - Below is an image of the accuracy over the training cycle.
        ![Training Accuracy Graph](neural_accuracy.png)

- **Performance**
    - The final test accuracy obtained was 78%.
        - With the self-imposed "Do this on a single Sunday" limit, this is without significant optimization, and no testing of various hidden layer sizes.

### XGBoost Classifier
- **Data Preprocessing**
    - Numerical values are normalized
    - Train-test splits are made (80% - 20%)
    - Categorical variables are established as Categorical in Pandas Dataframe

- **Model Parameters**
    - Model is set up to handle categorical variables with a histogram-based tree split method.
    - Max_depth is 5, with 10,000 estimators.
        - Training took about 1 minute on my machine.

- **Performance**
    - The final test accuracy obtained was 77%.
        - With the self-imposed "Do this on a single Sunday" limit, this is without significant optimization, only trying a handful of max_depths in the range of 3 to 7.


## Acknowledgments
Realinho, V., Vieira Martins, M., Machado, J., & Baptista, L. (2021). Predict Students' Dropout and Academic Success [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5MC89.