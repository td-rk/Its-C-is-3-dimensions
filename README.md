# C3: Channelized, Common-State, Cubic-Readout-Tensor SSM

C3 (Channelized, Common-State, Cubic-Readout-Tensor SSM) is a State Space Model architecture that improves the output projection.  

The process for obtaining output from the state space was decomposed into three components. Output directions were obtained from several output matrices. Attention was used to combine these outputs into one. The magnitude was adjusted by a scalar gain.

These three mechanisms together constitute the entire readout structure, rather than being added independently.
 
The state transition matrix A and input matrix B remain conventional 2‑dimensional matrices.

## Background

## Problem Statement

## Proposed Approach

## Components
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
