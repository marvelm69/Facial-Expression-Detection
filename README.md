# Facial Expression Detection Based on Machine Learning for Public Service Evaluation

## Introduction

Public service officers' friendliness plays a significant role in shaping public perception of service quality. Traditional methods for evaluating this, such as surveys, are time-consuming, expensive, and subject to bias. In this project, we propose a machine learning framework that uses facial expression recognition to evaluate officers' friendliness in real-time, offering an efficient, unbiased alternative to conventional methods.

This system could be a key tool for public institutions, enabling them to receive objective feedback and make immediate improvements to service quality.

## Table of Contents
- [Introduction](#introduction)
- [Overview](#overview)
- [Models](#models)
- [Methodology](#methodology)
- [Datasets](#datasets)
- [Results Discussion](#results-discussion)
- [Real-Time Simulation](#real-time-simulation)
- [Conclusion](#conclusion)
- [Future Work](#future-work)
- [Authors](#authors)
- [License](#license)

## Overview
This project focuses on developing a machine learning framework to detect facial expressions and evaluate the friendliness of public service officers in real-time. The framework utilizes images from popular datasets like the Karolinska Directed Emotional Faces (KDEF) and Real-world Affective Faces Database (RAF-DB) to train machine learning models using two distinct approaches.

## Models
The first approach implements two pre-trained models based on transfer learning, MobileNet and VGGNet, with additional patch extraction and self-attention mechanisms. The second approach leverages classical machine learning techniques such as Random Forest, XGBoost, Neural Network, and Support Vector Machine (SVM) based on facial landmarks.

### Model Performance Comparison:

#### Tabel I: Performance Comparison of Convolutional Models

| Model Konvolusi       | Dataset | Pre. | Rec. | F1  | AUC | Acc. |
|-----------------------|---------|------|------|-----|-----|------|
| **Attention MobileNet**          | KDEF    | 0.97 | 0.97 | 0.97| 0.51| 0.96 |
|           | RAF-DB  | 0.80 | 0.80 | 0.80| 0.49| 0.80 |
| **Attention VGGNet**          | KDEF    | 0.93 | 0.93 | 0.73| 0.50| 0.89 |
|           | RAF-DB  | 0.59 | 0.60 | 0.58| 0.50| 0.60 |

#### Tabel II: Performance Comparison of Landmark Models

| Model Landmark        | Dataset | Pre. | Rec. | F1  | AUC | Acc. |
|-----------------------|---------|------|------|-----|-----|------|
| **SVM**               | KDEF    | 0.74 | 0.75 | 0.74| 0.93| 0.75 |
|                       | RAF-DB  | 0.71 | 0.72 | 0.71| 0.89| 0.72 |
| **Neural Network**     | KDEF    | 0.70 | 0.71 | 0.71| 0.92| 0.70 |
|                       | RAF-DB  | 0.70 | 0.70 | 0.70| 0.90| 0.70 |
| **Random Forest**      | KDEF    | 0.70 | 0.69 | 0.70| 0.90| 0.70 |
|                       | RAF-DB  | 0.69 | 0.68 | 0.68| 0.91| 0.71 |
| **XGBoost**            | KDEF    | 0.69 | 0.70 | 0.69| 0.91| 0.70 |
|                       | RAF-DB  | 0.68 | 0.68 | 0.69| 0.92| 0.71 |

## Methodology

### Data Augmentation
Data augmentation techniques were applied differently for the two datasets:
- **KDEF Dataset**: No data augmentation was performed since this dataset has balanced classes.
- **RAF-DB Dataset**: To balance the underrepresented classes such as "angry," "disgust," and "fear," the data was augmented with horizontal flips, rotations, shifts in width and height, and brightness adjustments.

### Convolutional Model with Attention
The project used **MobileNet** and **VGGNet** as base models in a transfer learning approach, adding patch extraction and self-attention mechanisms. The attention mechanism helps the model focus on key facial features, such as the eyes and mouth, when recognizing facial expressions.

### Facial Landmark Model
For the facial landmark-based models, facial landmarks were extracted using the **Dlib** library. These landmarks were then used to compute features such as distances between key facial points. Models like **SVM**, **Neural Networks**, **Random Forest**, and **XGBoost** were trained using these distance-based features.

### Evaluation Metrics
The models were evaluated using multiple metrics such as Precision, Recall, F1-Score, Accuracy, and AUC (Area Under the ROC Curve). Grad-CAM (Gradient-weighted Class Activation Mapping) was used to visualize which parts of the face the model focuses on during prediction.

### Flowchart of the Methodology:
![Flowchart](https://github.com/user-attachments/assets/a4387a84-54e8-4ac3-9b2e-7716089d8ba8)

## Datasets
1. **KDEF**: Contains 4,900 images of human faces displaying seven different expressions (angry, disgust, fear, happy, neutral, sad, surprise). Each expression is captured from five different angles. We used 700 images per class, splitting them into 80% for training and 20% for testing.
![image](https://github.com/user-attachments/assets/4d5aaeef-42fb-4c5b-887e-09b502f80556)
**Dataset [LINK](https://www.kaggle.com/datasets/tom99763/testtt)**
3. **RAF-DB**: Composed of approximately 30,000 images with seven facial expressions. Due to class imbalance, data augmentation techniques such as horizontal flips and brightness adjustments were applied to increase dataset variability.
![image](https://github.com/user-attachments/assets/92c48dec-f8fd-42ed-8603-e04eeb25a2dc)
**Dataset [LINK](https://www.kaggle.com/datasets/raufmomin/facial-expressions-dataset)**

## Results Discussion

### Convolutional Model Performance
The best model using the convolutional approach was **MobileNet** with an accuracy of 96%, precision of 97%, recall of 97%, and F1-score of 97% on the **KDEF** dataset. Although the AUC was lower at 0.51, the model’s high accuracy indicates its effectiveness at recognizing facial expressions in controlled environments.

### Landmark-Based Model Performance
The **SVM** model performed best among the landmark-based models with an accuracy of 75%, precision of 74%, recall of 75%, and F1-score of 74% on the **KDEF** dataset. The SVM model demonstrated a high AUC of 0.93, indicating good confidence in its predictions despite lower accuracy compared to the convolutional models.

The results demonstrate that convolutional models are better suited for complex, detailed facial recognition tasks, while landmark-based models provide robust performance with simpler features.

## Real-Time Simulation

A 10-minute real-time simulation was conducted using the best-performing MobileNet model to evaluate the friendliness of a public service officer at Universitas Bina Nusantara’s promotion team. The officer’s facial expressions were recorded and analyzed, and the results were saved into a CSV file that tracked facial expressions over time.

This simulation showcases the system's potential to provide real-time feedback on public service officers' interactions with the public, offering an efficient way to evaluate service quality.
![WhatsApp Image 2024-09-18 at 15 58 51_c422222a](https://github.com/user-attachments/assets/cfa4d55a-d36d-4a83-9cc5-612d52247d81)

## Conclusion

This project successfully developed a framework for detecting facial expressions to evaluate public service officers' friendliness. The MobileNet-based model outperformed other models, and further improvements could include integrating other modalities, such as voice or body movement, to increase prediction accuracy.

## Future Work

Future improvements could include:
- **Dataset Expansion**: Creating a larger dataset more representative of the Indonesian population will improve the model's real-world applicability.
- **Integration of Other Modalities**: The inclusion of voice recognition or body movement analysis could further enhance the accuracy of the model in assessing public service officers' friendliness.
- **Multi-modal Systems**: Combining facial expression recognition with audio analysis (e.g., tone of voice) could create a more comprehensive evaluation tool for assessing service quality.

## Authors
- [Marvel Martawidjaja](https://github.com/marvelm69)
- [Matthew Lefrandt](https://github.com/MatthewLefrandt)
- [Steve Marcello Liem](https://github.com/steveee27)
  

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
