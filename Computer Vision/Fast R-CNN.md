# Fast R-CNN
* link to paper - https://arxiv.org/pdf/1504.08083.pdf

Fast R-CNN aims to improve inferencing time by sharing image features between regions forward pass.
It does not run the network for each region proposal as in R-CNN.

It introduced [Region of Interest Pooling](Region%20of%20Interest%20Pooling.md) for the variable shape of regions.

Region proposals are made by another alogorithm.
The inference per region is made by a single pass of the netowork and allows for proper gradient flow backward.

The architecture is made by taking a pre trained net (ex. VGG16) and replacing the last maxpooling layer by a RoI layer to fit the next dense layer.
The last dense classisfication layer is replaced by to dense layers. One for predicting class confidense and one for predicting 4 BBox coordinates (Xcenter, Ycenter, width, height)

Architecture:
![](Pasted%20image%2020210111161442.png)

The loss is multitask loss for class probabilities and bounding box regression:
![](Pasted%20image%2020210111161655.png)

[Computer Vision](Computer%20Vision.md)