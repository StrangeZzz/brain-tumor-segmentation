Brain Tumor Segmentation with Deep Neural Networks
This repository contains the implementation and documentation for a fully automatic brain tumor segmentation method based on Deep Neural Networks (DNNs). The method is specifically tailored for glioblastomas (both low and high grade) as seen in MR images. The proposed approach leverages Convolutional Neural Networks (CNNs) to achieve state-of-the-art performance in brain tumor segmentation, while being significantly faster than existing methods.

Key Features
Novel CNN Architecture: The proposed CNN architecture exploits both local and global contextual features simultaneously, differing from traditional CNNs used in computer vision.

Efficient Training: A two-phase training procedure is employed to handle the imbalance of tumor labels, ensuring robust performance across different tumor regions.

Cascaded Architectures: The method explores cascaded CNN architectures that model dependencies between adjacent labels, improving segmentation accuracy.

Speed: The segmentation process is highly efficient, with processing times ranging from 25 seconds to 3 minutes per brain, making it practical for clinical use.

Dataset
The experiments were conducted on the BRATS 2013 dataset, which includes:

Training Dataset: 30 patient subjects (20 high grade and 10 low grade tumors) with pixel-accurate ground truth.

Test Dataset: 10 patient subjects (all high grade tumors) without ground truth.

Leaderboard Dataset: 25 patient subjects (21 high grade and 4 low grade tumors) without ground truth.

Each brain in the dataset includes four MRI modalities: T1, T1C, T2, and FLAIR, which are co-registered.

Model Architectures
The repository includes several CNN architectures:

TwoPathCNN: A two-pathway architecture that combines local and global features.

InputCascadeCNN: A cascaded architecture where the output of the first CNN is fed as input to the second CNN.

LocalCascadeCNN: A cascaded architecture where the output of the first CNN is concatenated with the first hidden layer of the second CNN.

MFCascadeCNN: A cascaded architecture that models label dependencies similarly to mean-field inference in Conditional Random Fields (CRFs).

Training Procedure
The training process involves:

Two-Phase Training: The first phase trains the model with a balanced distribution of labels, while the second phase fine-tunes the output layer with the natural distribution of labels.

Regularization: Techniques such as Dropout, L1, and L2 regularization are used to prevent overfitting.

Data Augmentation: Input images are flipped to augment the training data.

Results
The proposed method achieves competitive results on the BRATS 2013 dataset, outperforming many state-of-the-art methods in terms of both accuracy and speed. Key metrics include:

Dice Score: Measures the overlap between predicted and ground truth tumor regions.

Sensitivity: Measures the true positive rate.

Specificity: Measures the true negative rate.


Usage
To use the models, follow these steps:

Preprocessing: Apply minimal preprocessing to the MRI images, including intensity normalization and bias correction.

Training: Train the models using the two-phase training procedure described in the paper.

Testing: Evaluate the models on the test dataset and upload the results to the BRATS evaluation system for quantitative analysis.

Dependencies
Pylearn2: The implementation is based on the Pylearn2 library, which supports GPU acceleration for deep learning algorithms.

GPU: A GPU is recommended for training and testing to achieve the reported processing times.
