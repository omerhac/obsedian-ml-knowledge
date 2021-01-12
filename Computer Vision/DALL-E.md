# DALL-E
* link to blogpost - https://openai.com/blog/dall-e/

DALL-E is an image generating model which takes a text sequence as input and an optional image. 
It produces images of amazing quality of the provided text.

It is trained on the theoritically infinte dataset of the internet (caption -> image)

Each input is tokenized and fed to the model. The model is a Transformer style decoder, thus using self attention and predicting each output token (pixel) based on all the ones before it.

Its absoloutly beautiful.

![](Pasted%20image%2020210111194102.png)

[Computer Vision](Computer%20Vision.md)
[Transformer](Transformer.md)