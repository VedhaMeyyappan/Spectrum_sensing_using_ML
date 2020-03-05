Spectrum detection to avoid interference between SUs and Pus using multiple cognitive radios( three receivers and one transmitter).
Used jupyter notebook from Anaconda

Libraries Used:

•	Pandas 
•	Matplotlib 
•	NumPy 
•	SciPy 
•	Scikit-learn 
•	Keras

Installed using command: conda install <package-name>

DATASET:

As opposed to the simplified CRN containing one transmitter and one receiver, this project contains multiple receiver and a single transmitter. The three radio receivers are placed at a respective distance of 2.7m, 4.7m and 5.7m from the transmitter radio which gives us three different input variables.  The dataset totally has 262169 data points with signal power as the input and labeled occupancy column as the output. The original dataset just has three columns of signal power from three different receivers, a few other features can be extracted from the available dataset to get more robust results.  

FEATURE EXTRACTION:

The dataset has just the signal power as input which is not enough to obtain optimum results. To get better results we can extract features from the signal power to provide them all together as input. Feature extraction helps us in dimensionality reduction by reducing the provided information into a manageable group of data. The extracted features must be related to the original dataset so that it produces non redundant results. The following features are extracted, pertaining to the bandwidth, from the original dataset using a fixed window size of 161, 
1) Kurtosis 
2) Skewness 
3) Central Difference 
4) Average Signal Power 
5) Maximum Signal Power 
6) Min-Max Signal Power 
7) Exponential Moving Average

FEATURE SELECTION

From the extracted features, not every feature will be necessary to get accurate results. There may be a few features that contributes less or reduces the accuracy of the result. To find out such unwanted feature, we use feature selection. Feature selection helps 
us segregate the most contributing feature towards the output. To find out which features provides us better results, we used the correlation factor between the output and each extracted feature.
From the correlation heat map that the least correlated values with the output occupancy are, central difference and skewness. They provide negative or less impact towards better performance. Thus they were dropped to obtain more optimum results. 
 
BALANCING THE DATASET

Before training the model, as a part of preprocessing, we need to balance the dataset. Imbalanced dataset can give us improper classification that leads to error in results. The feature with more instances than the other will be classified as having maximum accuracy which is not desirable. Balancing the dataset as a whole might give us over fitting results. Thus to avoid that we use oversampling method to balance the dataset. Oversampling creates copies of data points and makes the classes equal and balanced. There are different oversampling algorithms in machine learning like SMOTE, borderline SMOTE, random oversampling etc. In this project we choose random oversampling as it creates more training samples from the existing data points unlike SMOTE which creates new variety of data points to increase the samples. Thus random oversampling the training data points we got a balanced dataset.



The dataset was trained and tested using algorithms like Logistic regression, logistic regression with regularization L2, LDA, QDA, KNN, random forest and Bi-LSTM. Since it is an imbalanced dataset, F score tells us the accuracy of the model. To get better precision value than recall for a few models, the beta value of the f-score was increased.
 
 
