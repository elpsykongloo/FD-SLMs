## Overview

This directory contains the example code and reproduction guide for **Table 2** in **Section 4 (Evaluation)** of our paper.

### Data and Benchmarks

In our work, the code and datasets are based on the following resources:

- **Full-Duplex-Bench v1.5**: https://arxiv.org/abs/2507.23159  
- **Full-Duplex-Bench v2**: https://arxiv.org/abs/2510.07838  
- **HumDial Challenge**: https://github.com/ASLP-lab/Hum-Dial

### Models

For models, we use the **official repositories** corresponding to each model name whenever available.

If the official repository does **not** provide open-source weights, we adopt one of the following strategies:

- **Use hyperparameters reported in the original paper** (e.g., *Salmonn-Omni*), or  
- **Train a local model with the same configuration** based on third-party implementations/practices (e.g., *dGSLM*).

## Differences from the Paper

We additionally report evaluation results for [FLM-Audio](https://github.com/cofe-ai/flm-audio) and [Easy-Turn](https://github.com/ASLP-lab/Easy-Turn), which are not included in the paper. They represent the latest full-duplex models released from September through December, covering both the end-to-end and modular implementation paradigms.

## Evaluation Results for different models

| Model | FTO (↓) | SL (↓) | IRD (↓) | ISR (↑) | WER (↓) | PPL (↓) | QA Acc (↑) | N-MOS (↑) | M-MOS (↑) |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Human | ~0.20 s | ~0.30 s | 2.32 s | 93.69% | 1.5% | 10.2 | 92% | 4.92 (±0.02) | 4.85 (±0.03) |
| dGSLM | 0.33 s (±0.12) | 0.15 s (±0.03) | 1.33 s | 60.31% | 25% (±3.4) | 334.4 | 17.2% | 3.85 (±0.12) | 1.38 (±0.10) |
| NTPP | 0.30 s (±0.15) | 0.18 s (±0.05) | 1.30 s | 80.82% | 7.5% (±1.22) | 35 | 55.2% | 4.15 (±0.06) | 3.95 (±0.04) |
| Moshi | 2.22 s (±0.70) | 0.75 s (±0.10) | 1.44 s | 77.73% | 5.20% (±0.13) | 59.3 | 33.8% | 3.90 (±0.07) | 3.75 (±0.06) |
| SALMONN-omni | 0.38 s (±0.10) | 0.25 s (±0.08) | 1.38 s | 85.6% | 8.40% (±0.20) | 21.1 | 61% | 3.85 (±0.10) | 3.95 (±0.15) |
| VITA-1.5 | 2.10 s (±0.65) | 0.12 s (±0.05) | 9.49 s | 78.53% | 5.45% (±0.10) | 26.8 | 50.5% | 4.00 (±0.08) | 4.10 (±0.10) |
| Freeze-Omni | -0.40 s (±0.05) | 1.11 s (±0.17) | 9.25 s | 54.97% | 7.30% (±0.05) | 30.2 | 56.9% | 3.80 (±0.10) | 3.90 (±0.07) |
| FLM-Audio |  |  |  |  |  |  |  |  |  |
| Easy Turn |  |  |  |  |  |  |  |  |  |

This is the translated English Markdown version of your documentation. I have polished the technical terminology to ensure it meets international academic standards for a GitHub repository.

Metric Definitions

- **Floor Transfer Offset (FTO):** The signed time difference between the end of the previous speaker's turn and the start of the next speaker's turn. 
    - **Convention:** FTO > 0 represents a **gap**; FTO < 0 represents an **overlap**. 
    - **Unit:** ms (or s). **|Value| ↓ is better** (closer to 0 reflects more natural turn-taking).
- **Stop Latency (SL):** The time interval from the onset of user overlapping speech to the moment the model stops speaking. 
    - **Unit:** s (or ms). **↓ is better**.
- **Interrupt-Response Delay (IRD):** The time from the start of a user interruption (overlap onset) to the moment the system begins its next response (first frame or audible syllable). 
    - **Unit:** ms (often reported as median). **↓ is better**.
- **Success-Interrupt Rate (ISR / SIR):** The proportion of user interruption events where the system successfully yields the turn (stops speaking and switches to listening/responding) within a specified tolerance window. 
    - **Unit:** %. **↑ is better**. (ISR and SIR are synonymous in most literature).
- **Word Error Rate (WER):** A measure of Automatic Speech Recognition (ASR) performance. Formula: $WER = (S + D + I) / N \times 100\%$, where $S$ = substitutions, $D$ = deletions, $I$ = insertions, and $N$ = number of reference words. 
    - **Unit:** %. **↓ is better**.
- **Perplexity (PPL):** Calculated using an external language model on the transcribed text of generated dialogues. It represents the exponentiation of the average negative log-likelihood per word. 
    - **Unit:** Dimensionless. **↓ is better**.
- **QA Accuracy:** The percentage of samples where the answer in spoken/multi-turn QA is judged as correct. 
    - **Unit:** %. **↑ is better**.
- **N-MOS (Naturalness MOS):** Mean Opinion Score for subjective auditory naturalness (5-point scale, including confidence intervals/standard error). 
    - **Unit:** Score. **↑ is better**.
- **M-MOS (Meaningfulness MOS):** Mean Opinion Score for subjective semantic coherence and meaningfulness (5-point scale, including confidence intervals/standard error). 
    - **Unit:** Score. **↑ is better**.

To ensure full reproducibility and provide a reliable reference for future researchers, we detail the sources and implementation code for all data presented in the paper below:

1.  **Human Data:** We present results based on *Stivers et al., 2009 (PNAS)* and *Levinson & Torreira, 2015 (Frontiers)*.
2.  **dGSLM:** The authors did not provide "one-click" runnable model weights. However, based on repository issues and community experience, we have collected all necessary components for a cascaded version of this system (including the Fisher HuBERT encoder checkpoint, Fisher k-means model, and unit dictionary), along with the complete cascading code. Details can be found in `./src/dgslm`. We plan to integrate these components into a unified model weight for future release.
3.  **NTPP:** The authors provided full source code on [GitHub](https://github.com/Chaos96/NTPP) and open-sourced weights on [Hugging Face](https://huggingface.co/aigc-x/NTPP/tree/main). To replicate, follow their download instructions, wrap the model into an OpenAI-compatible API, and use our provided evaluation code (details below). **Note:** For other models listed below with similar availability, we use **"SAME"** for brevity.
4.  **Moshi:** **SAME**
5.  **SALMONN-omni:** Although the authors promised open weights in their paper, they have not yet been released. Therefore, we use data reported in the [original paper](https://arxiv.org/pdf/2505.17060) (including both the main text and appendix) as a reference. For subjective MOS scores, we verified accuracy by performing manual scoring on audio samples from their [demo page](https://github.com/bytedance/SALMONN). Note that the official demo page has since been taken down (404 error).
6.  **VITA-1.5:** **SAME**
7.  **Freeze-Omni:** **SAME**
8.  **FLM-Audio:** **SAME**
9.  **Easy Turn:** The authors have released their [repository](https://github.com/ASLP-lab/Easy-Turn/tree/main) and [model weights](https://huggingface.co/ASLP-lab/Easy-Turn). However, this is an FSM (Finite State Machine) rather than a complete end-to-end audio model; it only outputs full-duplex decision tokens. In our evaluation, we utilize a locally deployed **Qwen3-Omni** as the core Large Language Model (LLM). Please note that results may vary depending on the specific core LM used.

---

## Running the Evaluation

We assume you have deployed the models locally using the methods described above and that the OpenAI-compatible API is hosted on local port `10003`.

### Environment Setup

First, verify if `tmux` is installed:
```bash
command -v tmux >/dev/null 2>&1 || (sudo apt update && sudo apt install -y tmux)
```

Next, run the setup script to create the required Conda environment:
```bash
bash setup/aux_model.sh
```


