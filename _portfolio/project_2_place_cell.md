---
title: "More biological hippocampus model via cascade synapses"
excerpt: "hippocampus model with cascade synapse<br/><img src='/projects/fusi_4.png' width='400' height='400'>"
collection: portfolio
---



**Advisor: Stefano Fusi**

**Centre of Theoretical Neuroscience, Columbia University, U.S.** 

This project is one of the implementations of the synapse model in [https://doi.org/10.1038/nn.4401](https://doi.org/10.1038/nn.4401), which generally provides a solution to aviod the *catastrophic forgetting*. 

The synapse model is called cascade model, the diagram is given below. A classic cascade synapse is made by a number of connected variables. The first variably $u_1$ is the synapse weight, while others are just hidden variables, modelling the cascade of molecular signal. The learning preocess only influence $u_1$, while hidden variables $u_2, u_3,\cdots$ could preserve the old memories.

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi_1.png" alt="Fusi_1" style="zoom: 50%" ></center></p>

As shown in this paper [https://doi.org/10.1073/pnas.2018422118](https://doi.org/10.1073/pnas.2018422118), hippocampus could be viewed as an auto-encoder, and place cells are a natural result of memory compression. However, the synapse here are simple model without memory ability. Here, I implement cascade synapse to improve the model.

Here is the result of memory retrival task in auto-encoder, showing cascade synapse can improve the memory capacity.

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi_2.png" alt="Fusi_2" style="zoom: 50%" ></center></p>
To generate place cells, I use the method in the paper above. Here is the generated place cells with their typical behavior.

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi_4.png" alt="Fusi_4" style="zoom: 30%" ></center></p>

Then test the similar memory retrival test based on placed cell, the result suggesting the cascade model can sufficiently reduce the decoding error.

<p><center><img src="http://qiuyoungwang.github.io/images/projects/fusi_3.png" alt="Fusi_3" style="zoom: 50%" ></center></p>

Above all, we have shown that power of cascade synapse in avoiding the *catastrophic forgetting*. And a more biological hippocampus model could be built with such a synapse model.
