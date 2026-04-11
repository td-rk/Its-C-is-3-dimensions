# C3: Channelized, Common-State, Cubic-Readout-Tensor SSM

The only structural change is that C becomes a 3-dimensional tensor.
Other components such as A and B remain ordinary 2-dimension matrices.
Any additional structures are not essential; the core of C3 lies solely in the 3D C-tensor.


# Conpornent
## Mult-View SSM
The A and B matrices of this SSM are HiPPO matrices. The C-tensor makes several output from multiple viewpoint.

## Attention model
The outputs of SSM and a recent small amount of raw data are both given to Attention model. Attention model combines these inputs and integrates them into a vector.

## MLP
Role of this MLP is similar to that of FFN in Transformer. 
