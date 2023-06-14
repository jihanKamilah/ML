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
│       ── Image Classification
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
│       │       ├── clean_recipe_v3.csv
│       │       ├── Prdataset_user_rating_v4.csv
└── Model
        ├── Image Classification
        │       └── Assets
        │       │       └── Accuracy history.png
        │       │       └── Loss history.png
        │       └── Converted file
        │       │       └── model.pb
        │       │       └── converted_model_food_classification_v1.tflite
        │       │       └── model_food_classification_v1.h5
        │       └── Food Classification_v1.ipynb
        └── Recommendation System
                └── Assets
                │       └── Epochs history.png
                └── Converted file
                │       └── model.pb
                │       └── converted_model_recommendation_for_you_v4.tflite
                │       └── model_recommendation_for_you_v4.h5
                └── recommendation for you v4.ipynb
```

## Datasets
We collected the datasets for both the recommendation system and food classification by scraping. For food classification, we scraped images from Google Images, resulting in a dataset with 15 food labels, each containing 100 images. 
On the other hand, for the recommendation system, we scraped data from the cookpad.com website. The dataset includes 864 different recipes, each with the food's id, title, ingredients, step-by-step instructions for making the dish, and the corresponding image URL.


## Network
For the food classification model, we utilized transfer learning with the ResNet50 architecture. We also incorporated Convolutional Neural Networks (CNNs) into the model, specifically modified for the 15 food labels.
In the case of the recommendation system, the model calculates ratings and creating an embedding layer to suggest suitable recipes for the user. 


## Built With
* [Tensorflow Keras](https://www.tensorflow.org) - The AI framework used

## Authors
* **Jihan Kamilah (M304DSY2993)**  - [jihanKamilah](https://github.com/jihanKamilah)
* **Santiana (M304DSY2487)**       - [santiana1922](https://github.com/Santiana1922)
