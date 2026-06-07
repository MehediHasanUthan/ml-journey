# Day 3 — Batch Normalization Ablation

## What I built
In this session i have added batch normalization technique to my previously built CIFAR10 CNN trained with augmented datasets. Using augmented transform to train the model prevented overfitting significantly. Now adding batch normalization should increase the test accuracy and faster convergence. At the core, normalizing activations layer-by-layer keeps gradients well-scaled, which lets the optimizer move faster.

## Training Result 

| Epoch | Day 2 (Aug) | Day 3 (Aug + BN) | Δ |
|-------|-------------|-------------------|--------|
| 1     | 55.82%      | 58.34%            | +2.52% |
| 2     | 65.68%      | 66.54%            | +0.86% |
| 3     | 69.35%      | 73.05%            | +3.70% |
| 4     | 71.77%      | 73.36%            | +1.59% |
| 5     | 73.97%      | 74.69%            | +0.72% |
| 6     | 75.23%      | 76.20%            | +0.97% |
| 7     | 76.68%      | 76.82%            | +0.14% |
| 8     | 76.95%      | 78.18%            | +1.23% |
| 9     | 78.36%      | 78.19%            | -0.17% |
| 10    | 78.50%      | 78.20%            | -0.30% |

## What Changed In The Model's Performance

The highest test accuracy of the model is 78.2 (same as the previous model, deviations due to signal noise). The difference in test accuracy isnt much. But the test accuracy reaches higher value faster with batch normalization. It doesn't increase the accuracy. Faster covergence was expected from this model. 

## Does The Model's Structure Changes The Training Results??
If we use batch normalization after relu than we get 2.64% higher accuracy without including any function or increasing parameter. But this depends on the dataset. For other type of data this may not be true

## Training Result
| Epoch | Day 2 (Aug only) | Day 3a (BN before ReLU) | Day 3b (BN after ReLU) | Δ (3b vs Day 2) | Δ (3b vs 3a) |
|-------|------------------|--------------------------|--------------------------|------------------|----------------|
| 1     | 55.82%           | 58.34%                   | 66.71%                   | +10.89%          | +8.37%         |
| 2     | 65.68%           | 66.54%                   | 72.05%                   | +6.37%           | +5.51%         |
| 3     | 69.35%           | 73.05%                   | 73.59%                   | +4.24%           | +0.54%         |
| 4     | 71.77%           | 73.36%                   | 77.23%                   | +5.46%           | +3.87%         |
| 5     | 73.97%           | 74.69%                   | 78.42%                   | +4.45%           | +3.73%         |
| 6     | 75.23%           | 76.20%                   | 78.72%                   | +3.49%           | +2.52%         |
| 7     | 76.68%           | 76.82%                   | 78.66%                   | +1.98%           | +1.84%         |
| 8     | 76.95%           | 78.18%                   | 79.09%                   | +2.14%           | +0.91%         |
| 9     | 78.36%           | 78.19%                   | 80.28%                   | +1.92%           | +2.09%         |
| 10    | 78.50%           | 78.20%                   | 80.84%                   | +2.34%           | +2.64%         |

### Revised interpretation

Initial result (BN before ReLU, "original paper" ordering) showed BN gave faster convergence but no final accuracy gain over Day 2 augmentation. The tentative conclusion was "BN only helps convergence speed in this regime."

That conclusion was wrong. After running the alternative ordering (BN *after* ReLU), the result changed substantially:

- Final test acc with BN-after-ReLU: **80.84%** (vs 78.20% with BN-before-ReLU, vs 78.50% with no BN at all).
- Epoch 1 test acc: 66.71% — a +10.89% jump over the no-BN baseline in a single epoch.
- The "modern" ordering won by +2.64% over the "original paper" ordering, at the same epoch budget.

**The lesson: a single ablation can produce misleading conclusions when an interacting design choice is held at an arbitrary value.** Sweeping over the BN-position choice revealed that BN does provide a meaningful final-accuracy gain — the first experiment just happened to use the worse ordering.

## Discussion

The model validates the property of batch normalization that is it converges the model faster. If we want to increase the test accuracy we may use for batches (epochs) to train the model.

## Reference
Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift by Ioffe & Szegedy, 2015. 

## Time spent
- 3 hours

