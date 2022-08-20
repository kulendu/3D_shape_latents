# 3D shape inspection and detection with Efficient Modelling

<img src='https://miro.medium.com/max/800/0*AEfESZXdQ6hYJgqt.gif' width=50%>

Photo credit: [Aleksei Vasileika](https://dribbble.com/shots/9533255-Endless-geometric-animation) on [Dribble](https://dribbble.com/)

# Abstract:

# Training dataset:

![](https://github.com/deepmind/3d-shapes/raw/master/3dshapes.gif)

Dataset used here is a custom and refined dataset acquised from [Deepmind's repo](https://github.com/deepmind/3d-shapes), which was initially used in [Kim, Hyunjik and Mnih, Andriy. "Disentangling by Factorising." *In Proceedings of the 35th International Conference on Machine Learning (ICML). 2018.*](http://proceedings.mlr.press/v80/kim18b.html), to assess the ***disentanglement*** properties of unsupervised learning methods.

## Description:

The Dataset contains four types of 3D shapes: ***Cube, Cylinder, Spheroid,*** and ***Sphere***.

|![](https://github.com/kulendu/3D_shape_latents/blob/master/images/cube.png)| ![](https://github.com/kulendu/3D_shape_latents/blob/master/images/cylinder.png)|![](https://github.com/kulendu/3D_shape_latents/blob/master/images/spheroid.png)|![](https://github.com/kulendu/3D_shape_latents/blob/master/images/sphere.png)|
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
