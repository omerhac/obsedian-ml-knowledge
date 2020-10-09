# Attention
* good article link - https://lilianweng.github.io/lil-log/2018/06/24/attention-attention.html#self-attention
* paper - https://arxiv.org/pdf/1409.0473.pdf

Attention in a broad way is a way to tell the network which context vectors we should concider at each timestep (we shouldnt use only the last one). This is done by assigning learned weights to each context vector by similarity to the current decoder state.
![](%D7%A6%D7%99%D7%9C%D7%95%D7%9D%20%D7%9E%D7%A1%D7%9A%202020-10-09%20%D7%91-18.20.49.png)

1) There are several mechanisms to compute the attention weights:
	1) cosine similarity between encoder and decoder hidden states
	2) learnd weights to assign a score for encoder and decoder hidden states
	
	
2) There are two main modes for attention:
	1) global attention: Looking at all of the input at once - can be costly..
	2) local attention: predicting a pointer to which place we should look and only look at that place and a predefined window
	3