---
title: "CaMKII Pathway Model for LTP (Part of the Bachelor Degree Thesis)"
excerpt: "Simple model for mechanism of STDP<br/><img src='/images/projects/shengli_1.png' width='400' height='400'>"
collection: portfolio
---



**Advisor: Shengli Chen, Jiwei Zhang**

**College of Chemistry and Molecular Sciences, Wuhan University, China**

### Actually this is a trivial work and I'm not satisfied with my bachelor thesis, so I decide not to post the thesis here...

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
