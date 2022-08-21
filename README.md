# 3D shape inspection and detection with Efficient Modelling

<img src='https://miro.medium.com/max/800/0*AEfESZXdQ6hYJgqt.gif' width=70%>

Photo credit: [Aleksei Vasileika](https://dribbble.com/shots/9533255-Endless-geometric-animation) on [Dribble](https://dribbble.com/)

# Abstract:

This project involved the idea of building a system/pipeline that detects four types of 3D shapes — Cube, Cylinder, Spheroid and Sphere in an image, and repository contains code files for preparing the base-line for Transfer Learning. MobileNet (V1) is taken into consideration as the baseline for the Network. **Reason for using MobileNet**: Since MobileNet provides a light weight infrastructure, and at the same time due to its streamlined architecture makes more parameters customizable and easy to host (if interested) on light wieight MCUs.

## Mobilenet v1 — Base Model:
MobileNets are based on a streamlined architecture that uses depth-wise separable convolutions to build light weight deep neural networks. The purpose behind using mobilenet for this use case is that, this project is intended to be deployed on mobile devices on the edge, hence making perfect sense to build a model based on a class of efficient models (MobileNets) that were pre-trained to suite deployment of Fine-Tuned DNN models for mobile and embedded vision applications.

The following model parameters are considered and set as follows:
- `IMAGE_SIZE` = 224 	# Image input size = H x W = 224 x 224
- `ALPHA` = 0.75 	# α = Learning rate
- `EPOCHS` = 20  

# Training dataset:

![](https://github.com/deepmind/3d-shapes/raw/master/3dshapes.gif)

Dataset used here is a custom and refined dataset acquised from [Deepmind's repo](https://github.com/deepmind/3d-shapes), which was initially used in [Kim, Hyunjik and Mnih, Andriy. "Disentangling by Factorising." *In Proceedings of the 35th International Conference on Machine Learning (ICML). 2018.*](http://proceedings.mlr.press/v80/kim18b.html), to assess the ***disentanglement*** properties of unsupervised learning methods.

## Description:

<img src='https://github.com/kulendu/3D_shape_latents/blob/master/images/3d_shapes.png' width=50%>

The Dataset contains four types of 3D shapes: ***Cube, Cylinder, Spheroid,*** and ***Sphere***.

|![](https://github.com/kulendu/3D_shape_latents/blob/master/images/cube.gif)| ![](https://github.com/kulendu/3D_shape_latents/blob/master/images/cylinder.gif)|![](https://github.com/kulendu/3D_shape_latents/blob/master/images/shpreoid.gif)|![](https://github.com/kulendu/3D_shape_latents/blob/master/images/sphere.gif)|
|:----:|:--------:|:--------:|:------:|
| Cube | Cylinder | Spheroid | Sphere |



These 3D shapes are generated 6 ground truth latent factors. These factors are ***floor colour, wall colour, object colour, scale, shape*** and ***orientation***. All of them are customizable and can be plotted acording to thier respective defined value-bounds.
### Latent factor values:
- **floor hue**: 10 values linearly spaced in [0, 1]
- **wall hue**: 10 values linearly spaced in [0, 1]
- **object hue**: 10 values linearly spaced in [0, 1]
- **scale**: 8 values linearly spaced in [0, 1]
- **shape**: 4 values in [0, 1, 2, 3]
- **orientation**: 15 values linearly spaced in [-30, 30]

### Dataset configuration:
The dataset is stored in a `HDF5` file, with the following fields/parameters:
- `images`: (480000 x 64 x 64 x 3, uint8) RGB images.
- `labels`: (480000 x 6, float64) Values of the latent factors.

### Downloading the dataset from Google Cloud Storage:
The dataset can be downloaded from [here](https://console.cloud.google.com/storage/browser/3d-shapes;tab=objects?pli=1&prefix=&forceOnObjectsSortingFiltering=false)
