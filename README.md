\# Chest X-ray Pneumonia Classification using CNN



A Computer Vision project for classifying pediatric chest X-ray images into three categories:



\- NORMAL

\- BACTERIA Pneumonia

\- VIRUS Pneumonia



The project uses a custom Convolutional Neural Network (CNN) with image preprocessing, data augmentation, performance evaluation, and Grad-CAM visualization for model interpretability.



\---



\## Project Objective



The objective of this project is to build a deep learning model capable of classifying chest X-ray images into:



1\. Normal

2\. Bacterial Pneumonia

3\. Viral Pneumonia



The project also analyzes class imbalance, model errors, and the difficulty of distinguishing bacterial pneumonia from viral pneumonia.



\---



\## Dataset



Dataset: \*\*Labeled Chest X-ray Images\*\*



Source:  

https://www.kaggle.com/datasets/tolgadincer/labeled-chest-xray-images



\### Dataset Statistics



| Split | NORMAL | BACTERIA | VIRUS | Total |

|-------|--------|----------|-------|-------|

| Train | 1349   | 2538     | 1345  | 5232  |

| Test  | 234    | 242      |  148  | 624   |

| Total | 1583   |  2780    | 1493  | 5856  |



The dataset contains pediatric chest X-ray images from patients approximately 1–5 years old.



\---



\## Data Preprocessing



The following preprocessing techniques were applied:



\- Image resizing to `224 × 224`

\- Pixel normalization to `\[0, 1]`

\- Training / validation split

\- One-hot encoded class labels

\- Data augmentation:

&#x20; - Rotation

&#x20; - Horizontal flip

&#x20; - Zoom



The final dataset split used:



\- Training: 4185 images

\- Validation: 1047 images

\- Testing: 624 images



\---



\## CNN Architecture



The model consists of:



\- Conv2D — 32 filters

\- MaxPooling2D

\- Conv2D — 64 filters

\- MaxPooling2D

\- Conv2D — 128 filters

\- MaxPooling2D

\- Flatten

\- Dense — 128 neurons

\- Dropout — 0.5

\- Softmax output layer — 3 classes



\### Training Configuration



\- Optimizer: Adam

\- Learning Rate: 0.001

\- Loss Function: Categorical Crossentropy

\- Maximum Epochs: 200

\- Batch Size: 32

\- Early Stopping: Enabled

\- Model Checkpoint: Enabled



\---



\## Final Test Results



| Metric    | Score      |

|-----------|------------|

| Accuracy  | \*\*87.02%\*\* |

| Precision | \*\*87.82%\*\* |

| Recall    | \*\*87.02%\*\* |

| F1-score  | \*\*86.90%\*\* |



\### Class-wise Performance

\--------------------------------------------

| Class    | Precision | Recall | F1-score |

|----------|----------:|-------:|---------:|

| NORMAL   | 0.98      | 0.85   | 0.91     |

| BACTERIA | 0.81      | 0.98   | 0.89     |

| VIRUS    | 0.83      | 0.72   | 0.77     |

\--------------------------------------------



\## Confusion Matrix Analysis



The final model produced the following results:



\- NORMAL: \*\*200 / 234\*\* correctly classified

\- BACTERIA: \*\*236 / 242\*\* correctly classified

\- VIRUS: \*\*107 / 148\*\* correctly classified



The largest classification error occurred between viral and bacterial pneumonia:



\- \*\*41 VIRUS images were predicted as BACTERIA\*\*



This indicates that distinguishing viral pneumonia from bacterial pneumonia remains the main challenge for the model.



\---



\## Grad-CAM Explainability



Grad-CAM was implemented to visualize the regions of chest X-ray images that influenced the CNN's predictions.



This provides additional interpretability by showing which image regions contribute most strongly to a prediction.



Grad-CAM should be considered an interpretability technique rather than a clinically validated disease-localization method.



\---



\## Project Structure



```text

chest-xray-pneumonia-classification/

│

├── notebooks/

│   └── chest\_xray\_pneumonia\_classification.ipynb

│

├── images/

│

├── README.md

├── requirements.txt

└── .gitignore



###  Technologies Used
Python
TensorFlow / Keras
NumPy
Pandas
Matplotlib
Scikit-learn
Pillow
Kaggle
Jupyter Notebook


Installation

Clone the repository:

git clone https://github.com/newaz-dev/chest-xray-pneumonia-classification.git

cd chest-xray-pneumonia-classification

pip install -r requirements.txt


### Key Findings:

The CNN achieved 87.02% test accuracy.
Bacterial pneumonia achieved the highest recall at approximately 98%.
Viral pneumonia was the most challenging class, with approximately 72% recall.
Class imbalance may contribute to stronger performance on the BACTERIA class.
Some viral pneumonia images were visually difficult for the model to distinguish from bacterial pneumonia.

### Limitations:

The dataset is imbalanced across classes.
The dataset contains pediatric chest X-rays, so results may not generalize to adult patients.
Bacterial and viral pneumonia may contain similar visual characteristics.
Image quality, positioning, brightness, and contrast may influence predictions.
The model is a Basic CNN and could potentially be improved using transfer learning or more advanced architectures.


### Disclaimer

This project was developed for educational and Computer Vision research purposes.

The model is not intended for clinical diagnosis and should not replace evaluation by qualified medical professionals.


Author

Md Shah Newaz Fahmir Hridoy

GitHub: newaz-dev
