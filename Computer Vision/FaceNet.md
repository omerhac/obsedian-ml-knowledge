# FaceNet - Facial verification and identification
* link to facenet paper - https://arxiv.org/pdf/1503.03832.pdf
- Use CNN to embed facial images as small (128 byte) latent vectors
- Triplet Loss fucntion - a way to avoid softmax over all class labels
	-	$L=\sum (d(a, p) - d(a-n) + \alpha)$
	-	Where a is the anchore face, p is a face that belongs to the same identity as anchor and n is a face that belongs to another identity. d is the eculidean distance
-	The triplets are mined at an online fashion:
	-	for every batch, all positive (same identity) images are used and only the hard / semi-hard negative samples are used for loss computation.
		-	hard negative are such that $d(a, n) < d(a, p)$
		-	semi-hard negative are such that $0 < d(a, n) - d(a, p) < \alpha$
	- One should start the training without hard examplars, for the network not to collapse to the trivial local optima

[Image Processing](Image%20Processing.md)]
[Triplet loss function](Triplet%20loss%20function.md)
