# Golden MoE

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)

Golden Zone-based Mixture of Experts routing. The optimal inhibition ratio I~1/e emerges naturally from information theory, placing the gating function at the edge of chaos.

> Part of the [TECS-L](https://github.com/need-singularity/TECS-L) project family.

## Discovery Progress — Golden MoE

```
  Level 1: Proof of Concept  ████████████████████ 100%
    ✅ Boltzmann router  ✅ Cusp monitor  ✅ 8-expert MoE  ✅ Golden Zone I≈1/e
    ✅ MNIST 97.7% (+0.6%)  ✅ CIFAR 53.0% (+4.8%)  ✅ Gap 8x at scale

  Level 2: PyTorch + GPU     ████████████████████ 100%
    ✅ PyTorch backprop version  ✅ CIFAR-10 benchmark  ✅ Multi-scale GPU benchmark
    ✅ BitNet integration  ✅ LSTM+MoE recurrent variant  ✅ Score evaluation

  Level 3: LLM Integration   ████████░░░░░░░░░░░░ 40%
    ✅ Golden MoE router in AnimaLM (Mistral 7B)  ✅ Training pipeline (golden-llama)
    ⬜ Full LLM training (>1B params)  ⬜ PPL < 20 on Wikitext
    ⬜ Comparison vs Switch Transformer  ⬜ Comparison vs GShard

  Level 4: Production        ██░░░░░░░░░░░░░░░░░░ 10%
    ⬜ pip installable package  ⬜ HuggingFace integration
    ⬜ Distributed training support  ⬜ ONNX export
    ⬜ Benchmark on ImageNet  ⬜ Published paper

  Level 5: Adoption          ░░░░░░░░░░░░░░░░░░░░ 0%
    ⬜ External users  ⬜ Citations  ⬜ Framework integration (PyTorch/JAX)
    ⬜ Industry deployment  ⬜ Community contributions

  Overall: Level 2.4 / 5.0  (core proven, LLM integration in progress)
  Bottleneck: LLM-scale training (needs GPU hours)
  Theory: 100%  |  Implementation: 70%  |  Adoption: 0%
```

### Level-Up Priority Roadmap

```
  Level 2 → 3 (40% → 100%) — Fastest ROI
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

    #1 ★★★ Full LLM training (1B+ params)
       Difficulty: HIGH (GPU hours needed, RTX 5070 or RunPod A100)
       Effect: Prove MoE advantage at LLM scale
       → golden-llama training pipeline ready, needs compute

    #2 ★★★ Wikitext PPL < 20
       Difficulty: HIGH (depends on #1)
       Effect: Publishable result, competitive with Switch Transformer
       → Train on full Wikitext-103

    #3 ★★☆ Switch Transformer comparison
       Difficulty: MEDIUM
       Effect: Direct comparison with SOTA MoE
       → Same model size, same data, same compute budget

    #4 ★☆☆ GShard comparison
       Difficulty: MEDIUM (multi-GPU required)
       Effect: Distributed MoE comparison
       → After #3


  Level 3 → 4 (10% → 100%) — Package & Publish
  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

    #5 ★★★ pip install golden-moe
       Difficulty: MEDIUM
       Effect: Anyone can use it in 1 line
       → setup.py + PyPI upload

    #6 ★★☆ HuggingFace integration
       Difficulty: MEDIUM
       Effect: transformers.GoldenMoEModel
       → Custom modeling file + config

    #7 ★★☆ Paper submission
       Difficulty: HIGH (writing + review)
       Effect: Academic recognition
       → Target: ICML or NeurIPS workshop

    #8 ★☆☆ ONNX export
       Difficulty: LOW
       Effect: Cross-framework deployment
       → torch.onnx.export wrapper
```

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
