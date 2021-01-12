# Fully Convolutional Instance Segmentation (FCIS)
* link to paper - https://arxiv.org/pdf/1611.07709.pdf

Instance segmentation using a fully convolutional network. Combining segmentation and classification into an end-to-end solution.

This paper comes to solve the various problems of models with dense layers:
1) It is cotsly to run the per-ROI computation at the end of the network.
2) RoI pooling is distorting and losing details of the feature maps
3) A lot of parameters at the final dense layers

The general architecture of the model is as follows:
- Fully convolutional feature extractor (ResNet and such)
- Fully convoultional RPN as in [Faster R-CNN](Faster%20R-CNN.md) for region proposals
- A segmenting and classifying head that produces two score maps per ROI per class (i,e, 2x|ROI|x|classes|) inside and outside. Described bellow.
- The two score maps are then used to provide the segmentation mask and classification label.

![](Pasted%20image%2020210112210642.png)

## Score maps
The score maps are produced as follows:
- Each ROI is devided into a KxK regions (K is a free parameter), each representing a relative position with respect to the ROI.
- Then $K^2$ convolutional 'minimaps' are produced from the feature  map by a 1x1 convolution. Each $minimap_i , i\in{(1..k^2)}$ represents the question: "Is this pixel is inside/outside an object in the ROI **AND** in the relative position with respect to the ROI (and thus with respect to the object centerd at the ROI)". As is, each minimap only propogate the gradients of the parts of the object which fits is inside its kth partition (the minimap is actuatlly computer over the whole ROI then cropped).
- All the minimaps are asssembled into the score map by cropping the kth partion which correspond to each minimap and putting them together to from a full score map with the shape of the ROI. The other parts of each minimap are discarded and thus do not contribute to the gradient.

## Inferring from the score maps
Segmenting and classifying objects from the score maps is a rather quick and straight forward.
- Segmentaion:
	- Conduct per-pixel softmax (between the inside and outside score maps of each class)
	- Use mask voiting from the mask probabilities
- Classification:
	- Conduct per-pixal max (between the inside and outside score maps of each class) the obtain the likelihood of that pixel being part of an ROI that contains an object of the disired class
	- Perfrom avarage pooling of each class map
	- Use softmax to obtain class probabilities

This process is quiet fast and thus can be done for a lot of ROI with relatively low cost.

[Computer Vision](Computer%20Vision.md)