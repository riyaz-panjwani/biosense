# Code Explained
## Importing needed modules
<ol>
<li>pandas</li>
<li>numpy</li>
<li>tensorflow</li>
<li>matplotlib</li>
<li>opencv-python</li>
<li>seaborn</li>
<li>scikit-learn</li>
<li>tqdm</li>
<li>ipython</li>
</ol>
<br>
Custom Callback Concept
<ol>
<li>
Monitoring Progress: </li><br>
It keeps an eye on how well the program is doing as it learns. Imagine the program is like a student trying to get better grades. This tool looks at how well the student is doing on practice tests.<br>
<br>
<li>
Saving the Best:</li> <br>
Whenever the student (the program) gets the best score on a practice test, the tool remembers that score and also the way the student was studying at that time. <br>
 <br>
<li>
Learning from Mistakes:</li> <br>
If the student does worse on a practice test, the tool says, "Wait, you were doing better before, so let's go back to how you were studying when you did your best." <br>
 <br>
<li>
Lowering the Pace: </li><br> 
If the student keeps doing worse and worse, the tool tells the student to slow down a bit and study more carefully. <br>
 <br>
<li>
User Input: </li><br> 
Sometimes, the tool asks the user (the teacher) if they want to continue or maybe make some changes. It's like the tool checking with the teacher to see if everything is going well. <br>
 <br>
<li>
Progress Reports: </li><br> 
Throughout the learning process, the tool shows how much better the student is getting. This helps decide when to stop or make changes in the learning process. <br>
</ol>
<br>
<br>
## Data Preprocessing
<ul>
<li>
Detecting the images that throw errors and storing them in different lists.
</li>
<li>
Read in train, test, and valid images and create train, test, and validation data frames using train, test and valid directories
</li>
<li>
Trim train_df so no class has more than max_samples images
</li>
<li>
Expand train_df rows with augmented images so each class has 250 samples
</li>
<li>
Create the train_gen, test_gen final_test_gen and valid_gen
</li>
<li>
Create a function to show example training images
</li>
</ul>
<br>
## Create a model using transfer learning with EfficientNetB3
A model using transfer learning with EfficientNetB3 is a neural network model that leverages the pre-trained EfficientNetB3 architecture as a starting point and fine-tunes it for a specific image classification task. Transfer learning is a technique in deep learning where a model that has been pre-trained on a large dataset is adapted to a different but related task.
<br>
### Create a custom Keras callback to continue and optionally set LR or halt training
Purpose: The LR_ASK callback is a tool to help you control the training of a machine learning model. It gives you the option to continue training the model for more rounds (epochs) or stop the training process.<br>
<br>
How It Works: When you use this callback during training, you specify three things:
<br><br>
model: This is the name of your machine learning model, which you've already defined and compiled.<br><br>
epochs: It's the total number of rounds you initially planned for your training.<br><br>
Ask_epochs: This is like a checkpoint. When your training reaches this checkpoint, you decide whether to continue or stop.<br><br>
Decision Time: When the training reaches the ask_epochs, you have a choice to make:<br><br>
You can choose to stop training by entering 'H' (for "Halt").
Or, you can decide to continue training for a few more rounds by specifying the number of additional rounds you want to run (e.g., if you enter 4, it will continue for 4 more rounds).
<br><br>
After Training: Once the training is completed, the callback sets the model's weights to the point in time when it performed best, specifically when it had the lowest validation loss. It's like keeping your best work or results.
<br>
Instantiate custom callback
Train the model
it is better to make the base model trainable from the outset if you are doing transfer learning<br>
The model will converge faster and have a lower validation losss. Ensure you initialize the transfer model with imagenet weights.<br><br>
Define a function to plot the training data
Make Predictions on the test set
Define a function which takes in a test generator and an integer test_steps and generates predictions on the test set including a confusion matric and a classification report
<br>
Changing the saved .h5 Model to .tflite format for use 
To convert it we are going to need TensorFlow <br>
To do so install it first and then type the following command in command prompt<br>
tflite_convert --keras_model_file=C:/Users/riyaz/OneDrive/Desktop/AD/keras_model.h5 --output_file=C:/Users/riyaz/OneDrive/Desktop/AD/ad_model.tflite --quantize
<br>This converts the file into .tflite quantize format<br>





