# CLIP
* link to blogpost with implementation - https://openai.com/blog/clip/
* link to paper - https://cdn.openai.com/papers/Learning_Transferable_Visual_Models_From_Natural_Language_Supervision.pdf

CLIP is a model that allows zero-shot learning on a wide variety of computer vision tasks.
It does so by learning visual representations from textual supervision.

Essentialy, CLIP tries to predict which sentence out of N sentences is most appropriate to descrbie a certian image.
CLIP trains on ver large widely and publicly available dataset of images and captions from the internet.

Its architecture is a combination of a visual model (ResNet or similar, Visual Transformer) and a natural language processing model such as the Transformer: 
![](Pasted%20image%2020210111182817.png)

CLIP dataset containts pairs of (image, caption). Given N pairs, Clip tries to predict which of the NxN pairs actually occured.
It does so by computing cosine similarity between the vectors of each image and each text.

After training, CLIP can be used for zero-shot classification by constracting a small text dataset containing all the labels in the dataset by:
- dataset:
	- an image of a dog
	- an image of a cat
	- ....
	- an image of X

And then trying to predict which of the sentences fits the most.

![](Pasted%20image%2020210111184333.png)

[Computer Vision](Computer%20Vision.md)
[Transformer](Transformer.md)