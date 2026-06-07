# ml-journey
Daily log of building toward research and freelance work in computer vision and ML
-Started May 30, 2026. BUET EEE.

## Structure
- `projects/` — daily notebooks and code
- `notes/` — daily reflections, what worked, what didn't
- `papers-i-read/` — paper summaries
- `papers-i-write/` — drafts of my own work

## Progress
- **Day 1:** CIFAR-10 baseline CNN — 75.28% test accuracy. Observed overfitting after epoch 7 (train/test gap widened from 0% to 19%). [View notebook on nbviewer](https://nbviewer.org/github/MehediHasanUthan/ml-journey/blob/main/projects/day01-cifar10-baseline.ipynb)
- **Day 2:** Filter and feature map visualization of the Day 1 model — observed the textbook "edges → parts → concepts" hierarchy across conv1/conv2/conv3. First ablation experiment: adding RandomCrop and HorizontalFlip augmentation lifted test accuracy to **78.50% (+3.22%)** and eliminated the train/test gap (19.18% → -0.57%). [Notebook](projects/day02-visualize-and-augment.ipynb) · [Notes](notes/day-02.md)
- **Day 3:** BatchNorm ablation on top of Day 2's augmented model. First run (BN before ReLU, the original paper's prescription) gave no improvement in final test accuracy over Day 2, only faster early-epoch convergence. Re-ran with BN *after* ReLU — final test acc jumped to **80.84% (+2.34% over Day 2, +5.56% over Day 1 baseline)**. The single-ablation conclusion would have been wrong; sweeping the BN-position design choice was what revealed the real effect. [Notebook](projects/day03-batchnorm.ipynb) · [Notes](notes/day-03.md)
