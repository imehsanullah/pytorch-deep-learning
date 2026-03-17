
## TRAINING LOOP

┌─────────────────────────────────────────────────────────────┐
│                    TRAINING LOOP                            │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. Forward Pass                                            │
│     predictions = model(X)                                  │
│                                                             │
│  2. Calculate Loss                                          │
│     loss = loss_fn(predictions, y_true)  ← L1Loss (MAE)     │
│                                                             │
│  3. Backward Pass                                           │
│     loss.backward()  ← Calculate gradients                  │
│                                                             │
│  4. Optimizer Step                                          │
│     optimizer.step()  ← Update weights using SGD            │
│                                                             │
│  5. Zero Gradients                                          │
│     optimizer.zero_grad()  ← Reset for next iteration       │
│                                                             │
└─────────────────────────────────────────────────────────────┘

## TRAINING ITERATION   
┌─────────────────────────────────────────────────────────────────────┐
│                         ONE TRAINING ITERATION                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  X (data) ──┐                                                       │
│             │                                                       │
│  weights ───┼──→ forward() ──→ predictions                          │
│  bias ──────┘          │                                            │
│                        ▼                                            │
│                    loss_fn ──→ loss = 0.367                         │
│                        │                                            │
│                        ▼                                            │
│                   backward() ──→ computes gradients                 │
│                        │              │                             │
│                        │              ├── weights.grad = 0.12       │
│                        │              └── bias.grad = 0.08          │
│                        ▼                                            │
│                   optimizer.step() ──→ updates parameters           │
│                        │              │                             │
│                        │              ├── weights = 0.5 → 0.4988    │
│                        │              └── bias = 0.2 → 0.1992       │
│                        ▼                                            │
│                 optimizer.zero_grad() ──→ resets gradients to 0     │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
                      Repeat for many epochs
                              ↓
                    Loss decreases, model learns!


