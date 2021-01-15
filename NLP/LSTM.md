# Long Short Term Memory Cell
* link to paper - https://www.researchgate.net/publication/13853244_Long_Short-term_Memory
* link to article - https://colah.github.io/posts/2015-08-Understanding-LSTMs/ -REALLY GOOD
1) LSTM comes to solve the problem of explodeing / vanishing gradients over RNN and solve long term information dependecy in the input.
2) Cell structure:
![](%D7%A6%D7%99%D7%9C%D7%95%D7%9D%20%D7%9E%D7%A1%D7%9A%202020-10-09%20%D7%91-18.05.40.png)

3) It does so by enabeling the cell to pass infromation without modifcation if needed.
4) Cell components:
	1) Cell state($C_t$ ): state vector which is conveyed across cells
	2) Forget gate ($f_t$): sigmoid activated gate to tell which information of the cell state we should forget
	3) Input gate ($i_t$): sigmoid activated gate to tell which information from the input we should move to the cell state.
		- The input is concatinated with the previous cell state and then passed threw a learned layer in oreder to extract meaningfull information.
	4) Output gate ($o_t$): sigmoid activated gate to tell which information ffrom the cell state we should output.
	
	[Natural Language Processing](Natural%20Language%20Processing)