---
title: "Deep Learning Projects"
excerpt: "24-788 and 24-789 course exercises, Carnegie Mellon University <br/><img src='/images/ACSI_project/coverimage_500x250.jpg'>"
collection: portfolio
---

The various deep learning works seen here are part of the Introduction to Deep Learning and Intermediate Deep Learning coursework at Carnegie Mellon University.

**Airfoil Self-Noise Prediction Using a Multi-Layer Perceptron**

[AIRFOIL FIGURE]

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

***References***
Thomas F. Brooks, D. Stuart Pope, and Michael A. Marcolini. Airfoil self-noise and prediction. NTRS Author Affiliations: PRC Kentron, Inc., Hampton, NASA Langley Research Center NTRS Report/Patent Number: L16528 NTRS Document ID: 19890016302 NTRS Research Center: Legacy CDMS (CDMS). July 1989. Url: https://ntrs.nasa.gov/citations/19890016302 (visited on 01/24/2023).

RobertoLopez.Airfoil Self-Noise Data Set.Mar.2014.url:https://archive.ics.uci.edu/ml/datasets/airfoil+self-noise.




**CIFAR-10 Image Classification Using a Convolutional Neural Network**

In this project, I implemented a Convolutional Neural Network (CNN) to perform image classification on the CIFAR-10 dataset, which consists of 60,000 32×32 color images across 10 object categories. The goal was to train a model that generalizes well to unseen data while avoiding overfitting, using PyTorch as the primary framework. 

<img src='/images/ACSI_project/Dual_CF_wTruss.png' alt="Dual_CF_wTruss" class="center">
<p style="text-align:center"> <i>SolidWorks Assembly of the Dual-Drone System. Note the cross shape of the truss allowing for an unobstructed view for the Flowdecks on the underside</i></p>

**LSTM Modeling of Transient Hagen–Poiseuille Flow**


**Airfoil Shape Generation Using Variational Autoencoders and GANs**

This project focused on generative modeling of airfoil geometries using Variational Autoencoders (VAEs) and Generative Adversarial Networks (GANs). The input dataset consisted of 1,600 airfoil shapes from the UIUC Airfoil Database, preprocessed by interpolating to a shared x-coordinate grid and scaling y-coordinates to the range [−1, 1]. The generative models were trained to learn the underlying distribution of airfoil shapes using only the y-coordinates as input.

**Face Image Generation Using GAN on CelebA Dataset**

This project focused on applying Generative Adversarial Networks (GANs) to synthesize realistic face images using the CelebA dataset. The dataset consisted of 49,736 RGB face images, each resized to 128×128×3. The task was to synthesize new faces by learning a generative distribution using adversarial training. 

[ Face GAN training ]

The GAN architecture consisted of a generator network that learned to map Gaussian noise vectors to synthetic images, and a discriminator that learned to classify real versus fake images using binary cross-entropy loss. Both networks were trained iteratively using the standard adversarial training loop. PyTorch was used for implementation and training on Google Colab with GPU acceleration.

**Image Generation Using Denoising Diffusion Probabilistic Models**

In this project, I implemented a Denoising Diffusion Probabilistic Model (DDPM) to generate synthetic images of the digit "1" from the MNIST dataset. DDPMs operate by progressively adding Gaussian noise to images during a forward diffusion process and then learning to reverse this process to generate realistic data. A UNet-based architecture was trained to model this reverse trajectory by predicting the noise component at each step.


**References**

**Modeling PDE Dynamics with Transformer Architectures**

**Self-Supervised Visual Representation Learning with SimCLR on CIFAR-10**
