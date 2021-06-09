# Vision Transformers
* link to paper - https://arxiv.org/pdf/2010.11929.pdf

Transformers applied to visual data.
The authors apply transformers with minimal changes to visual data.
They do it by unrolling the image into a sequence of patches.

An image of HxWxC is unrolled into N patches of PxPxC pixels where $N=HW/P^2$.
Each patch is then embedded with a linear map into D dimesions, summed with positional embedding and then fed into the model as part of a sequence.

## Model performance
As expected, the transformers have inferior performance on visual data when trained on small datasets. This is because they lack the inherit inductive bias of CNN towards visual data such as locality and translation equivariance.
Thus, empirically CNN models outperform ViTs when the training data is small.
But.. When the training data gets really large, ViTs have comperable and even suprior performence compared to CNNs with lower computation demands.

![[Pasted image 20210609232012.png]]

[[Computer Vision]]
[[Transformer]]
[[ViTs with SAM]]