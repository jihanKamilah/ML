# BantuMasak App

BantuMasak is an application designed to assist users, particularly housewives, in creating a well-organized plan for the meals they want to prepare over several days. Our team has developed various features to simplify the process of meal planning. 
On the machine learning side, we have built two types of models: a recommendation system and an image classification system. 
The recommendation system utilizes a model that calculates ratings and suggests suitable recipes for users.
For food classification, users can either upload or scan existing food images from their phones. The application will then predict the name of the food and provide detailed information such as ingredients and complete recipes.

## Project Structure (ML)
```bash
.
├── README.md
├── Datasets
│       ├── Image Classification
│       │       ├── asinan-jakarta
│       │       ├── ayam-goreng-lengkuas
│       │       ├── es-dawet
│       │       ├── gado-gado
│       │       ├── gulai-ikan-asin
│       │       ├── kolak
│       │       ├── lumpia-semarang
│       │       ├── mie-aceh
│       │       ├── rendang
│       │       ├── rujak-cingur
│       │       ├── sate-ayam-madura
│       │       ├── sate-meranggi
│       │       ├── serabi
│       │       ├── soto-ayam-lamongan
│       │       └── soto-banjar 
│       └── Recommandation System
│               ├── clean_recipe_v3.csv
│               └── dataset_user_rating_v4.csv
└── Model
        ├── Image Classification
        │       ├── Assets
        │       │       ├── Accuracy history.png
        │       │       └── Loss history.png
        │       ├── Converted file
        │       │       ├── model.pb
        │       │       ├── converted_model_food_classification_v1.tflite
        │       │       └── model_food_classification_v1.h5
        │       └── Food Classification_v1.ipynb
        └── Recommendation System
                ├── Assets
                │       └── Epochs history.png
                ├── Converted file
                │       ├── model.pb
                │       ├── converted_model_recommendation_for_you_v4.tflite
                │       └── model_recommendation_for_you_v4.h5
                └── recommendation for you v4.ipynb
```

## Datasets
We collected the datasets for both the recommendation system and food classification by scraping. For food classification, we scraped images from Google Images, resulting in a dataset with 15 food labels, each containing 100 images. 

On the other hand, for the recommendation system, we scraped data from the cookpad.com website. The dataset includes 864 different recipes, each with the food's id, title, ingredients, step-by-step instructions for making the dish, and the corresponding image URL. Another file used is dataset_user_rating, which consists of user id, menu id, menu name, and rating. For the user rating itself, we generate dummy data using python, where the rating range is from 0 to 5.

## Network
For the food classification model, we utilized transfer learning with the ResNet50 architecture. We also incorporated Convolutional Neural Networks (CNNs) into the model, specifically modified for the 15 food labels.
In the case of the recommendation system, the model calculates ratings and creating an embedding layer to suggest suitable recipes for the user. 

## Recommendation System
Our recommendation system model is typically categorized as `Collaborative Filtering`, which is a technique that makes recommendations based on the preferences and behavior of similar users. In this approach, the system identifies users who have similar tastes and preferences and recommends items based on the ratings of those similar users.

#### Model Architecture
In this model, we utilize several types of layers as follows:
1. `InputLayer` : This layer serves as the entry point for the input data, defining the shape and type of the expected input data. It consists of two inputs: Recipe-Input and User-Input.
2. `Embedding` : This layer transforms categorical variables into low-dimensional numerical vectors. We create two embedding layers for Recipe-Embedding and User-Embedding.
3. `Flatten` : These layers convert the multidimensional input data into one-dimensional vectors. We create two Flatten layers, Flatten-Recipe and Flatten-Users.
4. `Concatenate` : This layer concatenates multiple input tensors along a specific axis.
5. `Dense` : These layers learn complex patterns and relationships by connecting neurons between layers. We create four Dense layers with 256, 128, 128, and 1 neurons, respectively. The last Dense layer serves as the output layer.

#### Model Training
We fit the model using the previously built architecture, where the input data consists of two inputs: `train.User_id` and `train.Id_Nama`. The target variable, `train.Rating`, represents the expected output corresponding to the input data. The model is trained for 700 epochs.

#### Model Performance
The final performance of the model is as follows:
- `Loss: 0.3278`
- `Mean Squared Error: 0.2711`
- `Mean Absolute Error: 0.3278`

## Food Classification
This model is a computer vision task that involves assigning a label or category to an input image. The goal of this model is to accurately recognize and classify different objects or patterns within the images based on their visual features. The model is trained on a labeled dataset, where each image is associated with a specific class or category. This model ease users to get to know the unfamiliar dish just by uploading the corresponding food images.

#### Model Architecture
In this model, we perform transfer learning using `Restnet50`. We instantiate the ResNet50 model with pre-trained weights from the `ImageNet` dataset. We are not included the top (fully connected) layers of the ResNet50 model. We freeze all the layers in the ResNet50 model, allowing us to use the ResNet50 model as a feature extractor without modifying its original weights. After that, we create two another layers as followings:
1. `GlobalAveragePooling2D` : This layer computes the average value of each feature map, reducing the spatial dimensions and preserving the channel information.
2. `Dense layer` : We create this layer with 15 neurons and add softmax activation. The softmax activation produces a probability distribution over the 15 classes, representing the model's predicted probabilities for each class.

#### Model Training
We fit the model using the previously built architecture. We train the `train_generator` by utilized data generator, which generates batches of training data on the fly. We also add parameter `validation_data=val_generator`. This parameter specifies the validation data generator, which generates batches of validation data. In this phase, We perform `callbacks` to do early stopping when the validation set reachs the desirable accuracy.

#### Model Performance
The final performance of the model after iterating with 22 epochs is as follows:
- `loss: 0.1338`
- `accuracy: 0.9750` 
- `precision: 0.9863` 
- `recall: 0.9567` 

## Deployment
To deploy the model on the cloud and Android devices, we convert the model into three types of extensions:
1. `.h5`
2. `.tflite`
3. `.pb`

## Built With
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.7.0-orange)](https://www.tensorflow.org/)
[![NumPy](https://img.shields.io/badge/NumPy-1.21.4-blue)](https://numpy.org/)
[![Pandas](https://img.shields.io/badge/Pandas-1.3.3-green)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.4.3-red)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.11.2-yellow)](https://seaborn.pydata.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0.1-lightgrey)](https://scikit-learn.org/)

## How to Run Our Code/ Model
1. Open the .ipynb file in `Model` folder, and select one you would like to run.
2. Download the raw file via download button on the top right of code.
3. Open file in your code editor (you can use Google Colab).
4. Prepare dataset by downloading from the GitHub/drive link provided.
5. Run the code one by one, and make predictions by setting inputs based on requirements for each feature.

You can also predict the model results by downloading the .h5 model on GitHub in the Model folder. How to do it:
1. Download the model of your choice.
2. Load the `.h5` model, then run the predict output code.

## Authors (ML)
|          Nama         | Bangkit-ID |       Path       |       Contact       |
|:---------------------:|:----------:|:----------------:|:-------------------:|
|  [Jihan Kamilah](https://github.com/jihanKamilah)  |  M304DSY2993  | Machine Learning | <a href="https://www.linkedin.com/in/jihan-kamilah/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" /></a> |
|  [Santiana](https://github.com/Santiana1922)  |  M304DSY2487  | Machine Learning | <a href="https://www.linkedin.com/in/santiana/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" /></a> |
