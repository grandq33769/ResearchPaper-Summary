# Learning Sparse Representations in Reinforcement Learning with Sparse Coding
###### tags: `Paper/rl`
#Paper/rl

## Summary
- We provided a simple algorithm that uses alternating minimization on these variables, and proved that this simple and easy-to-use approach is principled.
- develop a supervised sparse coding objective for policy evaluation.
- Representation learning techniques in reinforcement learning have typically drawn on the large literature in unsupervised and supervised learning.
- representations are handcrafted, with some common representations including tile-coding, ra-dial basis functions, polynomial basis functions and Fourier basis functions

## Sparse Coding
- Sparse coding approaches have been developed to learn MDP models for transfer learning
- Sparse coding representations have several advantages, including that they naturally enable local models, are computationally efficient to use, are much simpler to train than more complicated models such as neural networks and are biologically motivated by the observed representation in the mammalian cortex

## Joint Optimization
- We formalize sparse coding for reinforcement learning as a joint optimization over the value function parameters and the representation
- A joint optimization over the basis and the value function parameters, to provide a supervised sparse coding objective where the basis is informed by its utility for prediction.

## Model
- The quality of the representation is critical to accurately approximating `V ^pi`with `phi``w`, but also balancing compactness of the representation and speed of learning.
- The weighted L1 promotes sparsity on the entries of promotes sparsity on the entries of `phi`, preferring entries in `phi` to be entirely pushed to zero rather than spreading magnitude across all of `phi`.
- The Frobenius norm regularizer on `B` ensures that `B` does not become too large
- we need to jointly learn and `w`, where `w` provides the approximate value function.
- The optimization must balance between accurately recreating `X` and approximating the value function `phi``w`.

## Explanation of 4 Errors
- The family of TD algorithms converge to the minimum of the MSPBE, whereas residual gradient algorithms typically use the MSBE
- The expected value of the BE is the expected squared error between the prediction from this state and the reward plus the value from a possible next state.
- The MSBE, on the other hand, is the squared error between the prediction from this state and the expected reward plus the expected value for the next state
- First, the MSBE, BE and MSRE are all convex in `phi`, whereas the MSPBE is not.
- Second, because of the projection onto the space spanned by the features, the MSPBE can be solved with zero error for any features.

## Experiment
- SCoPE
- Avoiding conflating incremental estimation
- Mountain Car, Puddle World and Acrobot
- The dimension k=100 is set to be smaller than for tile coding
- The reason for this appears to be that we optimize MSRE to obtain the representation, which is a surrogate for the MAPVE.

## Conclusion
1. The structure in the observations is not sufficient for un-supervised sparse coding
2. The combination of supervised and unsupervised losses sufficiently constrain the space to obtain discriminative representations
3. The combination of the two losses, therefore, much more effectively constrains or regularizes the space of feasible representations and improves discriminative power.

## Academic term
- mean-squared Bellman error (MSBE)
- mean-squared projected BE (MSPBE)
- the mean-squared return error (MSRE)
- Bellman error (BE)
- SCoPE
- mean absolute percentage value error (MAPVE)
- tile-coding(TC) representations
- PCA
- CCA
- ISOMAP
- L1 regularization
- Incremental estimation

## Vocabulary
- tackle
	抓住
- alleviate
	緩和
- amenable
	合適
- hinges
	關鍵
- surrogat
	代孕
- alleviates
	緩和
- analytically
	解析
- nullifying
	抵消
- constitute
	構成
- intentionally
	故意地

## Sentence
- Nonetheless
	儘管如此，...
---
- Highlighted Source : http://lnr.li/btvhg/
- Original Source : https://getliner.com/webpdf/web/viewer.html?file=ae718be0adf5a4da6362859ad0b988e5.pdf
