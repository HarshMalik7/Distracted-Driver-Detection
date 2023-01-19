# Distracted Driver Detection
![](/images/state_farm.png)

## Applying on Input Video
![](/images/statefarm_result.gif)

## Applying on Input Image
![](/images/demo_image.gif)

## Project Overview
There has been a substantial increase in the total number of road accidents leading to fatal injuries and deaths in recent years. As per the Union Road Transport and Highways Ministry Report 2016, 17 people were killed each hour in India due to road accidents. A major reason behind these staggering figures are distracted drivers. In this project, I aim to develop a model which will identify whether a driver is distracted or not. I will use various Deep Learning models, namely the Convolution Neural Network(CNN), VGG16 to create my model. For the purpose of training and testing, I have used the kaggle dataset provided by State Farm which contains images of drivers in different scenarios, and we will try to classify them into various classes. Some important libraries used in creation of this model are scikit-learn and keras.

## Problem Statement

Given a dataset of 2D dashboard camera images, an algorithm needs to be
developed  to classify each driver's behaviour and determine if they are
driving attentively, wearing their seatbelt, or taking a selfie with their friends in
the backseat etc..? This can then be used to automatically detect drivers
engaging in distracted behaviours from dashboard cameras.

Following are needed tasks for the development of the algorithm:

1. Download and preprocess the driver images

2. Build and train the model to classify the driver images

3. Test the model and further improve the model using different techniques.

## Data Exploration

The provided data set has driver images, each taken in a car with a driver
doing something in the car (texting, eating, talking on the phone, makeup,
reaching behind, etc). This dataset is obtained from Kaggle(State Farm
Distracted Driver Detection competition).

Following are the file descriptions and URL’s from which the data can be
obtained :
* imgs.zip - zipped folder of all (train/test) images
* sample_submission.csv - a sample submission file in the correct format
* driver_imgs_list.csv - a list of training images, their subject (driver) id, and
* class id
* driver_imgs_list.csv.zip
* sample_submission.csv.zip

The 10 classes to predict are:

* c0: safe driving

* c1: texting - right

* c2: talking on the phone - right

* c3: texting - left

* c4: talking on the phone - left

* c5: operating the radio

* c6: drinking

* c7: reaching behind

* c8: hair and makeup

* c9: talking to passenger

There are 102150 total images. Of these 17939 are training images,4485
are validation images and 79726 are training images. All the training,
validation images belong to the 10 categories shown above.
The images are
coloured and have 640 x 480 pixels each as shown below  

Driver texting right  
![](images/img_12_TEXTING_RIGHT.jpg)  

Driver operating the radio  
![](images/img_10_OPERATING_RADIO.jpg)

## Project Overview

### Data Preprocessing

Preprocessing of data is carried out before model is built and training process
is executed.
Following are the steps carried out during preprocessing.
* Initially the images are divided into training and validation sets.
* The images are resized to a square images i.e. 224 x 224 pixels.
* All three channels were used during training process as these are color
images.
* The images are normalised by dividing every pixel in every image by 255.
* To ensure the mean is zero a value of 0.5 is subtracted.

### Implementation

A standard CNN architecture was initially created and trained. We have created 4 convolutional layers with 4
max pooling layers in between. Filters were increased from 64 to 512 in each
of the convolutional layers. Also dropout was used along with flattening layer
before using the fully connected layer. Altogether the CNN has 2 fully
connected layers. Number of nodes in the last fully connected layer were
setup as 10 along with softmax activation function. Relu activation function
was used for all other layers.Xavier initialization was used in each of the
layers.

### Refinement

To get the initial result simple CNN architecture was built and evaluated. This
resulted in a decent loss. The public score for the initial simple CNN
architecture(initial unoptimized model) was 2.67118.
After this to further improve the loss, transfer learning was applied to VGG16
along with investigating 2 types of architectures for fully connected layer.
Model Architecture1 showed good results and was improved further by using
the below techniques
* Drop out layer was added to account for overfitting.
* Xavier initialization was used instead of random initialization of weights
* Zero mean was ensured by subtracting 0.5 during Pre-processing.
* Training was carried out with 400 epochs and with a batch size of 16
* To further improve the loss metric ,VGG16 along with Model Architecture1
was selected and fine-tuning was applied. SGD optimiser was used with very
slow learning rate of 1e-4. A momentum of 0.9 was applied with SGD.


### Results

The comparison of the Public Scores for all the model architectures
considered for this data set is shown in Fig

![](images/comparison.png)

### Installation 

1. Install `Python 3.8.5` on your Local Machine 
2. Execute `git clone https://github.com/Abhinav1004/Distracted-Driver-Detection.git` to clone the repository
3. Create Python Virtual Environment in root folder by opening terminal and executing
    ```
      * pip install virtualenv
      * virtualenv distracted_env
      * source distracted_env/bin/activate
     ```
4. Install required Python Libraries by `pip install -r requirements.txt`




