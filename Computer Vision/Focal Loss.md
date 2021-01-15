# Focal Loss
* link to paper - https://arxiv.org/pdf/1708.02002.pdf

Focal loss is a noval loss term which tries to bridge the accuracy gap between two stage cascade object detectors (such as Faster R-CNN) and one stage detectors (such as YOLO).

The observation in the paper is that the problem with training one shot detectors with alot (dense) of candidate object loacation is that the loss term is overwhelmed by the loss from 'easy' examples.

## Easy examples
Easy examples are the ones which the model is correct about the detection result and the predicted probability is high.
When training an object detector, such easy examples normally comes from background candidate object location, which are abundent with respect to foreground examples (with a ratio of about 1:1000).
With this much easy examples a cross-entropy loss term is overwhelmed even if the loss per example is low. And thus, the model can't learn from the 'hard' examples which provide usefull gradients.

Two stage detectors usually adress this problem with heuristics such as Online Hard Examples Mining and RPN's which provide much less ROI proposals.

Focal loss addresses the issue by assigning less loss to an 'easy' example (which the model is sure about) and thus lowering the effect of them on the loss term.

Regular cross entropy loss is defined as follows:
![](Pasted%20image%2020210113184516.png)

Where:
![](Pasted%20image%2020210113184532.png)

Focal loss adds a regularizing term $(1-p_t)^\gamma$ such as:
![](Pasted%20image%2020210113184718.png)

And thus we can see that when the model is sure, $(1-p_t)^\gamma$  is low, and the loss term is low. When the model is unsure, or its wrong about its prediction, $(1-p_t)^\gamma$  is high and the loss term is identical to cross-entropy loss.

## RetinaNet
The paper shows by a simple one shot network architecture that a fully convolutional network which is trained with Focal Loss can achive SOTA performance on the object detection task.
I wont go into the details of the architecture but I'll just say that for such model to work it is essential to use [Feature Pyramids](Feature%20Pyramids.md) More on that in the paper.

[Object Detection](Object%20Detection.md)