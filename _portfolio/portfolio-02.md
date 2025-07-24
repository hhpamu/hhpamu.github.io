---
title: "Deep Learning Exercises - WIP"
excerpt: "24-788 and 24-789 course exercises, Carnegie Mellon University <br/><img src='/images/ACSI_project/coverimage_500x250.jpg'>"
collection: portfolio
---

The various deep learning works seen here are part of the Introduction to Deep Learning and Intermediate Deep Learning coursework at Carnegie Mellon University.

# Airfoil Self-Noise Prediction Using a Multi-Layer Perceptron


<img src='/images/Deep_Learning/Airfoil_Noise/airfoil_figure.png' alt="airfoil_figure" class="center">
<p style="text-align:center"> <i>[AIRFOIL FIGURE]</i></p>

This project focused on developing a neural network to predict airfoil self-noise based on five input features: frequency, angle of attack, chord length, free-stream velocity, and suction side displacement thickness. The target output was the scaled sound pressure level in decibels. The task used a regression-based formulation, and the model was trained using PyTorch.

I implemented a custom Dataset class to load and batch the data (split into training, validation, and test sets), and defined a Multi-Layer Perceptron with configurable depth and width, along with a ReLU activation function. For evaluating the performance of the networks, and MSE loss was used

The network architecture, hyperparameters (learning rate, weight decay, batch size), and training loop were tuned across multiple configurations to evaluate their effect on model performance. Training was monitored using loss curves, and the best configuration, Combination 4, achieved a test loss of 11.913, indicating strong model generalization. I analyzed the impact of model depth, batch size, and learning rate on convergence rate and final error, and presented the results with accompanying plots.

Combination 1
hid_dim = [64, 32],
num_epochs = 1000,
lr = 0.01,
weight_decay = 1e-5,
batch_size = 32

Train Loss: 0.4474	Validation Loss: 0.7819
TOTAL EVALUATION LOSS: 16.13764

[comb1 IMAGE]
Explanation
Compared to the test run above, increasing the number of neurons improved the model's performance on the test dataset by reducing the test loss. However, model1 didnt generalize well enough as evidenced by the difference in training and validation losses.

Combination 2
hid_dim = [32, 64],
num_epochs = 1000,
lr = 0.01,
weight_decay = 1e-5,
batch_size = 32

Train Loss: 0.4739	Validation Loss: 0.5971
TOTAL EVALUATION LOSS: 14.82711

[comb2 IMAGE]

Explanation
The validation and training are very close, indicating a a good amount of generalization. For this combination, I just wanted to see if flipping the number of neurons made any difference, and apparently it improved the performance slightly, and generalized better compared to model1. The plots are still jittery, likely due to a high learning rate.

Combination 3
hid_dim = [32, 64, 32],
num_epochs = 2000,
lr = 0.01,
weight_decay = 1e-5,
batch_size = 32

Train Loss: 0.2237	Validation Loss: 0.5934
TOTAL EVALUATION LOSS: 12.83629

[comb3 IMAGE]

Explanation
The loss plots look jittery, probably because the learning rate is too high. However, adding an extra layer and running for more epochs appears to have improved the model's performance on the test data. The validation loss is higher than the train loss, indicating minor degree of overfitting.

Combination 4
hid_dim = [64, 128, 256, 256, 128, 64],
num_epochs = 2500,
lr = 0.0005,
weight_decay = 1e-6,
batch_size = 128

Train Loss: 0.0233	Validation Loss: 0.1845
TOTAL EVALUATION LOSS: 11.91328

[comb4 IMAGE]

****Explanation****
A wider and deeper neural network, along with a learning rate of 0.0005 and a batch size of 128 seemed to give the lowest error on the test data. I believe that the complexity of the network and the larger batch size impacted the most in significantly lowering the test error. The test loss curve's spikes indicate that the learning rate may be too high in the beginning. Overall, there appears to be slight overfitting as the final validation error is higher than the training error. I didnt get a chance to fix this due to time constraints.

### References
Thomas F. Brooks, D. Stuart Pope, and Michael A. Marcolini. Airfoil self-noise and prediction. NTRS Author Affiliations: PRC Kentron, Inc., Hampton, NASA Langley Research Center NTRS Report/Patent Number: L16528 NTRS Document ID: 19890016302 NTRS Research Center: Legacy CDMS (CDMS). July 1989. Url: https://ntrs.nasa.gov/citations/19890016302 (visited on 01/24/2023).

RobertoLopez.Airfoil Self-Noise Data Set. Mar. 2014. URL: https://archive.ics.uci.edu/ml/datasets/airfoil+self-noise.

# CIFAR-10 Image Classification Using a Convolutional Neural Network

In this project, I implemented a Convolutional Neural Network (CNN) to perform image classification on the CIFAR-10 dataset, which consists of 60,000 32×32 color images across 10 object categories. The goal was to train a model that generalizes well to unseen data while avoiding overfitting, using PyTorch as the primary framework. 

### Network Architecture
The training pipeline included dataset normalization, data augmentation with random 45 degree rotation, random crop and random vertical flip, and network regularization using dropout. I defined a ResNet inspired CNN architecture consisting of multiple convolutional layers with ReLU activation and max-pooling, followed by fully connected layers for classification. Cross-entropy loss was used with the Adam optimizer.
<!--
```python
===================================================================================================================
Layer (type:depth-idx)                   Input Shape               Kernel Shape              Output Shape
===================================================================================================================
CNN_RES                                  [128, 3, 32, 32]          --                        [128, 10]
├─Sequential: 1-1                        [128, 3, 32, 32]          --                        [128, 64, 32, 32]
│    └─Conv2d: 2-1                       [128, 3, 32, 32]          [3, 3]                    [128, 64, 32, 32]
│    └─BatchNorm2d: 2-2                  [128, 64, 32, 32]         --                        [128, 64, 32, 32]
│    └─ReLU: 2-3                         [128, 64, 32, 32]         --                        [128, 64, 32, 32]
├─Sequential: 1-2                        [128, 64, 32, 32]         --                        [128, 128, 16, 16]
│    └─Conv2d: 2-4                       [128, 64, 32, 32]         [3, 3]                    [128, 128, 32, 32]
│    └─BatchNorm2d: 2-5                  [128, 128, 32, 32]        --                        [128, 128, 32, 32]
│    └─ReLU: 2-6                         [128, 128, 32, 32]        --                        [128, 128, 32, 32]
│    └─MaxPool2d: 2-7                    [128, 128, 32, 32]        2                         [128, 128, 16, 16]
├─Sequential: 1-3                        [128, 128, 16, 16]        --                        [128, 128, 16, 16]
│    └─Conv2d: 2-8                       [128, 128, 16, 16]        [3, 3]                    [128, 128, 16, 16]
│    └─BatchNorm2d: 2-9                  [128, 128, 16, 16]        --                        [128, 128, 16, 16]
│    └─ReLU: 2-10                        [128, 128, 16, 16]        --                        [128, 128, 16, 16]
│    └─Conv2d: 2-11                      [128, 128, 16, 16]        [3, 3]                    [128, 128, 16, 16]
│    └─BatchNorm2d: 2-12                 [128, 128, 16, 16]        --                        [128, 128, 16, 16]
│    └─ReLU: 2-13                        [128, 128, 16, 16]        --                        [128, 128, 16, 16]
├─Sequential: 1-4                        [128, 128, 16, 16]        --                        [128, 256, 8, 8]
│    └─Conv2d: 2-14                      [128, 128, 16, 16]        [3, 3]                    [128, 256, 16, 16]
│    └─BatchNorm2d: 2-15                 [128, 256, 16, 16]        --                        [128, 256, 16, 16]
│    └─ReLU: 2-16                        [128, 256, 16, 16]        --                        [128, 256, 16, 16]
│    └─MaxPool2d: 2-17                   [128, 256, 16, 16]        2                         [128, 256, 8, 8]
├─Sequential: 1-5                        [128, 256, 8, 8]          --                        [128, 10]
│    └─Flatten: 2-18                     [128, 256, 8, 8]          --                        [128, 16384]
│    └─Linear: 2-19                      [128, 16384]              --                        [128, 500]
│    └─ReLU: 2-20                        [128, 500]                --                        [128, 500]
│    └─Linear: 2-21                      [128, 500]                --                        [128, 84]
│    └─ReLU: 2-22                        [128, 84]                 --                        [128, 84]
│    └─Linear: 2-23                      [128, 84]                 --                        [128, 10]
│    └─Dropout: 2-24                     [128, 10]                 --                        [128, 10]
===================================================================================================================
Total params: 8,902,826
Trainable params: 8,902,826
Non-trainable params: 0
Total mult-adds (G): 30.31
===================================================================================================================
Input size (MB): 1.57
Forward/backward pass size (MB): 671.70
Params size (MB): 35.61
Estimated Total Size (MB): 708.88
===================================================================================================================
```
-->

### Training

During training, I monitored both training and validation loss and accuracy, and tuned the model to maximize test performance.

<img src='/images/Deep_Learning/CIFAR10_CNN/final_loss_acc_plot.png' alt="final_loss_acc_plot" class="center">
<p style="text-align:center"> <i>[final_loss_acc_plot]</i></p>

The final model was trained for 50 epochs and achieved a test accuracy of 83.63%, demonstrating strong classification performance across multiple classes. The following are some key steps taken to improve:
  * a
  * b
  * c

### References

CIFAR 10 Dataset: <a href="https://www.cs.toronto.edu/~kriz/cifar.html" target="_blank">www.cs.toronto.edu/~kriz/cifar.html</a>


# Graph Neural Network for Molecular Solubility Prediction
This project explored the use of Graph Neural Networks (GNNs) for predicting aqueous solubility from molecular structure, using PyTorch Geometric. Each molecule was represented as a graph with atoms as nodes and bonds as edges. Node and edge features were precomputed, and the task was framed as a regression problem to predict log solubility.

I implemented a GCN-based model using the GCNConv layer from torch_geometric.nn, and trained it using mean squared error (MSE) loss. The dataset was preprocessed using the provided get_dataset() function, and the training loop was augmented with early stopping and model checkpointing to prevent overfitting.

The model was configured with 8 graph convolutional layers, each using 128 channels, followed by a single linear layer that maps the 128-dimensional output to the final prediction. Batch normalization was applied after convolutional layers 1, 2, 3, 5, and 6, with the selection based on trial and error. The training objective used mean squared error loss (nn.MSELoss) appropriate for the regression task. Optimization was performed using Adam with a learning rate of 0.0001 and weight decay of 1e-5. The model was trained for 100 epochs, which provided the best balance between underfitting and overfitting. The model met performance expectations by achieving a sum of mean square errors between the model prediction and the label of 167.

<img src='/images/Deep_Learning/GNN/GNN_loss_plot.png' alt="GNN_loss_plot" class="center">
<p style="text-align:center"> <i>[GNN_loss_plot]</i></p>

<img src='/images/Deep_Learning/GNN/pred_label_plot.png' alt="pred_label_plot" class="center">
<p style="text-align:center"> <i>[pred_label_plot]</i></p>

### References
Kipf, Thomas N., and Max Welling. "Semi-supervised classification with graph convolutional networks." arXiv preprint arXiv:1609.02907 (2016).

# LSTM Modeling of Transient Hagen–Poiseuille Flow

This project involved building and training an LSTM model to predict the transient velocity profile of incompressible laminar flow through a pipe, governed by the simplified Navier–Stokes equations for Hagen–Poiseuille flow. The goal was to learn the evolution of the axial velocity field from initial flow conditions using a recurrent neural network trained on simulated time series data.

I implemented a multi-layer LSTM using PyTorch’s nn.LSTMCell, enabling step-wise control over hidden states. The model was trained on a dataset consisting of velocity measurements at 17 spatial points over 20 time steps, where each input sequence began with physical flow parameters (diameter, pressure gradient, viscosity, density) followed by 19 steps of observed velocity. During testing, only the initial condition was provided to autoregressively predict the entire 20-step sequence.

<!--
```python
==========================================================================================
Layer (type:depth-idx)                   Output Shape              Param #
==========================================================================================
FlowLSTM                                 [64, 19, 17]              --
├─LSTMCell: 1-1                          [64, 128]                 75,264
├─LSTMCell: 1-2                          [64, 128]                 132,096
├─Linear: 1-3                            [64, 17]                  2,193
├─LSTMCell: 1-4                          [64, 128]                 (recursive)
├─LSTMCell: 1-5                          [64, 128]                 (recursive)
├─Linear: 1-6                            [64, 17]                  (recursive)
├─LSTMCell: 1-7                          [64, 128]                 (recursive)
├─LSTMCell: 1-8                          [64, 128]                 (recursive)
├─Linear: 1-9                            [64, 17]                  (recursive)
├─LSTMCell: 1-10                         [64, 128]                 (recursive)
├─LSTMCell: 1-11                         [64, 128]                 (recursive)
├─Linear: 1-12                           [64, 17]                  (recursive)
├─LSTMCell: 1-13                         [64, 128]                 (recursive)
├─LSTMCell: 1-14                         [64, 128]                 (recursive)
├─Linear: 1-15                           [64, 17]                  (recursive)
├─LSTMCell: 1-16                         [64, 128]                 (recursive)
├─LSTMCell: 1-17                         [64, 128]                 (recursive)
├─Linear: 1-18                           [64, 17]                  (recursive)
├─LSTMCell: 1-19                         [64, 128]                 (recursive)
├─LSTMCell: 1-20                         [64, 128]                 (recursive)
├─Linear: 1-21                           [64, 17]                  (recursive)
├─LSTMCell: 1-22                         [64, 128]                 (recursive)
├─LSTMCell: 1-23                         [64, 128]                 (recursive)
├─Linear: 1-24                           [64, 17]                  (recursive)
├─LSTMCell: 1-25                         [64, 128]                 (recursive)
├─LSTMCell: 1-26                         [64, 128]                 (recursive)
├─Linear: 1-27                           [64, 17]                  (recursive)
├─LSTMCell: 1-28                         [64, 128]                 (recursive)
├─LSTMCell: 1-29                         [64, 128]                 (recursive)
├─Linear: 1-30                           [64, 17]                  (recursive)
├─LSTMCell: 1-31                         [64, 128]                 (recursive)
├─LSTMCell: 1-32                         [64, 128]                 (recursive)
├─Linear: 1-33                           [64, 17]                  (recursive)
├─LSTMCell: 1-34                         [64, 128]                 (recursive)
├─LSTMCell: 1-35                         [64, 128]                 (recursive)
├─Linear: 1-36                           [64, 17]                  (recursive)
├─LSTMCell: 1-37                         [64, 128]                 (recursive)
├─LSTMCell: 1-38                         [64, 128]                 (recursive)
├─Linear: 1-39                           [64, 17]                  (recursive)
├─LSTMCell: 1-40                         [64, 128]                 (recursive)
├─LSTMCell: 1-41                         [64, 128]                 (recursive)
├─Linear: 1-42                           [64, 17]                  (recursive)
├─LSTMCell: 1-43                         [64, 128]                 (recursive)
├─LSTMCell: 1-44                         [64, 128]                 (recursive)
├─Linear: 1-45                           [64, 17]                  (recursive)
├─LSTMCell: 1-46                         [64, 128]                 (recursive)
├─LSTMCell: 1-47                         [64, 128]                 (recursive)
├─Linear: 1-48                           [64, 17]                  (recursive)
├─LSTMCell: 1-49                         [64, 128]                 (recursive)
├─LSTMCell: 1-50                         [64, 128]                 (recursive)
├─Linear: 1-51                           [64, 17]                  (recursive)
├─LSTMCell: 1-52                         [64, 128]                 (recursive)
├─LSTMCell: 1-53                         [64, 128]                 (recursive)
├─Linear: 1-54                           [64, 17]                  (recursive)
├─LSTMCell: 1-55                         [64, 128]                 (recursive)
├─LSTMCell: 1-56                         [64, 128]                 (recursive)
├─Linear: 1-57                           [64, 17]                  (recursive)
==========================================================================================
Total params: 209,553
Trainable params: 209,553
Non-trainable params: 0
Total mult-adds (G): 32.28
==========================================================================================
Input size (MB): 0.08
Forward/backward pass size (MB): 2.66
Params size (MB): 0.84
Estimated Total Size (MB): 3.58
==========================================================================================
```
-->

### Training
Training was performed using MSE loss and the Adam optimizer, with tuned hyperparameters to minimize L1 and L2 errors. The model was evaluated by comparing predicted flow profiles to the true time evolution across the pipe radius. The model was initially trained using three LSMCell layers with a batch size of 128 and dropout set to 0.1; however, this configuration yielded poor predictions, with L1 and L2 losses in the ranges of 1e-5 and 1e-3, respectively. After resolving shape and datatype mismatches, I reduced the model to two LSMCell layers, adjusted the batch size to 64, and increased the dropout rate to 0.15, which slightly improved the results but still produced unsatisfactory predictions. The final breakthrough occurred after correcting a timestep loop error in the forward and test methods, which resolved the prediction issue and yielded acceptable L1 and L2 losses. The final training setup consisted of 20 epochs, a learning rate of 0.001, a dropout rate of 0.15, and a batch size of 64.

<img src='/images/Deep_Learning/LSTM/LSTM_loss_plot.png' alt="LSTM_loss_plot" class="center">
<p style="text-align:center"> <i>[LSTM_loss_plot]</i></p>

<img src='/images/Deep_Learning/LSTM/LSTM_pred_plot.png' alt="LSTM_pred_plot" class="center">
<p style="text-align:center"> <i>[LSTM_pred_plot]</i></p>

<img src='/images/Deep_Learning/LSTM/LSTM_truth_plot.png' alt="LSTM_truth_plot" class="center">
<p style="text-align:center"> <i>[LSTM_truth_plot]</i></p>

The final model achieved a total L1 error of 4580.517 and L2 error of 14.075, meeting satisfactory performance. The project demonstrates how sequence learning methods like LSTM can effectively capture temporal dynamics in physical systems governed by PDEs, and serve as surrogates for numerical solvers.

### References
The course assignment guide.

Nina Prakash for providing her code for generating Hagen-Poiseuille flow data.

# Airfoil Shape Generation Using Variational Autoencoders and GANs

This project focused on generative modeling of airfoil geometries using Variational Autoencoders (VAEs) and Generative Adversarial Networks (GANs). The input dataset consisted of 1,600 airfoil shapes from the UIUC Airfoil Database, preprocessed by interpolating to a shared x-coordinate grid and scaling y-coordinates to the range [−1, 1]. The generative models were trained to learn the underlying distribution of airfoil shapes using only the y-coordinates as input.

### VAE model
The VAE architecture employed a 3-layer encoder (256–512–512 units) and a 2-layer decoder (512–512 units), each with ReLU activations and a final Tanh activation in the decoder. The model was trained for 30 epochs using an MSE loss term, weighted equally, with a small KL divergence regularization term (weight = 0.0001). Adam optimizer was used with a learning rate of 0.001. Tuning included expanding layer widths and deepening the encoder and decoder to improve expressiveness. The resulting generated airfoils were consistent and realistic, although the diversity of shapes was somewhat limited.


<img src='/images/Deep_Learning/Airfoil_Shape/VAE_Loss.png' alt="VAE_Loss" class="center">
<p style="text-align:center"> <i>[VAE_Loss]</i></p>

[  Real airfoils ] [  VAE reconstructed airfoils ]
[  VAE generated airfoils ]


# Face Image Generation Using GAN on CelebA Dataset

This project focused on applying Generative Adversarial Networks (GANs) to synthesize realistic face images using the CelebA dataset. The dataset consisted of 49,736 RGB face images, each resized to 128×128×3. The task was to synthesize new faces by learning a generative distribution using adversarial training. 

[ Face GAN training ]

The GAN architecture consisted of a generator network that learned to map Gaussian noise vectors to synthetic images, and a discriminator that learned to classify real versus fake images using binary cross-entropy loss. Both networks were trained iteratively using the standard adversarial training loop. PyTorch was used for implementation and training on Google Colab with GPU acceleration.

# Image Generation Using Denoising Diffusion Probabilistic Models

In this project, I implemented a Denoising Diffusion Probabilistic Model (DDPM) to generate synthetic images of the digit "1" from the MNIST dataset. DDPMs operate by progressively adding Gaussian noise to images during a forward diffusion process and then learning to reverse this process to generate realistic data. A UNet-based architecture was trained to model this reverse trajectory by predicting the noise component at each step.


**References**

# Modeling PDE Dynamics with Transformer Architectures

# Self-Supervised Visual Representation Learning with SimCLR on CIFAR-10
