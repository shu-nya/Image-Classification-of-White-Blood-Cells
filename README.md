# Image-Classification-of-White-Blood-Cells into 9 sub-types
---------------------------------------------------------------------------------------------------------------------------------------------

## 📖 Project Goal

This task aims to classify images of White Blood Cells into 9 subtypes. The specific types of WBCs to be classified are as follows: bands, basophils, blasts, eosinophils, lymphocytes, metamyelocytes, monocytes, myelocytes, and neutrophils. 

The data has been provided to me and it contains two folders: WBC and classify-images. Images in the WBC folder have been used for training and testing the model. While the classify-images folder has been used to classify images into the 9 subtypes mentioned above.


## 📖 Data Summary

-> WBC: This folder has 9 sub-folders, each containing labelled images of the sub-types of WBC. The images in these 9 sub-folders are to be used for training and testing the model.

-> classify-images: This folder has unlabelled images. It is to be used for classifying the images after the model has been trained and tested.


## 📖 Modelling Environment

All the tasks have been performed in the free version of Colab notebook having System RAM = 12.7 GB. The CNN and models have been trained using GPU T4. 


## 📖 Task Work-flow: Pre-processing

1. Two more folders using the labelled images of the folder WBC in the base directory are created. One folder is named train and the other is the test.
   
-> train: 80% of the labelled images of folder WBC are copied into the train folder. 

-> test: the remaining labelled images are copied into the test folder. The test folder will be used for model testing and evaluation. This is because the folder classify-images has unlabelled images and it is difficult to create a confusion matrix using it.
   
2. The independent variable X is an array created from images having dimensions = 256, 256. Hence X has been normalized so that the images contribute more evenly to the total loss.

3. The dataset was augmented to increase the variations in the images of each class.

4. The balance of the dataset is checked and it is found that it is an unbalanced dataset. Hence, the imbalance was removed using SMOTE.

5. One-hot encoding of the labels in the training dataset is done.


## 📖 Task Work-flow: Model training and testing

Note: Accuracy is used as a metric for model evaluation because it is more important that the model classifies each image correctly rather than penalizing the False-Positives (Precision) or the False-Negatives (Recall) or penalizing both (F1).

### VGG16 model: It gave a prediction accuracy of 76.6% on the test set.


## 📖 Challenges

1. The computational resource limitation to handle image data: The pre-processing steps, especially image augmentation and SMOTE, are restricted by the 12.7 GB RAM available in the Colab notebook.

2. To manage the computational limitation, multiple Colab notebooks for different tasks have been used.

3. Concerning SMOTE: SMOTE uses KNN algorithm to increase the number of samples in the minority classes. The class blasts in the train dataset has only 3 images. This means that each image has only 2 neighbours in the original train dataset. Hence, applying SMOTE on the original training dataset may created many similar images in the under-represented classes.

4. Hence, image augmentation has been done before applying SMOTE. Augmentation creates many variations in the under-represented classes and after that SMOTE over-samples the variations.
