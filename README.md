# C3: Channelized, Common-State, Cubic-Readout-Tensor SSM

C3 (Channelized, Common-State, Cubic-Readout-Tensor SSM) is a State Space Model architecture that improves the output projection.  

The process for obtaining output from the state space was decomposed into three components. Output directions were obtained from several output matrices. Attention was used to combine these outputs into one. The magnitude was adjusted using a scalar gain.
 
The state transition matrix A and input matrix B remain conventional 2‑dimensional matrices.

## Conpornent
### 1. Multi‑View SSM
- The matrices A and B are constructed using HiPPO.
- The C‑tensor enables the model to generate multiple outputs from different viewpoints.
- Each slice of the C‑tensor acts as an independent readout head, providing diverse representations of the shared state.

This multi‑view mechanism enhances the expressive power of the SSM without altering its core dynamics.

### 2. Attention Model
The outputs from the multi‑view SSM are fed into an Attention module.

The Attention module:
- Integrates long‑term information captured by the SSM  
- Combines it with short‑term, high‑resolution raw input  
- Produces a unified feature vector that balances both memory scales

## Summary
C3 SSM introduces:
- A 3D C‑tensor enabling multi‑view readout  
- Standard HiPPO‑based A and B matrices  
- An Attention module that fuses long‑term SSM memory with short‑term raw data  

## References
- Gu, A., et al. "Efficiently Modeling Long Sequences with Structured State Spaces." (S4)
- Gu, A., et al. "HiPPO: Recurrent Memory with Optimal Polynomial Projections."
