# BantuMasak App

BantuMasak is an application designed to assist users, particularly housewives, in creating a well-organized plan for the meals they want to prepare over several days. Our team has developed various features to simplify the process of meal planning. 
On the machine learning side, we have built two types of models: a recommendation system and an image classification system. 
Our recommendation system includes two types. First, it provides recipe recommendations by calculating ratings. Second, it suggests menus based on the user's input, specifically the ingredients they have on hand. 
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
We collected the datasets for both the recommendation system and food classification by scraping. For food classification, we scraped images from Google Images, resulting in a dataset with 25 food labels, each containing 50 images. 
On the other hand, for the recommendation system, we scraped data from the cookpad.com website. The dataset includes 800 different recipes, each with the food's title, ingredients, step-by-step instructions for making the dish, and the corresponding image URL.


## Network
For the food classification model, we utilized transfer learning with the ResNet50 architecture. We also incorporated Convolutional Neural Networks (CNNs) into the model, specifically modified for the 25 food labels.
In the case of the recommendation system, we developed two types. The first type, "Recommendation for You," involves calculating ratings and creating an embedding layer to provide suitable recipes for the user. 
The second type of recommendation system is based on user input. We tokenize the ingredients and create an embedding layer to suggest appropriate recipes based on the available ingredients provided by the user.

## Built With
* [Tensorflow Keras](https://www.tensorflow.org) - The AI framework used

## Authors
* **Jihan Kamilah (M304DSY2993)**  - [jihanKamilah](https://github.com/jihanKamilah)
* **Santiana (M304DSY2487)**       - [santiana1922](https://github.com/Santiana1922)
