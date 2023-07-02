# Task: White Blood Cell Classification
-------------------------------------------------------------------------------------------------------------------------------------------------


Note: Notebook 2 is a continuation of Notebook 1. Please run Notebook 1 first and then run Notebook 2.


## 📖 Project Goal

This task aims to classify images of White Blood Cells into 9 subtypes. The specific types of WBCs to be classified are as follows: bands, basophils, blasts, eosinophils, lymphocytes, metamyelocytes, monocytes, myelocytes, and neutrophils. 

The data has been provided to me and it contains two folders: WBC and classify-images. Images in the WBC folder have been used for training and testing the model. While the classify-images folder has been used to classify images into the 9 subtypes mentioned above.


## 📖 Data Summary

-> WBC: This folder has 9 sub-folders, each containing labelled images of the sub-types of WBC. The images in these 9 sub-folders are to be used for training and testing the model.

-> classify-images: This folder has unlabelled images. It is to be used for classifying the images after the model has been trained and tested.


## 📖 Training Environment: Colab notebook (free version)

1. All the tasks have been performed in the free version of the Colab notebook having System RAM = 12.7 GB. 

2. The models have been trained using GPU T4. 


## 📖 Task Work-flow: Pre-processing

1. Creation of train and test folders using the labelled images of the folder WBC in the base directory:

-> train: 80% of the labelled images of the folder WBC are copied into the train folder.

-> test: the remaining labelled images are copied into the test folder. The test folder will be used for model testing and evaluation. This is because the folder classify-images has unlabelled images and it is difficult to create a confusion matrix using it.

2. Normalization: The independent variable X is an array created from images having dimensions = 256, 256. Hence X has been normalized so that the images contribute more evenly to the total loss.

3. Augmentation: The dataset is augmented to increase the variations in the images of each class.

4. Over-sampling using SMOTE: The balance of the dataset is checked and it is found that it is an unbalanced dataset. Hence, the imbalance is removed using SMOTE.

5. One-hot encoding of the labels in the training dataset.


## 📖 Task Work-flow: Model training and testing

Note: Accuracy is used as a metric for model evaluation because it is more important that the model classifies each image correctly rather than penalizing the False-Positives (Precision) or the False-Negatives (Recall) or penalizing both (F1).

### VGG16 model: It gave a prediction accuracy of around 75% on the test set created from the wbc folder.

After training the model, predictions have been made on the classify-images folder dataset and the output has been stored in a dataframe.


## 📖 Inference: on Generalization of the results

The dataset is originally imbalanced. It is biased towards the well-represented classes. The results are not expected to generalize well due to the fact that some classes in the train dataset are under-represented and hence SMOTE technique is used to treat the underlying imbalance. However, SMOTE can still be ineffective in model fine-tuning due to the generation of lower-quality images.


## 📖 Challenges faced

1. The computational resource limitation to handle image data: The pre-processing steps, especially image augmentation and SMOTE, are restricted by the 12.7 GB RAM available in the Colab notebook.

2. To manage the computational limitation, multiple Colab notebooks for different tasks have been used.

3. Concerning SMOTE: SMOTE uses the KNN algorithm to increase the number of samples in the minority classes. The class blasts in the training dataset have only 3 images. This means that each image has only 2 neighbours in the original train dataset. Hence, applying SMOTE to the original training dataset may create many similar images in the under-represented classes.

4. Hence, image augmentation has been done before applying SMOTE. Augmentation creates many variations in the under-represented classes and after that, SMOTE over-samples the variations.

5. A CNN model built from scratch and a Resnet152 model were also trained. But their predictions were not satisfactory. More work has to be done to improve their predictions.


## 📖 Future work

1. Fine-tuning the VGG16 model.

2. Dealing with overfitting.

3. Selecting the appropriate number of layers to unfreeze by careful experimentation.

