# llm-edge-bench 🚀

[](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-agx-xavier/)
[](https://huggingface.co/)
[](https://opensource.org/licenses/MIT)

> **Comparative performance analysis of ultra-lightweight LLMs: Cloud (Colab) vs. Edge (Jetson Xavier).**

This repository contains the benchmarking suite and implementation guides for evaluating **\<4B parameter** Large Language Models. The project focuses on the trade-offs between cloud-based inference and local edge deployment on NVIDIA Jetson hardware for a formal research review.

-----

## 📊 Research Objectives

The goal of this project is to provide empirical data for a review paper comparing:

  * **Performance:** Tokens Per Second (TPS) and Time to First Token (TTFT).
  * **Efficiency:** VRAM consumption and Power Draw (Watts).
  * **Quantization:** Impact of 4-bit -$Q4\_K\_M$- quantization on inference speed across platforms.

-----

## 💻 Hardware Comparison

| Feature | Cloud Baseline (Colab) | Edge Target (Jetson Xavier) |
| :--- | :--- | :--- |
| **GPU** | NVIDIA T4 / L4 | 512-core Volta (Tensor Cores) |
| **RAM** | 12GB - 16GB GDDR6 | 8GB - 16GB (Unified Memory) |
| **OS** | Linux (Ubuntu 22.04) | Ubuntu (L4T / JetPack) |
| **Power** | \~70W - 150W | **10W - 30W** |

-----

## 🧠 Supported Models

  * **Gemma 3 (Google):** sliding-window attention, text-only at 1B
  * **Qwen 3 (Alibaba):** hybrid thinking/non-thinking modes, Apache 2.0

-----

## 🛠️ Project Structure

```text
├── colab/      # Notebooks for baseline testing & GGUF model dumping
├── jetson/     # Scripts for llama.cpp & jtop power monitoring
├── data/       # CSV exports of benchmark results
└── scripts/    # Python utilities for calculating TPS and Latency
```

-----

## 📈 Key Metrics Measured

  * **Throughput:** $Tokens / Second$
  * **Latency:** $TTFT (ms)$
  * **Energy Efficiency:** $Joules / Token$ (via `tegrastats`)
  * **Memory:** Peak VRAM utilization

-----

## 🚀 Quick Start (Phase 1: Colab)

1.  Navigate to `/colab` and open `ultralight_llm_bench_colab.ipynb`.
2.  Run benchmarking cells to establish **Cloud Baseline**.
3.  Execute the **Model Dump** script to export `.gguf` files for the Xavier.

## 📜 Citation

If you use this benchmarking suite for your research, please cite:

-----

*This project is part of a performance review paper on lightweight edge intelligence.*
