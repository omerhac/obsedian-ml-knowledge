# Attention
* good article link - https://lilianweng.github.io/lil-log/2018/06/24/attention-attention.html#self-attention
* paper - https://arxiv.org/pdf/1409.0473.pdf

Attention in a broad way is a way to tell the network which context vectors we should concider at each timestep (we shouldnt use only the last one). This is done by assigning weights to each context vector by similarity to the current decoder state.
![](%D7%A6%D7%99%D7%9C%D7%95%D7%9D%20%D7%9E%D7%A1%D7%9A%202020-10-09%20%D7%91-18.20.49.png)

1) There are several mechanisms to compute the attention weights:
	1) cosine similarity between encoder and decoder hidden states
	2) learnt weights to assign a score for encoder and decoder hidden states
	
	
2) There are two main modes for attention:
	1) global attention: Looking at all of the input at once - can be costly..
	2) local attention: predicting a pointer to which place we should look and only look at that place and a predefined window

3) $C_t$ is the current weighted context vectors and $a_x$ are attention weights:
	
$$ C_t = \sum_{i=1}^t a_t h_t $$

* Where:
$$ a_t = \frac {exp(score(h_t, s_{t-1}))} {\sum_{i=1}^t exp(score(h_i,s_{-1}))} $$

* Where:
$$ score(h,s) = cosine(h, s) / tanh(h^TWs) / ... $$


** Therefore, if input node $x_i$ is of high importance to decode node $y_j$, the assigned weight $a_ij$ will have high value

[Natural Language Processing](Natural%20Language%20Processing)