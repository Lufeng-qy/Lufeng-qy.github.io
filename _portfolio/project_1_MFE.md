---
title: "Coarse-Grained method for Integral-and-Fire network and Spatially Ordered Network"
excerpt: "PDEs in IF neural network 
Advisor:Jiwei Zhang.  School of Math and Statistics, Wuhan University
<br/><img src="http://qiuyoungwang.github.io/images/projects/Jiwei_1.png">"
collection: portfolio
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