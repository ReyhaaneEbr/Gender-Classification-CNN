
# Gender Classification Using an Optimized CNN

## Overview

This project implements a Convolutional Neural Network (CNN) for binary gender classification using facial images.

The model is inspired by the VGG architecture and is designed to extract hierarchical visual features while reducing overfitting through batch normalization, dropout, and data augmentation.

## Model Architecture

The proposed CNN consists of four convolutional blocks with increasing numbers of filters, followed by a classification head.

Main components:

- Convolutional layers with ReLU activation
- Batch Normalization
- Max Pooling
- Global Average Pooling
- Fully Connected Dense Layer
- Dropout
- Softmax output layer

The architecture uses Global Average Pooling instead of Flatten to reduce the number of trainable parameters.

## Dataset

The model uses facial images stored in Google Drive.

Dataset configuration:

- Number of images: 1,200
- Input image size: 224 × 224 pixels
- Number of classes: 2
- Image format: RGB
- Pixel normalization: [0, 1]

Class labels are extracted from image filenames. The second underscore-separated field is expected to contain the binary label (0 or 1).

**Note:** The dataset is not included in this repository. Users must provide their own dataset and configure the corresponding Google Drive path.

## Data Preprocessing

The preprocessing pipeline includes:

1. Loading images using OpenCV.
2. Converting images from BGR to RGB.
3. Resizing images to 224 × 224 pixels.
4. Normalizing pixel values to the range [0, 1].
5. Extracting binary labels from filenames.
6. Splitting the data into training, validation, and testing sets using stratified sampling.

Data augmentation is applied during training using:

- Random horizontal flipping
- Random rotation
- Random zoom

## Training Configuration

| Parameter | Value |
|---|---|
| Optimizer | Adam |
| Loss Function | Sparse Categorical Crossentropy |
| Batch Size | 32 |
| Maximum Epochs | 100 |
| Initial Learning Rate | 0.001 |
| Early Stopping | Enabled |
| Learning Rate Reduction | Enabled |
| Model Checkpoint | Best validation loss |

Early stopping and learning rate reduction are used to improve training efficiency and generalization.

## Evaluation Metrics

The model is evaluated using the following metrics:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

A separate test set is reserved for final evaluation.

## Project Structure

```text
Gender-Classification-CNN/
│
├── Optimized_CNN_Gender_Classification.ipynb
├── README.md
│
└── models/
    ├── optimized_gender_cnn.keras
    └── gender_classification_results.csv
```

The `models/` directory contains the trained model and evaluation results after running the notebook. These files are generated during execution and are not required to be included in the repository.

## Requirements

The project uses the following Python libraries:

- TensorFlow
- Keras
- OpenCV
- NumPy
- Pandas
- Matplotlib
- Scikit-learn

Install the dependencies using:

```bash
pip install tensorflow opencv-python numpy pandas matplotlib scikit-learn
```

## How to Run

1. Clone or download this repository.
2. Open the notebook in Google Colab.
3. Mount your Google Drive.
4. Place the facial image dataset in:

   `/content/gdrive/My Drive/photo`

5. Run the notebook cells sequentially.
6. The trained model and evaluation results will be saved in:

   `/content/gdrive/My Drive/models`

## Model Saving

The best model checkpoint is selected based on validation loss and saved in the Keras format:

`optimized_gender_cnn.keras`

Evaluation metrics are also exported to a CSV file.

## Notes

- This project is designed for binary classification with labels 0 and 1.
- The mapping between numerical labels and class names depends on the dataset.
- The dataset must follow the expected filename convention.
- Model performance depends on dataset quality, class balance, and training configuration.

## License

This project is intended for educational and research purposes.
