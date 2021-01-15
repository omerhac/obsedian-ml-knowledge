# Faster R-CNN Object Recognition
* link to paper - https://arxiv.org/pdf/1506.01497.pdf

- Object detection going towards real-time inference. (5FPS)
- This architecture uses a Region Proposal Network (RPN) that uses shared image features with the classifier, thus drastically reducing running time while maintaining accuracy. 
- The main change from Fast R-CNN is the RPN. The classifier is actually a Fast R-CNN ontop a [Region of Interest Pooling](Region%20of%20Interest%20Pooling.md) .

General architecture:
![](Pasted%20image%2020210111131854.png)

## Region Proposal Network
The idea here is to run the expenssive feature extractor only once (and not once per bbox size/ratio) and reduce time spent on classical region proposal schemes.
Both on running time and number of proposals.

Arbiterery sized images are processed threw a pre-trained network (ZF or VGG-16) for computing image features.
Then a sliding window of size 3x3 (A Covolutional layer) is pased over the features so every patch of 3x3 can be assigned Bounding Box coordinates (Xcenter, Ycenter, width, height) and objectness score.
This is done via 2 separate dense layers (one for score and one for coordinates, actually implemented by 1x1x256 Conv layer).
This process is done simultaneously for 9 BBox "Anochors" (of re-defined size and aspect ration) so every score and coordinates are relative to one of the anchors.
This produces (4 coordinates + 2 scores) x 9 anchors outputs per patch of 3x3 features.
This actually means that there are 9 classifiers for proposing BBoxes for each type of anchor. These classifiers do not share their weights. 
This also Creates translation inviance because the dense layers weights are shared between patches. 

The network is trained via a combined loss on every bbox proposal on the objectness (1/0 per bbox) and the regression loss over BBox coordinates:
![](Pasted%20image%2020210111133351.png)

Where pi is the predicted probability of the bbox containing an object and ti is the vector containing bbox coordinates.  pi* and ti* stands for the ground truth.
Lcls is log loss and Lreg is robust loss. Other stuff is just Hyperparameters.


## Training
This architecture also uses shared weights between the RPN and classifier so the training can be done in two main ways:
1) Alternated training- training each network while the other is held constant and using its predictions and then switching.
2) Joint model training - online RPN infrence and using the proposed regions as input to the classifier. The gradient is propogated threw both networks.

The metric used id [Mean Average Precision](Mean%20Average%20Precision.md).

[Object Detection](Object%20Detection.md)