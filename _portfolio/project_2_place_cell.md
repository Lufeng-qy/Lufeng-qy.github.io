---
title: "More biological hippocampus model via cascade synapses"
excerpt: "Hippocampus model with cascade synapse<br/><img src='/images/projects/fusi_2.png' width='400' height='400'>"
collection: portfolio
---



**Advisor: Stefano Fusi**

**Centre of Theoretical Neuroscience, Columbia University, U.S.** 

This project is one of the implementations of the cascade synapse model in [this paper$^{[1]}$](https://doi.org/10.1038/nn.4401), which generally provides a solution to aviod the *catastrophic forgetting* in neural networks. 

The diagram of the cascade synapse model is shown below$^{[1]}$. It's inspired by the cascade of signal molecules in the process of synaptic plasticity. A classic cascade synapse consists of a number of connected variables. The first variable $u_1$ represnets the synapse weight, while others are hidden variables (which is an abstraction of the chemical reactions in a synapse ). The synapse weight updating rule in the learning process(e.g. Hebb's rule) only influence $u_1$, while the hidden variables $u_2, u_3,\cdots$ can preserve the old memories.

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi/fusi_1.png" alt="Fusi_1" style="zoom: 50%" ></center></p>

As shown in this paper [this paper$^{[2]}$](https://doi.org/10.1073/pnas.2018422118), hippocampus could be viewed as an auto-encoder, and the place cells are a natural result of memory compression. However, the synapse model here is the trivial synapse in neural network, which lacks memory ability. Here, we implemented the cascade model to improve the performance of the hippocampus auto-encoder.

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi/auto_encoder.png" alt="Fusi_4" style="zoom: 30%" ></center></p>

We first do the memory retrieval task with the input being of a set of binary strings generated from ultra-metric tree$^{[2]}$. 

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi/fusi_tree_1.png" alt="Fusi_4" style="zoom: 30%" ></center></p>

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi/fusi_tree2.png" alt="Fusi_4" style="zoom: 30%" ></center></p>

Then we retreive the memory to test its memory capacity. The x-axis is the number of input memories while the y-axis represents the number of correctly retrieved memories. The result is shown below, from which we could see with 

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi/fusi_2.png" alt="Fusi_2" style="zoom: 50%" ></center></p>

To generate place cells, I use the method in the paper above. Here is the generated place cells with their typical behavior.

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi/fusi_4.png" alt="Fusi_4" style="zoom: 30%" ></center></p>

Then test the similar memory retrival test based on placed cell, the result suggesting the cascade model can sufficiently reduce the decoding error.

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi/fusi_3.png" alt="Fusi_3" style="zoom: 50%" ></center></p>

Above all, we have shown that power of cascade synapse in avoiding the *catastrophic forgetting*. And a more biological hippocampus model could be built with such a synapse model.



[1 ]Benna, M., Fusi, S. Computational principles of synaptic memory consolidation. *Nat Neurosci* **19**, 1697–1706 (2016). https://doi.org/10.1038/nn.4401

[2] Benna MK, Fusi S. Place cells may simply be memory cells: Memory compression leads to spatial tuning and history dependence. Proc Natl Acad Sci U S A. 2021 Dec 21;118(51):e2018422118. doi: 10.1073/pnas.2018422118. PMID: 34916282; PMCID: PMC8713479.
