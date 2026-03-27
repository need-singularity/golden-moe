# Golden MoE

## Project Overview
Golden Zone-based Mixture of Experts routing library.
Optimal inhibition ratio I~1/e emerges from information theory.
Extracted from TECS-L -- standalone, pip-installable MoE implementation.

## Parent Project
Part of the TECS-L family. Mathematical foundation at https://github.com/need-singularity/TECS-L
Atlas: https://need-singularity.github.io/TECS-L/atlas/

## Key Constants
```
  Golden Zone Center = 1/e ~ 0.3679
  Optimal I = 0.375 (empirical, closest to 1/e)
  Expert count = 8 (default)
  Boltzmann temperature T = I/(1-I)
```

## Results
```
  MNIST:  Golden MoE 97.7% > Top-K 97.1% (+0.6%)
  CIFAR:  Golden MoE 53.0% > Top-K 48.2% (+4.8%)
  Gap increases 8x with scale
```

## Files
```
  golden_moe.py           -- Core NumPy implementation (8-expert MoE)
  golden_moe_torch.py     -- PyTorch version + MNIST benchmark
  golden_moe_cifar.py     -- CIFAR-10 scale dependency test
  golden_moe_recurrent.py -- Golden MoE + LSTM combination
  golden_moe_gpu_benchmark.py -- Multi-scale GPU benchmarking
  golden_moe_score.py     -- Element-wise score evaluation
  bitnet_golden_moe.py    -- BitNet + Golden MoE integration
  benchmark_cifar.py      -- CIFAR-10 meta engine benchmark
  model_utils.py          -- Shared training utilities
```

## How to Run
```bash
# Core MoE demo
python3 golden_moe.py

# MNIST benchmark
python3 golden_moe_torch.py

# CIFAR-10 scale test
python3 golden_moe_cifar.py

# GPU benchmark
python3 golden_moe_gpu_benchmark.py
```

## Background Execution
All experiments must run in background. No exceptions.
```
  Rules:
    1. All python3 scripts -> run_in_background: true
    2. Check results with Read after completion
    3. No foreground execution (blocks user dialogue)
```
