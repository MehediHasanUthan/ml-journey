# Day 1 — CIFAR-10 baseline

## What I built
3 layer CNN, no regularization, Adam lr=1e-3, 10 epochs, batch size 64.

## Result
- Final train acc: 94.46%
- Final test acc:  75.28%
- Best test acc:   75.78% at epoch 8

## Observation
Train or test gap widens from 0% at epoch 2 to 19% at epoch 10. Test acc plateaus
around epoch 7. Model overfits.

## What I didn't fully understand
- The pattern detecting at each stage that are represented with numbers. But the value is not actually tells anything about pattern that is getting detected

## Time spent
- 6-7hours
