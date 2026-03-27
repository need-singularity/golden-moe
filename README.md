# Golden MoE

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)

Golden Zone-based Mixture of Experts routing. The optimal inhibition ratio I~1/e emerges naturally from information theory, placing the gating function at the edge of chaos.

> Part of the [TECS-L](https://github.com/need-singularity/TECS-L) project family.

## Results

| Dataset | Golden MoE | Top-K MoE | Gap |
|---------|-----------|-----------|-----|
| MNIST | 97.7% | 97.1% | **+0.6%** |
| CIFAR-10 | 53.0% | 48.2% | **+4.8%** |

- Optimal I = 0.375 ~ 1/e (Golden Zone center)
- Gap increases **8x** with scale
- Boltzmann router + Cusp catastrophe monitor

## Quick Start

```bash
# Basic demo (NumPy)
python golden_moe.py

# PyTorch MNIST benchmark
python golden_moe_torch.py

# CIFAR-10 scale dependency
python golden_moe_cifar.py

# GPU multi-scale benchmark
python golden_moe_gpu_benchmark.py
```

## Architecture

```
Input -> Boltzmann Router (I~1/e) -> Expert Selection -> Output
                |
        Cusp Monitor (catastrophe detection)
```

The Boltzmann router uses temperature T = I/(1-I), placing the optimal routing at the Golden Zone center 1/e ~ 0.368. This is the phase transition point between:
- I < 1/e: Too many experts active (waste)
- I > 1/e: Too few experts active (underfitting)
- I ~ 1/e: Edge of chaos (optimal)

## Files

| File | Description |
|------|------------|
| `golden_moe.py` | Core implementation (NumPy, 8-expert) |
| `golden_moe_torch.py` | PyTorch version with MNIST benchmark |
| `golden_moe_cifar.py` | CIFAR-10 scale dependency test |
| `golden_moe_recurrent.py` | Golden MoE + LSTM combination |
| `golden_moe_gpu_benchmark.py` | Multi-scale GPU benchmarking |
| `golden_moe_score.py` | Element-wise score evaluation |
| `bitnet_golden_moe.py` | BitNet + Golden MoE integration |
| `benchmark_cifar.py` | CIFAR-10 meta engine benchmark |
| `model_utils.py` | Shared training utilities |

## Theory

The Golden Zone (I in [1/2 - ln(4/3), 1/2]) emerges from the 4-state model of cognitive function:
- Upper bound = 1/2 (Riemann critical line)
- Center ~ 1/e (natural constant)
- Width = ln(4/3) (entropy jump from 3->4 states)

For the full mathematical foundation, see [TECS-L](https://github.com/need-singularity/TECS-L).

## Citation

```bibtex
@software{golden_moe_2026,
  author = {Park, Min Woo},
  title = {Golden MoE: Golden Zone-based Mixture of Experts},
  year = {2026},
  url = {https://github.com/need-singularity/golden-moe}
}
```

## License

MIT
