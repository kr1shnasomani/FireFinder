# Fire Detection System

## Execution Guide:
1. Run the following command line in the terminal:
   ```

   ```

2. Download the dataset (link to the dataset: **https://www.kaggle.com/datasets/tharakan684/urecamain**)

## Overview:
This project develops a fire detection system using deep learning techniques. Here's a detailed breakdown:

1. **Dataset Preparation**:
   - The **URecamain dataset** is downloaded from Kaggle, containing labeled images for two classes: *Fire* and *Non-Fire*. The dataset is divided into training, validation, and testing directories.
   - The images are extracted using `zipfile` and organized into respective folders for efficient use in training.

2. **Data Augmentation and Preprocessing**:
   - **Training Data**: Augmented using `ImageDataGenerator` with rescaling, shearing, zooming, and horizontal flipping to enhance model robustness against variations in input images.
   - **Validation and Test Data**: Rescaled to standardize pixel values to the range [0, 1].
   - Images are resized to 224x224 pixels to match the input size of the chosen model.

3. **Model Architecture**:
   - **ResNet50**: A pre-trained deep convolutional neural network from TensorFlow's Keras Applications library is used for feature extraction. The `imagenet` weights are loaded, and the top classification layers are excluded for customization.
   - **Custom Layers**: The model is fine-tuned with additional layers:
     - `GlobalAveragePooling2D` for dimensionality reduction.
     - Fully connected layers with ReLU activation for feature learning.
     - A final dense layer with a sigmoid activation function for binary classification.

4. **Compilation and Training**:
   - **Optimizer**: The Adam optimizer is configured with a learning rate of 0.0001 for stable convergence.
   - **Loss Function**: Binary Crossentropy is used to optimize the model for two-class classification.
   - **Metrics**: Accuracy is tracked during training.
   - The model is trained over 25 epochs using the augmented training data and validated on a separate dataset. Performance metrics, including training and validation accuracy/loss, are recorded.

5. **Evaluation**:
   - The trained model achieves a validation accuracy of ~50%, suggesting possible challenges like dataset imbalance or insufficient feature representation.
   - A classification report and confusion matrix are generated to analyze precision, recall, F1-score, and support for each class.

6. **Visualization**:
   - Training progress is visualized using matplotlib with:
     - Accuracy over epochs for training and validation.
     - Loss over epochs for training and validation.

7. **Prediction Functionality**:
   - A custom function accepts an image path, preprocesses the input, and uses the model to predict whether the image contains fire.
   - The result is displayed visually, including the predicted label ("Fire" or "No Fire") and the confidence score.

8. **Output**:
   - The model is saved in Keras format for future use.
   - Predictions are showcased using sample images from the dataset, illustrating the system's practical application.

This project leverages transfer learning and real-time image classification for fire detection but highlights areas for improvement, such as dataset enhancement, fine-tuning of hyperparameters and addressing potential class imbalances for better performance.
