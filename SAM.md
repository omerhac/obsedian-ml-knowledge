# Sharpness Aware Minimizer, SAM
* link to paper - https://arxiv.org/pdf/2010.01412.pdf

This optimizers tries to find weights that lies in a neighborhood that has uniformally low training loss rather then finding weights that only themselves have low training loss.
This theoretically and emprically leads to better generlization.

In order to find these weights, the algorithm computes the standard training loss per batch, then it computes the weights with the highest loss across the neighborhood and then approximates the gradient of L_SAM w.r.t. the weights with both of these values.
Standard SGD is then used to minimize L_SAM.