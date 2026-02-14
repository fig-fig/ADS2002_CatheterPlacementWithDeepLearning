# Catheter Placement Classification Using Deep Learning
### ADS2002 Data Challenges 4 | Semester 2 2023

## Introduction
This project addresses a **critical healthcare challenge** by developing deep learning models to precisely detect and classify the placement accuracy of medical catheters in chest X-ray images.  
The goal was to determine which convolutional neural network among **ResNet, DenseNet, UNet, or a custom-built neural network**, could most accurately assess the placement of Endotracheal Tubes (ETT), Nasogastric Tubes (NGT), and Central Venous Catheters (CVC).

## Problem Statement
Catheter placement is essential in modern healthcare, but incorrect positioning can lead to severe complications:
- **Nasogastric tube misplacement** into airways occurs in up to 3% of cases, with 40% resulting in complications
- **Airway tube malpositioning** in adult patients outside the operating room occurs in up to 25% of cases
- **Human error** in high-stress situations, especially during peak hospital capacity, poses significant risks

Early recognition of malpositioned catheters is crucial for preventing hazardous complications and potential fatalities.

## Dataset

### Source
- **Kaggle**: RANZCR CLiP - Catheter and Line Position Challenge
- Chest X-ray images with annotations
- TFRecord files for efficient TensorFlow processing

### Data Structure
- **Total Images**: 30,083 training images
- **Unique Patients**: 3,255
- **Image Format**: JPEG chest X-rays
- **File Types**: 
  - `train.csv` - Training labels and metadata
  - `train_annotations.csv` - Detailed annotations
  - TFRecord files for training and testing

### Variables

#### Target Variables (11 Binary Labels)
**Endotracheal Tube (ETT)**
- `ETT - Abnormal` – ETT placement abnormal
- `ETT - Borderline` – ETT placement borderline abnormal
- `ETT - Normal` – ETT placement normal

**Nasogastric Tube (NGT)**
- `NGT - Abnormal` – NGT placement abnormal
- `NGT - Borderline` – NGT placement borderline abnormal
- `NGT - Incompletely Imaged` – NGT placement inconclusive due to imaging
- `NGT - Normal` – NGT placement normal

**Central Venous Catheter (CVC)**
- `CVC - Abnormal` – CVC placement abnormal
- `CVC - Borderline` – CVC placement borderline abnormal
- `CVC - Normal` – CVC placement normal

**Swan Ganz Catheter Presence**
- `Swan Ganz Catheter Present` – Presence indicator

#### Metadata
- `StudyInstanceUID` – Unique identifier for each X-ray image
- `PatientId` – Patient identifier (one patient can have multiple images)

## Project Workflow

1. **Data Quality Assessment**
   - High-quality dataset with no missing values
   - Comprehensive X-ray image collection
   - Properly annotated catheter placements

2. **Data Wrangling and Processing**
   - Image preprocessing and normalisation
   - TFRecord format conversion for efficient training
   - Train-test split preparation
   - Data augmentation techniques

3. **Exploratory Data Analysis**
   - Distribution analysis of catheter placement classes
   - Patient and image statistics
   - Visualisation of X-ray samples
   - Class imbalance assessment

4. **Model Development and Training**

   **A. Support Vector Machine (SVM)**
   - Initial baseline model
   - Provided solid foundation for comparison
   - Limited performance on image classification
   
   **B. Custom-Built Neural Network**
   - In-house designed architecture
   - Initial exploration of deep learning capabilities
   - Insights into training challenges with limited datasets
   - Foundation for understanding model complexity
   
   **C. ResNet-50**
   - Pre-trained on ImageNet database
   - Deep convolutional neural network
   - Transfer learning approach
   - Strong feature extraction capabilities
   - Showed potential but exhibited overfitting
   
   **D. DenseNet-121**
   - Densely connected layers architecture
   - Enhanced feature propagation
   - Depth and capacity for complex medical images
   - Overfitting observed in training data
   
   **E. UNet**
   - Specialised image segmentation architecture
   - **Test Accuracy: 80.0%** (Best Performance)
   - Superior false negative reduction
   - Excellent generalisation with minimal overfitting
   - Optimal for patient safety prioritization

5. **Evaluation Metrics**
   - **Accuracy Score**
   - **False Negative Rate** (critical for patient safety)
   - **False Positive Rate**
   - **Overfitting Assessment** (training vs. validation performance)

<br>

---

## Results

### Model Performance Comparison

| Model | Test Accuracy | Key Characteristics |
|-------|--------------|---------------------|
| **UNet** | **80.0%** | Best performance, minimal overfitting, prioritizes false negative reduction |
| **DenseNet-121** | **72.89%** | Good performance but some overfitting observed |
| **ResNet-50** | ~70% | Strong feature extraction, overfitting issues |
| **Custom CNN** | ~65% | Baseline neural network, training challenges |
| **SVM** | ~50% | Initial baseline, limited for image tasks |

### Key Findings

🔬 **Deep learning models** significantly outperform traditional machine learning for medical image analysis  
🎯 **UNet's architecture** is particularly well-suited for catheter placement classification  
⚠️ **Overfitting mitigation** is crucial when working with medical imaging datasets  
🏥 **False negative reduction** should be prioritized over overall accuracy for patient safety  
📊 **Transfer learning** from ImageNet provides valuable feature extraction capabilities  
💡 **Data quality** matters - high-quality annotated datasets enable better model performance  

### Clinical Significance

The UNet model demonstrates **proficiency in accurately predicting abnormalities in CVC placements**, with potential to:
- Reduce risks associated with catheter placement inaccuracies
- Enhance patient safety in high-stress medical procedures
- Minimise complications from malpositioned catheters
- Support healthcare practitioners in decision-making in high-stress situations

<br>

---

## Built With

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Matplotlib](https://img.shields.io/badge/matplotlib-11557C?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)
![ResNet](https://img.shields.io/badge/ResNet-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![DenseNet](https://img.shields.io/badge/DenseNet-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![UNet](https://img.shields.io/badge/UNet-00599C?style=for-the-badge&logo=keras&logoColor=white)
![CNN](https://img.shields.io/badge/CNN-013243?style=for-the-badge&logo=deep-learning&logoColor=white)
![SVM](https://img.shields.io/badge/SVM-F7931E?style=for-the-badge&logo=scikit--learn&logoColor=white)

## Technologies Used

- **Deep Learning Frameworks**: PyTorch, TensorFlow/Keras
- **Computer Vision**: OpenCV
- **Data Processing**: Pandas, NumPy
- **Model Architectures**: 
  - ResNet-50 (Pre-trained on ImageNet)
  - DenseNet-121
  - UNet (Image Segmentation)
  - Custom CNN
- **Data Format**: TFRecord (TensorFlow's binary storage format)
- **Development Environment**: Jupyter Notebooks

## Data Source

RANZCR CLiP - Catheter and Line Position Challenge  
Available on Kaggle: [https://www.kaggle.com/competitions/ranzcr-clip-catheter-line-classification](https://www.kaggle.com/competitions/ranzcr-clip-catheter-line-classification)

## License

This project was developed for academic purposes (2023).  
If reused or distributed, please provide proper academic attribution.

---

<div align="center">

**Enhancing Patient Safety Through Deep Learning** 🏥🤖

</div>
