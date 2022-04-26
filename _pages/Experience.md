---
permalink: /Experience/
title: "Projects"
author_profile: true
redirect_from: 
  - /md/
  - /markdown.html
---



---



## Coarse-Grained method for Integral-and-Fire network and Spatially Ordered Network

**Advisor: Jiwei Zhang**

**School of Mathematics and Statistics, Wuhan University, China**

Integral-and-Fire(IF) neural network is a more biological neural network compared with the artificial neural network (ANN), since it generates spike trains. However, it's really expansive to evolve this network because of the *curse of the dimensionality*. In ANN, the computation is quite fast, since the activation function is simple and the derivation is somehow trivial. In IF network, however, we have to solve the ODE below for each time step.

(the 2nd term in the right hand side repersents the total external input, both from the background noise and other inputs from presynaptic neurons)

$$\frac{dV_i^Q}{dt} = -g_i(V_i^Q-V_L) + \sum_j\sum_k S^{QY}\delta(t - t_{jk}) $$

But in fact, what we really care is not the spikes or voltage, but the firing rate $m(t)$. And to get the firing rate, we need to  know the probility distribution function(PDF) of voltage and its PDE. Here we demonstrate the idea by taking a simple all-to-all connected IF network for example.

First, write down the master equation governing the evolution of PDF $\rho(v,t)$

$$\partial_t \rho^Q(v,t)=g_L\partial_v[(v-V_L)\rho^Q(v,t)]+\eta^Q[\rho^Q(v-S^{QY},t)-\rho^Q(v,t)]$$

To make it more clear, we transform this equation into the Fokker-Planck equation:

$$\partial_t \rho^Q(v,t)+g_L\partial_vJ^Q(\rho^Q(v,t))=0$$

Using boundary conditions, the firing rate $m^Q(t)$ could be written as:

$$m^Q(v,t)=g_LJ^Q(\rho^Q(v,t)) = -\frac{g_L\sigma^2}{2}\partial_v \rho^Q(V_T, t)$$

Then, we problwm becomes how to solve this PDE. We transform the PDE into a series of ODEs by introducing moments. Define the moments as usual:

$$M^Q_j(t)=\int^{V_T}_{-\infty}v^j\rho^Q(v,t)dv$$

Then, the higher order moment could be calculated via lower order moments:

$$\frac{dM^Q_j(t)}{dt}=-m^Q(t)V_T^j-jg_L[M^Q_j-\mu^QM^Q_{j-1}-\frac{j-1}{2}(\sigma^Q)^2M^Q_{j-2}]$$

However, to evolve such an ODEs system with given initial conditions $M(t_0),m(t_0)$, we need to compute $m(t)$ at each time step, which still inquires computing $\rho(v,t)$. 

Instead of computing $\rho(v,t)$ directly (which needs solving PDE), we use the maximum entropy method by approximating the PDF $\rho(v,t)$ with the equilibruim solution $\rho_{eq}$

$$\rho_{eq}^Q=C\exp(-\frac{(v-\mu^Q)^2}{(\sigma^Q)^2})\int^{(V_T-\mu^Q)/\sigma^Q}_{(v-\mu^Q)/\sigma^Q}e^{s^2}ds$$

$$\rho_{me}(v)=\rho_{eq}(v)\exp(\sum_{j=0}^N\lambda_jv^j-1)$$

Above all, we could get the firing rate of a IF network by simply dealing with the ODEs system. This method is both fast and accurate. With more moments introduced, the result becomes more accurate. 

<p><center><img src="http://qiuyoungwang.github.io/images/projects/Jiwei_1.png" alt="Jiwei_1" style="zoom: 50%" ></center></p>

I also built a spatially ordered IF network with for further analysis.

(This method can be generalized to spatially ordered IF network, which can be used in V1 simulation, but we have to do some modifications)



## More biological hippocampus model via cascade synapses

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



## CaMKII Pathway Model for LTP (Part of the Bachelor Degree Thesis)  

**Advisor: Shengli Chen**

**College of Chemistry and Molecular Sciences, Wuhan University, China**

Spike Timing Dependent Plasticity (STDP) is believed to be a general rule in human learning. Basically, *neurons fire together, wire together*. The change of the synaptic weight is related to the time interval between pre and post synaptic spikes. However, it remains unclear how neurons can generate such a behavior. And important molecular in such a physiological process is CaMKII, which is generall considered as bistable switch molecular in LTP. Here the CaMKII pathway is shown below. 

Note that CaMKII can phosphorylate itself. So when the concentration is high, it could be quickly activated. (To simplify our system, we assume that when $[CaMKII]$ go beyond a threshold, the self-phosphorylation starts)

<p><center><img src="http://qiuyoungwang.github.io/images/projects/shengli_1.png" alt="shengli_1" style="zoom: 30%" ></center></p>

And we model the interaction (or chemical reaction) of different molecular with the kinetic equations since most of them are enzyme catalysis:

$$V_0 = V_{max}\frac{[S]}{K_M + [S]}$$

Or more specifically, take the interaction between PKA and cAMP as an example:

$$\frac{d[PKA]}{dt} = k_{phos}[cAMP]^4\frac{[PKA]_0-[PKA]}{K_{f} +[PKA]_0-[PKA] } - k_{deph}[PKA]\frac{[PKA]}{K_{b}+[PKA]}$$

We could see that CaMKII act as an molecular switch in such an network. When input is low, the CaMKII will remain at a low state, while when the input is high, CaMKII phosphorylate itself when the concentration is high, thus remain at a high state

<p><center><img src="http://qiuyoungwang.github.io/images/projects/shengli_2.png" alt="shengli_2" style="zoom: 30%" ></center></p>

Yet CaMKII here is not strictly bistable, since the concentration of activated CaMKII could be of various of values, the ability of phosphorylate itself could result in bistable behavior in the downstream reaction. And example is CREB, which could lead to LTP when activated. CREB could be a downstream molecular in CaMKII pathway, which can be bistable as a result.

<p><center><img src="http://qiuyoungwang.github.io/images/projects/shengli_3.png" alt="shengli_3" style="zoom: 30%" ></center></p>

Above all, we modeled the CaMKII pathway, and showed that CaMKII could be a molecular switch in LTP. 

## Anti-bactrier materials

**Advisor: Xianzheng Zhang        **

**College of Chemistry and Molecular Sciences**

Well, this project is about chemistry and materials (literally *cooking*). So I'll talk about them later...but you can check my publication...

