# Regoin oof Interest Pooling
* link to blogpost with implementation - https://medium.com/xplore-ai/implementing-attention-in-tensorflow-keras-using-roi-pooling-992508b6592b

Region of Interest Pooling (RoI) comes to adress the problem of variable shape region proposal encountered at object detetion models.
When we need to feed a dense layer we have to have consistant shape input.

This is done by making the output shape of the RoI constant and splicing the image into a constant number of patches coressponding to the output shape of the layer.
Within each splice we maxpool the pixels.

As shown here, different size patches are pooled to a constant size map:

![](Pasted%20image%2020210111151920.png)

- Implementation trick for bounding box coordinates: use relative coordinates (with respect to the feature map of bbox proposal) in order to not account to the image shape changes during convolution operations.

[Object Detection](Object%20Detection.md)
[Computer Vision](Computer%20Vision.md)

