# TIL ai.x conference 2019.06.25

## AI for Visual Pleasure
Taehyun Kim (Hanyang University)
computational imaging - Algorithms

motion blur remove

- previous works
  Two-step approach:

- deep multi-scale CNN

super-resolution

## Frontiers of Metric-based Few-shot Learning
Jake Snell (Univ. of Toronto)

approach
1. Data augmentation
2. meta-learning
3. **metric learning**

### metric learning
metrics include
Euclidean
Manhattan

mahalanobis distance learning

neighborhood component analysis(nca)

Nonlinear NCA

few-shot classification
siamese neural networks

benefits >> 
1. simple : straightforard to understand and implement
2. interpretable : 

## Meta AI Research and System Development
Dongyeon Cho (SK telecom)

Meta AI Research
- NIPS workshop Auto-Meta
  Gradient based classification
  good initialization
  meta-learning
  Progressive NAS - RNN predictor가 좋은 evaluation만 탐색하여 성능측정한다.

  Mini-Imagenet

- Few-shot learning cross-domain
  Selection network with RNN

- Meta continual learning
  Optimizer for continual learning

Meta Learner
    Hyperparameter optim - NAS사용법
    SHAC kumar et al.,2018
    RWNN Xie et al.,2019