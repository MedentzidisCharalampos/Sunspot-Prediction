# Sunspot-Prediction
Sunspots are temporary phenomena on the Sun's photosphere that appear as spots darker than the surrounding areas. They are regions of reduced surface temperature caused by concentrations of magnetic field flux that inhibit convection. Sunspots usually appear in pairs of opposite magnetic polarity. Their number varies according to the approximately 11-year solar cycle. You can find the dataset there:  https://www.kaggle.com/robervalt/sunspots  

It is a csv dataset with the first column as index, the second being a date in the format of year, month, day, and the third being the date of that month that the measurement was taken it is an average monthly amount that should be at the end of the month.  
The column of sunspots and timestamps are extracted from the dataset. These columns is being converted into numpy arrays because it is more memory efficient.  

The series is being splited into training and validation sets. The split will be at time 3,000, the window size at 60, the batch size at 100 and a shuffled buffer at 1,000
The series  will be converted into the dataset using the previous configurations.  

The network design and hyperparameters are as follows:  
A convolutional layer with 60 filter, kernel size 3x3, stride 1, input a timeserie and activation function Relu  
Two lstm layers with 60 cells each   
A dense layer of 30-units with input the window size and activation fucntion Relu  
A dense layer of 10-units with input and activation fucntion Relu  
A dense layer of 1-unit   
A lambda layer that multiplies the output to 400 because our numbers are in range 1-400

The model compiled with mse as loss function and SGD as optimizer with lr = 1e-5 and momentum = 0.9.  
The model is trained for 500 epochs and in the end our metric mae is 15.40074.



