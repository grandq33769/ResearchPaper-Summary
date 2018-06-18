# Measuring Catastrophic Forgetting in Neural Networks
#Paper/ML# 

## Summary
- Multi-layer preceptron(MLP) architecture and typical training algorithms cannot handle incrementally learning new tasks or categories without catastrophically forgetting previously learned training data.
- Catastrophic forgetting is often overcome simply by storing new training examples and then re-training either the entire network from scratch or possibly only the last few layers. -> Too slow !!
- Five common mechanisms for mitigating catastrophic forgetting
	1. regularization
	2. ensembling
	3. rehearsal
	4. dual-memory models
	5. sparse-coding
- Trained a network by using three different scenarios: 
	1. Identical tasks with different permutations of input,
	2. Similar tasks with incremental classes
	3. Dissimilar tasks

## Five mechanisms of mitigating catastrophic forgetting
### 	Regularization Methods
	- High plasticity: easily affected by changes
	- High stability: harder to adapt
	- ::Elastic Weight Consolidation (EWC):: :The Fisher matrix is used to constrain the weights important to previously learned tasks to their original value.

### 	Ensemble Methods
	- Memory usage will scale with the number of sessions, which is highly undesirable.
	- Accuracy Weighted Ensembles & Life-long Machine Learning: Automatically decide whether a sub-network should be removed or added to the ensemble
	- ::PathNet::  : Since entire portions of the network are sequentially frozen as new tasks are learned, there is a risk of PathNet losing its ability to learn once the maximum capacity is reached.
	- Accessing that output layer during prediction time requires a priori information on which session the model needs to access.
	
### 	Rehearsal Methods
	- Rehearsal methods try to mitigate catastrophic forgetting by mixing data from earlier sessions with the current session being learned (Robins 1995).
	- ::GeppNet:: stores all previous training data and replays it along with the previous data during a portion of its incremental learning step.

### 	Dual-Memory Models
	- Dual-memory models are inspired by memory consolidation in the mammalian brain, which is thought to store memories in two distinct neural networks.
	- Dual-memory models incorporate rehearsal, but not all rehearsal-based models are dual-memory models.
	- ::Gepp-Net+STM:: also stores all previous and new training data; however, each training example is only replayed if the modelis uncertain on the prediction.

### 	Sparse-Coding Methods
	- Sparse Distributed Memory (SDM): convolution-correlation model that uses sparsity to reduce the overlap between internal representations
	- ::The Fixed Expansion Layer (FEL)::  : model creates sparse representations by fixing the network’s weights and specifying neuron triggering conditions.
	- The second hidden layer (FEL-layer) has a higher capacity than the first fully-connected layer, but the weights are sparse and remain fixed through training.

## Reason of occuring  catastrophic forgetting
::Catastrophic forgetting in neural networks occurs because of the stability-plasticity dilemma::

## Approaches of solving catastrophic forgetting
1. To try to keep new and old representations separate, which can be done using distributed models, regularization, and ensembling.
2. To prevent the forgetting of prior knowledge simply by training on the old tasks (or some facsimile of them) as well as new tasks, thereby preventing the old tasks from being forgotten.
	
## Experiments
- To provide a fair comparison, the number of parameters in each model were chosen to be as close as possible to the number of parameters in the baseline MLP.
- We do not assume sessions are iid.
- The model is only permitted to learn sessions sequentially.

1. ::Data Permutation Experiment:: : The elements of every
feature vector are randomly permuted
2. ::Incremental Class Learning:: : Each new session learned contains only a single class.
3. ::Multi-Modal Learning:: : The model incrementally learns
different datasets.
	- Inputs with different dimensionality
	- A different number of classes

### 	Datasets
	1. MNIST
	2. CUB-200
	3. AudioSet
	
### 	Reason of choosing these datasets
	1. Different data modalities (image and audio)
	2. A large number of classes
	3. A small number of samples per class

### 	Evaluation
	1. Base: Measures a model’s retention of the first session
	2. New:  Measures the model’s ability to immediately recall new tasks
	3. All: How well a model both retains prior knowledge and acquires new information.

### 	Results
	- PathNet performed best overall on the data permutation experiments, with the exception of CUB-200.
	- Because permuting the data does not reduce feature overlap, the model requires more trainable weights(less weight sharing) to build a discriminative model, causing PathNet to saturate (freeze all weights) more quickly.
	- Both GeppNet variants performed best at incremental class learning.
	- With 100-200 classes, this corresponds to 2-5 hidden layer neurons per class respectively
	- Performance may improve if their model capacity was significantly increased, but this would demand more memory and computation.
	- EWC performed best on the multi-modal experiment.
	- EWC is a better choice for separating non-redundant data and PathNet may work well when working with data that has different, but not entirely dissimilar, representations. 
	
## Suggestions
- Methods for mitigating catastrophic forgetting should have the amount of total memory they use constrained.
- Reinforcement Learning: The agent learns an initial study-session (e.g., an ATARI game), which represents the base knowledge.

## Conclusion
 ::Catastrophic forgetting is not solved.::

1. A combination of rehearsal/pseudo-rehearsal and dual-memory systems are optimal for learning new classes incrementally.
2. Regularization and ensembling are best at separating multiple dissimilar sessions in a common DNN framework

- Sparsity model (i.e., FEL) can sometimes improve significantly; however, the cost is a 40x increase in the models memory footprint.
- Learning algorithms have a larger impact compared with activation function

## Supplement Materials
###  Setting of Hyperparameters
	1. Training for a fixed period of time
	2. Using test accuracy to stop training early.

## Special Technique
	- Fisher information matrix
	- The Fixed Expansion Layer (FEL)
	- TODAM
	- CHARM
	- Sparse Distributed Memory (SDM)
	- ALCOVE
	- CALM
	- GeppNet
	- GeppNet+STM
	- pseudopatterns
	- PathNet
	- Life-long Machine Learning
	- Elastic weight consolidation (EWC)
	- Fast Correlation Based Filter
	- Evolved Plastic Artificial Neural Networks

## Vocabulary
	- prone 易於
	- urge 敦促
	- viable 可行
	- modalities 模式
	- fine-grained 細粒度
	- inhibitory 抑制
	- excitatory 興奮
	- alleviate 緩和
	- consolidated 綜合
	- pursued 追求的
	- remedy 補救
	- metrics 指標
	- catastrophically 災難性的
	- attempts 嘗試
	- considerably 相當
	- noticeably 明顯
	- emptied 清空
	- excels 過人之處

## Sentence
	- Their review ::covered a wide range of:: brain-inspired algorithms ::and also noted that:: the field lacks appropriate benchmarks.
	- ::interest in them:: has never been greater in both ::industry:: and the artificial intelligence research ::community::.
	- ::Owing to:: … , …. . 由於... , … .
	- ::In nearly every case::, … . 接近全部結果/事件/個案, … .
	- We compare learning CUB-200 ::first then:: AudioSet ::as well as:: learning AudioSet followed by learning CUB-200.
	- The performance of EWC and PathNet ::for both:: the data permutation and multi-modal experiments ::are consistent with this hypothesis.::
	- Both variants of GeppNet are ::orders of magnitude:: slower because they train the model one sample at a time.
	- ::suffered from:: … 遭遇到 …

· Highlighted Source : http://lnr.li/ghrOX/
· Original Source : http://getliner.com/webpdf/web/viewer.html?file=86b1f1ed4792c3b931b04aac282664fa.pdf