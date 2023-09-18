# Neural Net Regression Model on a Toy Example

UNDERSTANDING OF THE PROBLEM
The problem is a regression problem, where we have to predict the total price of the products based on the data we have about the quantity and total price of our past purchases. We do not have the individual prices of the products (i.e., Fish, Chips, and Ketchup).

![image](https://github.com/AishwaryaHastak/Basic_NN_toy_model/assets/31357026/24d8ea2d-4e11-4ef6-ba2a-6970a6f41831)

We will build a neural net model with a single linear layer that will produce one output, i.e., the estimated total price. After training on multiple data points, our final trained model should have the weights associated with each of these three products, to be proportional to their actual individual prices.



THOUGHT BEHIND THE CODE
I have created three separate Excel files for delta rule training data, batch rule training data, and testing data (as attached below). We have read this file into pandas data frames.
 	 	 
We have two separate classes for training and testing that have Dataset objects as their argument. We have implemented three methods of the Dataset Class in it, __init__ is used to initialize all the parameters of the model, __len__ returns the length of the dataset and __getitem__ method returns the data point at the specified index.
We have separated the data frame into two parts to create feature and target tensors. We in turn create a dataset object and pass it to our models.
For the delta rule model, we iterate over each data point in our training dataset and calculate the price estimate using the linear formula. We then calculate the MSE loss against the actual price and then calculate the gradient and update weights.
For the batch delta rule model, we create a DataLoader object that will iterate through the dataset with a batch size of three. We perform the same process as the delta rule model but over 10 iterations or epochs. We calculate the gradient as the average gradient of all data points in a single batch. We use this average gradient to update the model parameters only once for each batch.
Our models return the tuned weights and biases. These weights and biases are then passed as an argument to the test class and we calculate the losses. We have plotted both the training and testing losses using matplotlib library.

DELTA RULE

![image](https://github.com/AishwaryaHastak/Basic_NN_toy_model/assets/31357026/b0139556-e741-4a2b-a46b-424090abf18f)

Final Weights and Biases after training the model
![image](https://github.com/AishwaryaHastak/Basic_NN_toy_model/assets/31357026/301c080d-bf86-4f70-8cae-cfdf7d29e62f)

BATCH DELTA RULE

![image](https://github.com/AishwaryaHastak/Basic_NN_toy_model/assets/31357026/c491e386-7e80-4a59-8890-a0db32160297)

Final Weights and Biases after training the model

![image](https://github.com/AishwaryaHastak/Basic_NN_toy_model/assets/31357026/21571a57-0af4-4102-beac-2f6f86af5c34)


FINDINGS
The batch delta rule model performed better than the normal delta rule model. The training loss graph for the batch model follows a gradually decreasing curve, showing a gradual decrease in the loss of the model. More epochs and training in batches helped the model perform better.
