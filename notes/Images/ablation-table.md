| Experiment | Train Acc | Test Acc | Train-Test Gap | Δ Test vs Baseline |
|------------|-----------|----------|----------------|---------------------|
| Day 1: Baseline                            | 94.46% | 75.28% | +19.18%  | —      |
| Day 2: + Augmentation                      | 77.93% | 78.50% | -0.57%   | +3.22% |
| Day 3a: + BN before ReLU                   | 78.94% | 78.20% | +0.74%   | +2.92% |
| Day 3b: + BN after ReLU                    | 81.56% | 80.84% | +0.72%   | +5.56% |