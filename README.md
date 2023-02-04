# NOVA IMS - Deep Learning Neural Networks course - Project - Group4 
## Face expressions recognition with Convolutional Neural Networks

#### Benedita Pereira, 20211752, Cátia Reis, 20211749, Gil Marinho, 20211785, Maria do Carmo Sousa, 20211813


The aim of this work is to develop a deep learning model for predicting facial emotions. The approach was to use Convolutional Neural Network (CNN) models. Techniques such as normalization and regularization were assessed. The results show that the best model has an F1-score of 0.50, and regularization techniques did not result in a reduction of overfitting. Furthermore, transfer learning was applied, but no improvement in results were observed. We considered that the dataset used might not be the best to obtain an efficient model for predicting facial emotions.

## How to run the programm
1. Datasets

The folder data can be splitted into 3 categories: 

1.1 Original datasets which inside have subfolders with the pictures distributed according to the emotion they represent. These datasets are the following: 

- CK+48: This dataset has sequencies of images completely identical.
- JAFFE: This dataset has sequences of photographs of the same subject, undergoing different emotions, and distinct levels of display intensity of those emotions.
- SFEW: This dataset has some images where no human face is recognizable, has is made evident on the following image.

1.2 compiled_dataset folder

The three datasets containing only the selected images were then compiled all together and spread across distinct directories, one for each emotion, adding up to 233 images labeled as “surprise”, 252 labeled as “sadness”, 315 as “happy”, 156 as “fear”, 141 as “disgust”, 293 as “anger”, 18 as “contempt” and 232 as “neutral”. Given the lack of representativity of the contempt images, it was decided to remove them from the dataset, and from the list of classification labels. The previous process resulted in a final dataset with 1622 images.
1.3 Input folder. This folder considers 4 subfolders, which have the pictures split according to the respective emotion:
- TRAIN: training dataset
- VALIDATION: validation dataset
- TEST: test dataset
- TRAIN_augmentation: new balanced train dataset with artificially created images and an even number of images by emotion

2. Script
The script used is labeled DLNN_Project_group4.ipynb. There are some considerations we would like you to consider:
- The subsections "CK+48", "JAFFE", "SFEW", "Compiled dataset", "Train, Validation and Test datasets", "Balance Train dataset: image data augmentation" within "Data Preparation" section don't need to be run, since the pre-processing outputs are already displayed in folders scheme described above.
- In the subsections mentioned above we commented the "save" statements in order to not overlap our data.
- Since the datasets had some noisy pictures, we manually deleted them from the SFEW directory.
- Before creating any instace of model we certified that this instance did not exist in order to try to avoid retraining the models. To do this used the following lines of code (example): 
del_var = 'cnn61'
if del_var in globals(): globals().pop(del_var, None).
- In what regards to the tensorboard, we used it to visualize and assess the models during the training process. It enabled us to monitor key metrics such as F1-score, AUROC, and accuracy and make decisions on how to optimize and improve models’ performance. We commented all the 'callbacks' parameters within the fit function along the script, except for the 'final' models, which were CNN-51 with 20 epochs and a 64 batch-size and the transfer learning model that used the CNN-51 classifier architecture with a 128 batch-size.
