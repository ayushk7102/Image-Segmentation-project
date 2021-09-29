# Image-Segmentation-project
This repository is meant for a drone flying 200 ft above ground and taking pictures of letters and shapes in the ground. It is part of the codebase for AUVSI SUAS competition.
The objective is to identify the letter, the shape and the colour of the letter and the shape in the image.
![Example Image] (https://github.com/NeetigyaPod/Image-Segmentation-project/blob/main/circle_A_8.jpg)

An image of a letter contained inside a shape is given as as input. The following algorithm segments out the letter as well as the shape using modified KMeans that clusters on HLS colour space along with X-Y coordinated to take proximity into consideration as well. The segmentation results are in Mask_Returners.ipynb for you to look at. These masks are then given to the classifiers to identify. The colour segmented image is given to the colour-detection module that uses euclidean distance in HLS colour space to identify the colour.

Read more about the objective in the following pdf (Please refer to the odcl part for more info):
https://static1.squarespace.com/static/5d554e14aaa5e300011a4844/t/6130b8f8fce9880009500f1b/1630583032891/auvsi_suas-2022-rules.pdf


Image Segmentation project:

cluster_image_kmeans and crop_clustering is used for colour clustering and helping the formation of shapes using KMeans and GaussianMixtures respectively

Color_Returner gives the color of the letter as well as the shape using k means. The smallest colour is assumed to be of the letter's. The secons is assumed to be of the shape

colordetection uses Color_Returner and then converts to HLS color space. Based on Euclidean distance, it chooses the colour that is closest to it.

Mask_Returners uses clustering as described in the first line to give masks of letter and shape to the classifiers.

LetterClassifier and ShapeClassifier classifies the masks using XCeption training network and the imagenet dataset weights. The model weights are then stored for future classifications.
