Image Segmentation project:

cluster_image_kmeans and crop_clustering is used for colour clustering and helping the formation of shapes using KMeans and GaussianMixtures respectively

Color_Returner gives the color of the letter as well as the shape using k means. The smallest colour is assumed to be of the letter's. The secons is assumed to be of the shape

colordetection uses Color_Returner and then converts to HLS color space. Based on Euclidean distance, it chooses the colour that is closest to it.

Mask_Returners uses clustering as described in the first line to give masks of letter and shape to the classifiers.

LetterClassifier and ShapeClassifier classifies the masks using XCeption training network and the imagenet dataset weights. The model weights are then stored for future classifications.