# Predict_Attacks_In_Network_Traffic

## Introduction 
The code implements a Long Short-Term Memory (LSTM) neural network to classify network traffic
data from the dataset used. The aim is to differentiate between normal network traffic and network
attacks. The LSTM is a type of recurrent neural network (RNN) that can process sequential data, making
it a suitable choice for this task.

## Implementation 
The code first loads the dataset from a CSV file using pandas' read_csv function. The dataset has 41
features, including the target variable 'class'. The target variable is categorical, with two possible values:
'normal' and 'attack'. To convert the target variable to a numerical format, the code uses pandas replace
function, assigning 0 to 'normal' and 1 to 'attack.
Next, the input features are one-hot encoded using pandas get_dummies function. One-hot encoding is a
technique used to convert categorical variables into numerical features. It creates a binary vector for each
category, with a value of 1 for the category present in the sample and 0 for all other categories.
After one-hot encoding, the input data is reshaped into the format required by the LSTM layer. The
LSTM layer expects a 3D input of the shape (samples, time steps, features). The 'samples' dimension
corresponds to the number of samples in the dataset, 'time steps' refers to the number of time steps in
the input sequence (set to 1 in this case), and 'features' represents the number of input features.

## Methodology
The dataset is then split into training and testing sets using the train_test_split function from scikit-
learn. The test size is set to 20% of the dataset, and the random_state parameter is set to ensure
reproducibility.
Next, the LSTM model is defined using the Sequential model from Keras. The Sequential model is a
linear stack of layers. The LSTM layer is added as the first layer, with 64 units and an input shape of
(1, 122). The dropout layer is added after the LSTM layer, with a rate of 0.2, to prevent overfitting. The
dense layer is added as the last layer, with a single output unit and a sigmoid activation function for
binary classification.

## Results
The model is trained using the fit method of the Sequential model. The batch size is set to 64, and the
number of epochs is set to 50. During training, the model is optimized using the Adam optimizer and
the binary_crossentropy loss function. The training history is saved in the 'history' variable for later
analysis.
Finally, the accuracy of the trained model is evaluated on the test set using the evaluate method of the
Sequential model. The test accuracy is printed on the console.

## Conclusion 
In summary, the code implements an LSTM neural network to classify network traffic data from the
dataset. The dataset is preprocessed by converting the categorical target variable to numerical format,
one-hot encoding the input features, and reshaping the data to the format required by the LSTM layer.
The model is defined using the Sequential model from Keras, with an LSTM layer, a dropout layer for
regularization, and a dense layer with a sigmoid activation function for binary classification. The model
is trained using the fit method of the Sequential model, with 50 epochs and a batch size of 64. The
accuracy of the trained model is evaluated on the test set using the evaluate method of the Sequential
model.
