# EfficiantNets: Model Scaling for ConvNets
* link to paper - https://arxiv.org/pdf/1905.11946.pdf

This paper proposes scaling ConvNets with a constant ratio across width, depth and resolution as apposed to scaling in only one of these dimensions arbitrarily.
Depth: number of layers
Width: number of channel
Resolution: input resulution (224x224, 500x500 for example)

![[Pasted image 20210609140856.png]]

Model FLOPS acts linearly on model depth and cubic on model width and resolution.

In this paper, the authors chose to each time scale a base model with constant ratio on each dimension, so that:
![[Pasted image 20210609141024.png]]

This ensures that when choosing a scaling parameter p, model FLOPS will increase by $2^p$

To find the right constants, the paper proposes using greed search on the baseling model which is not expensive to compute and then scaling by the found constants.

This method achives much more parameter and FLOPS efficiant models, with up to 10x decrease in FLOPS and 8x decrease in parameters when compared to manually scaled models.

[[Computer Vision]]