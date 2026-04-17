# SSM‑ABCD: State Space Model with an Add-on for Boosting Classic Drives

## Background

Since around 2021, research and development on State Space Models (SSMs) has accelerated rapidly.  
However, most existing work focuses on improving the input matrix and state transition dynamics, while the output matrix and direct term have received very little attention.  
In fact, the direct term is not even implemented in widely used SSM variants such as S4 and Mamba.  
This imbalance suggests that the output mechanism of SSMs remains underexplored, motivating us to focus specifically on improving the output matrix and the direct term.

## Problem Statement

Traditionally, SSMs use a single output matrix "C" to read information from the hidden state.  
However, it is unclear whether a single projection can adequately extract the rich information encoded in modern SSM states.  
In classical control systems, each dimension of the state has a clear physical meaning.  
In contrast, the hidden state of machine‑learning‑oriented DSSMs is constructed using HiPPO matrices and contains extremely high information density.  
Relying on a single projection matrix inevitably discards most of this information, creating a structural bottleneck in the output stage.

## Proposed Approach

We introduce three improvements to address the limitations of the traditional SSM output mechanism.

### 1.Multi‑C: Multiple output projections instead of a single matrix  
Rather than using a single output matrix \(C\), we replace it with a tensor containing multiple projection matrices.  
Each matrix provides a different view of the hidden state, allowing the model to extract information that a single projection would inevitably miss.  
This reduces information loss and alleviates the bottleneck caused by the high‑density hidden state.

### 2.Multi‑D: Direct terms that incorporate multiple recent inputs  
The traditional direct term \(D\) only uses the most recent input, which is often insufficient for modeling short‑term dependencies.  
We extend this by introducing a tensor of direct‑term matrices, each corresponding to a different recent input.  
By leveraging multiple recent inputs, the model becomes more expressive and robust in capturing short‑term patterns.

### 3.Weighted fusion of all output candidates  
Finally, the model’s output is computed as a weighted sum of all candidate vectors produced by Multi‑C and Multi‑D.  
This weighted fusion allows the model to adjust the contribution of each projection dynamically, including the option to suppress unnecessary components.  
It also unifies the multiple candidate vectors into a single coherent output.

In short, SSM‑ABCD strengthens the entire output pathway—both the readout matrix \(C\) and the direct term \(D\)—so that the model can properly capture long‑term and short‑term dependencies.

## Model Components
### 1. Input structure

#### B (input projection)
- This is constructed using HiPPO.

### 2. State transition structure 

#### A (state transition)
- This is constructed using HiPPO.

### 3. Output structure

A single linear projection is simply not enough.  
The structure of a HiPPO state space forces the readout to be more complex.


#### Mult-C (output projection)
- This enables the model to generate multiple outputs from different viewpoints.
- Each slice of the C‑tensor acts as an independent readout head, providing diverse representations of the shared state.
- This multi‑view mechanism enhances the expressive power of the SSM without altering its core dynamics.

#### Attention
- The outputs from the multi‑view SSM are fed into an Attention.
- Integrates long‑term information captured by the SSM  
- Produces a unified feature vector

#### Scalar-gain
- It adjusts the magnitude.

## References
- Gu, A., et al. "Efficiently Modeling Long Sequences with Structured State Spaces." (S4)
- Gu, A., et al. "HiPPO: Recurrent Memory with Optimal Polynomial Projections."
