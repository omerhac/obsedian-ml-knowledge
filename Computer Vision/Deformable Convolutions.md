# Deformable Convolutions
* link to paper - https://arxiv.org/pdf/1703.06211.pdf

Deformable convolutions adress the problem of the fixed field of view of standard convolutions.
It does so by learning offsets for the convolutional kernels by back propogation end-to-end and thus acquiring "smart dynamic" convolutional kernel.

The standard convolution kernel is computed as follows:
![](Pasted%20image%2020210112171229.png)

Where $p_0$ is the location on the output feature map, $p_n$ is the kernel locations and X is the input feature map.

Deformable convolutions works by adding a learned offset to the convolution kernel.
The offset is different per image and per image location. It is constant among the channel dimension.

The offset $\Delta p$ is added to the kernel sampling as follows:
![](Pasted%20image%2020210112171836.png)

Because the offset is typically fractional, the kernel actually uses bilinear interpolation as described in the paper.

The offset is inferred by applying a convolutional filter to the input feature map.:
![](Pasted%20image%2020210112172235.png)

Each offset from $|kernel|$ has its own feature map.
Thus, each offset is dynamic with respect to the input feature map contant.
This way the offset can be learned "deeply" end to end.

The aqcired offsets are able to 'attend' to various object shapes and sizes:
![](Pasted%20image%2020210112172450.png)

There is also a deformable RoI layer described in the paper, the general idea is the same and I wont go into the details here.

[Computer Vision](Computer%20Vision.md)