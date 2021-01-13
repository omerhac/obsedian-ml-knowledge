# Feature Pyramids
* link to paper - https://arxiv.org/pdf/1612.03144.pdf

Feature Pyramids comes to solve the problem of using only the final layer of a ConvNet which has strong semantic features but low resolution and often wrong object localitzation due to the translation invariance property of convolutions.

It is known, that low layers of a ConvNet have high resolution and better feature positions (fewer sampling and downsampling) but has weaker semantic features.
High layers of ConvNets have good semantic features but low resolution.

So, if we only use the last convolutional layer, we lose alot of details.
Earlyer approaches used featurized image pyramids, which is scaling the input image multiple times and then running the model over each scale of the image.
This is time and resource expansive.

![](Pasted%20image%2020210113193642.png)

Feature Pyramids tries to do the samce without these expenses.
It does so by building strong higher resolution semantic features.
General architecture is:

![](Pasted%20image%2020210113193706.png)

## Feature Pyramid building process
Building the pyramids is as follows:
- The last layer of each block of the ConvNet (before the downsampling) is used and called $C_i$ for block $i$
- From each $C_i$ we build a $P_i$ which is a pyramid feature map 
- For example lets assume we have $C_1, C_2, C_3$ and $P_1, P_2, P3$
- To construct $C_1, C_2, C_3$ we simply need a forward pass of the ConvNet
- To construct $P_1, P_2, P3$ we do three operations:
	1) Firstly, we upsample the last pyramid ($P_i$) feature map. For the top one ($P_3$) we upsample the last C map ($C_3$) by using nearest nighbours upsampling
	2) Secondly we perfrom 1x1 convolution on C map with the same resolution (for filter number correspondance) and add it
	3) Finally, we perform 3x3 convolution n the resulting map.
- The whole operation is:
	![](Pasted%20image%2020210113194642.png)
	
Producing these maps is cheap with respect to computation and memory.
	
	
## Inferring on the downstream task
After we built the strong Feature Pyramid maps, inferring is fast and straight forward.
We run the head of the network on each of the feature pyramid maps, with shared weights between maps (because feature semantics are the same within each map).
This operation is typiclly pretty cheap and fast.

It is shown in the paper that both the bottom up and the lateral connections are important. Also, using all feature maps is important.

[Computer Vision](Computer%20Vision.md)