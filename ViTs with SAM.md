# Vision Transformers Outperform ResnNets without Pretraining or Strong Data Augmentations
* link to paper - https://arxiv.org/pdf/2106.01548.pdf

When training with first order optimizer such as SGD or ADAM and such, Vision Transformers have inferior performance on visual data compared with Convolution style architecture. 
This is thought to be because of the inate bias towards locaion invariance that Convolution possesses.
Fully connected architectures such as Transformers and MLPs don't have that inate property and thus require lots of data or strong augmentations in order to learn it.

This paper propses the use of Sharpness Aware Minimizer for training General perpose neural architectures and shows that they can be as strong on visual data.
It shows that ViTs and MLPs trained with SGD converge to a really sharp minima compared with convolution style architectures. Thus, training  with SAM which finds weights which lie at a neighborhood which overall have low loss, i.e. "Flat Minima", will benefit ViTs more then it benefifts ConvNets.

This finding makes progress towards more general perpuse architecture which do not require hand-wired features.

[[SAM]]

[[Transformer]]