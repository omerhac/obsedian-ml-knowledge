# Sequence to Sequence
## LSTMs for Machine Translation
* link to paper - https://papers.nips.cc/paper/5346-sequence-to-sequence-learning-with-neural-networks.pdf

1) Main architecture consists of two LSTM cell, one acts as an encoder and one as a decoder. This allows us to translate sentence of length x to sentence of length y.
	- Encoder cell takes as input $x^i$ (word embedding) and $h^(i-1)$ (thought vector).
	- Encoder outputs $h^i$ (current thought vector).
	- Decoder cell takes as input $y^(i-1)$ (previous word output) and v (final encoder state (final thought vector))
	- Decoder ouputs log probabilitys of current word which in turn goes threw softmax to produce next token.
		- Beam search is used for selecting the most probable sentence out of a sequence of log probs

2) Its really good to reverse the order of the input sentence so the time lag between correlated words is smaller.
3) More layers of the LSTM really helps reduce preplexity.
4) Paralleliaztion can be done on a layer basis, each forward pass can be calculated seperatly on a different GPU wating only for the previous layer to finish.

[Natural Language Processing](Natural%20Language%20Processing.md)
[LSTM](LSTM.md)