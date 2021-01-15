# Mean Average Precision - mAP
* link to blog post - https://jonathan-hui.medium.com/map-mean-average-precision-for-object-detection-45c121a31173

This is a metric primeraly used for Object Recontion models.

The general definition of Average Precision is the area under the Precision-Recall graph. As is: 
![](Pasted%20image%2020210111141520.png)

For Object Detection model, a TP is defined by an object detection with IoU larger then a cetain value (usually 0.5) with the ground trouth object.

This is usually softened  to disable noise by two methods:
1) Taking the maxium of precision values of higher recall values per recall value, as:
![](Pasted%20image%2020210111141747.png)

2) Using interpolated AP - taking the avarage precsion values at n recall points.


This is combined to create mean Average Precesion as in COCO-dataset.
It is done by computing the AP value with the 1st softening method for a range of IoU threshold. That is the mAP@[0.5:0.95:0.05] is the mean AP computed for each TP threshold in the range 0.5 to 0.95 with step size of 0.05.

[Object Detection](Object%20Detection.md)