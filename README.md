# Full-Duplex Spoken Language Models (FD-SLMs)
[![arXiv](https://img.shields.io/badge/arXiv-2509.14515-b31b1b.svg)](https://arxiv.org/abs/2509.14515)

This is an evolving Github repository for the paper: [From Turn-Taking to Synchronous Dialogue: A Survey of Full-Duplex Spoken Language Models](https://arxiv.org/pdf/2509.14515), which is under review at ICASSP 2026. In this paper, we survey the field of Full-Duplex Spoken Language Models (FD-SLMs), which enable synchronous human–AI dialogue via simultaneous speaking and listening, achieving a more realistic human-computer interaction experience.

---

This is a survey, but more than a survey —— due to ICASSP's page limitation, we have omitted and abbreviated many technical details in the paper, which are highly valuable for guiding the future implementation of a Full-Duplex Spoken Language Model for practical production. Therefore, we will continue to update relevant content at this link.

If you find any mistakes, please don’t hesitate to open an issue, or contact to yxchen5522@mails.jlu.edu.cn directly.

---

### Introduction

![common event](images/Common%20full-duplex%20turn-taking%20events.png)

---

### Background




---

### Taxonomy

![Classification Chart](images/Classification%20Chart.png)

> **Note:** A modular implementation does not necessarily imply plug-and-play compatibility with other SLMs—for example, VITA-1.5 and Freeze-Omni. They are end-to-end models and can only be integrated as a whole.

---

### Existing Works

In this section, we will list all existing papers on full-duplex SLMs, covering both models and benchmarks. 

#### 1. Models

##### 1.1 Learned Synchronization ( End-to-End ) :



##### 1.2 Engineered Synchronization ( Modular ) :

| Year | Paper/Project                                                | Links                                                        | Repo                                                         | Open‑source Weight                                           | Notes                                                        |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 2025 | **Easy Turn: Integrating Acoustic and Linguistic Modalities for Robust Turn‑Taking in Full‑Duplex Spoken Dialogue Systems** | [arXiv:2509.23938](https://arxiv.org/abs/2509.23938)         | [ASLP‑lab/Easy‑Turn](https://github.com/ASLP-lab/Easy-Turn)  | [Hugging Face: ASLP‑lab/Easy‑Turn](https://huggingface.co/ASLP-lab/Easy-Turn) | Open‑source turn‑taking detector that predicts four dialogue states and releases a ~1,145‑hour train/test set; repo and model card confirm weights & datasets. ([GitHub](https://github.com/ASLP-lab/Easy-Turn)) |
| 2025 | **FireRedChat: A Fully Self‑Hosted Solution for Full‑Duplex Voice Interaction** | [arXiv:2509.19048](https://arxiv.org/abs/2509.19048)         | [FireRedTeam/FireRedChat](https://github.com/FireRedTeam/FireRedChat) | [Hugging Face org (models)](https://huggingface.co/FireRedTeam) | Self‑hosted real‑time voice agent stack; repo “News” notes releases of pVAD, turn‑detector, ASR, TTS; HF org lists these models. ([GitHub](https://github.com/FireRedTeam/FireRedChat)) |
| 2025 | **FlexDuo: A Pluggable System for Enabling Full‑Duplex Capabilities in Speech Dialogue Systems** | [arXiv:2502.13472](https://arxiv.org/abs/2502.13472)         | —                                                            | —                                                            | Proposes a plug‑and‑play duplex controller with an explicit *Idle* state; no official code/weights released with the paper. ([arXiv](https://arxiv.org/abs/2502.13472)) |
| 2024 | **Freeze‑Omni: A Smart and Low‑Latency Speech‑to‑Speech Dialogue Model with Frozen LLM** | [arXiv:2411.01941](https://arxiv.org/abs/2411.01941)         | [VITA‑MLLM/Freeze‑Omni](https://github.com/VITA-MLLM/Freeze-Omni) | [Hugging Face: VITA‑MLLM/Freeze‑Omni](https://huggingface.co/VITA-MLLM/Freeze-Omni) | Repo states inference code, demo server and weights released; HF page hosts the checkpoint. ([GitHub](https://github.com/VITA-MLLM/Freeze-Omni)) |
| 2025 | **MinMo: A Multimodal Large Language Model for Seamless Voice Interaction** | [arXiv:2501.06282](https://arxiv.org/abs/2501.06282)         | —                                                            | —                                                            | Paper and project page indicate “code and models will be released soon”; at the time of writing no official repo/weights. ([arXiv](https://arxiv.org/abs/2501.06282?utm_source=chatgpt.com)) |
| 2024 | **A Full‑Duplex Speech Dialogue Scheme Based on Large Language Model (neural‑FSM)** | [NeurIPS 2024 paper (PDF)](https://proceedings.neurips.cc/paper_files/paper/2024/file/180d4373aca26bd86bf45fc50d1a709f-Paper-Conference.pdf), [arXiv:2405.19487](https://arxiv.org/abs/2405.19487) | —                                                            | —                                                            | Introduces a 2‑state neural FSM (*SPEAK/LISTEN*) where the LLM emits control tokens to manage turn‑taking; no official code/weights. ([proceedings.neurips.cc](https://proceedings.neurips.cc/paper_files/paper/2024/file/180d4373aca26bd86bf45fc50d1a709f-Paper-Conference.pdf?utm_source=chatgpt.com)) |
| 2025 | **LLM‑Enhanced Dialogue Management for Full‑Duplex Spoken Dialogue Systems** | [arXiv:2502.14145](https://arxiv.org/abs/2502.14145)         | —                                                            | —                                                            | Positions a ~0.5B‑param semantic‑VAD LLM as the dialogue manager to control turn‑switching/keeping; authors note Interspeech 2025 submission and no code link. ([arXiv](https://arxiv.org/abs/2502.14145)) |
| 2023 | **Semantic VAD: Low‑Latency Voice Activity Detection for Speech Interaction** | [INTERSPEECH 2023 PDF](https://www.isca-archive.org/interspeech_2023/shi23c_interspeech.pdf), [arXiv:2305.12450](https://arxiv.org/abs/2305.12450) | —  (no official)                                             | —                                                            | Adds frame‑level punctuation and artificial end‑point classes; paper reports ~53% latency reduction; only third‑party re‑implementations exist, not official code. ([ISCA Archive](https://www.isca-archive.org/interspeech_2023/shi23c_interspeech.pdf?utm_source=chatgpt.com)) |
| 2025 | **SHANKS: Simultaneous Hearing and Thinking, a SLM Inference Framework** | [arXiv:2505.00408](https://arxiv.org/abs/2505.00408)         | —                                                            | —                                                            | Project page describes “listening‑while‑thinking” SLM inference; no official repository/weights were linked. ([GitHub](https://github.com/HJ-Ok/SpeculativeETD?utm_source=chatgpt.com)) |
| 2025 | **Speculative End‑Turn Detector for Efficient Speech Chatbot Assistant** | [arXiv:2503.23439](https://arxiv.org/abs/2503.23439)         | [HJ‑Ok/SpeculativeETD](https://github.com/HJ-Ok/SpeculativeETD) | —                                                            | Paper introduces an ETD dataset and a two‑stage (lightweight GRU on‑device + wav2vec server) speculative framework; repo provides dataset details, but trained weights are not provided. ([arXiv](https://arxiv.org/abs/2503.23439?utm_source=chatgpt.com)) |
| 2025 | **VITA‑1.5: Towards GPT‑4o Level Real‑Time Vision and Speech Interaction** | [arXiv:2501.01957](https://arxiv.org/abs/2501.01957)         | [VITA‑MLLM/VITA](https://github.com/VITA-MLLM/VITA)          | [Hugging Face: VITA‑1.5](https://huggingface.co/VITA-MLLM/VITA-1.5) | Official repo with training/inference; HF hosts VITA‑1.5 weights; tech report describes real‑time vision + speech interaction. ([GitHub](https://github.com/VITA-MLLM/VITA?utm_source=chatgpt.com)) |
| 2025 | **Smart Turn (project)**                                     | — (project, no formal paper)                                 | [pipecat‑ai/smart‑turn](https://github.com/pipecat-ai/smart-turn) | [Hugging Face: pipecat‑ai/smart‑turn‑v3](https://huggingface.co/pipecat-ai/smart-turn-v3) | BSD‑licensed, community‑driven turn‑detection model (v3) with CPU‑friendly inference and multi‑language support; repo README links the v3 weights and docs. ([GitHub](https://github.com/pipecat-ai/smart-turn)) |

##### 1.3 Pseudo Full-Duplex :



##### 1.4 Non-independent Models :

We define non-independent models as either prior or subsequent works from the same author team of an existing model, or fine-tuned variants built upon existing full-duplex models.



#### 2. Benchmarks



---

### Model Structure (only for e2e) :

After this, let's assume we set aside the issue of Transformer, no matter how it might be implemented—such as with a dual-tower architecture (dGSLM) or token interleaving (NTPP). In an end-to-end implementation solution, we must answer another fundamental question: who serves as the system's clock for perceiving the external world? 

Some may ask: traditional SLMs don't incorporate clocks, yet they still function properly. In fact, it is not that they lack this ability, but rather that they employ a more subtle method, which is the more familiar turn-taking in conversation. 


---

### Training Datasets

We have compiled as comprehensive a list as possible of all existing datasets available for full-duplex training and provided the methods for obtaining them.

| Dataset                     | Lang  | Scene        | Access      | License             | Channels | Hours  | Reference                                                    |
| --------------------------- | ----- | ------------ | ----------- | ------------------- | -------- | ------ | ------------------------------------------------------------ |
| AMI Meeting Corpus          | EN    | meeting      | Free        | CC BY 4.0           | 8        | ~100   | [AMI (Univ. of Edinburgh)](https://groups.inf.ed.ac.uk/ami/corpus/) |
| ICSI Meeting Corpus         | EN    | meeting      | Free        | CC BY 4.0           | ~6       | ~70    | [ICSI (Edinburgh portal)](https://groups.inf.ed.ac.uk/ami/icsi/) |
| ISL Meeting Speech Part 1   | EN    | meeting      | Paid        | LDC EULA            | 8        | ~10    | [LDC2004S05](https://catalog.ldc.upenn.edu/LDC2004S05)       |
| LibriCSS                    | EN    | meeting      | Free        |                     | 7        | 10     | [LibriCSS (GitHub)](https://github.com/chenzhuo1011/libri_css) |
| Fisher English              | EN    | phone        | Paid        | LDC EULA            | 2        | ~1,960 | [LDC2004S13 / LDC2005S13](https://catalog.ldc.upenn.edu/LDC2004S13) |
| SEAME (Mandarin–English CS) | EN+ZH | interview    | Paid        | LDC EULA            | 2        | ~192   | [LDC2015S04](https://catalog.ldc.upenn.edu/LDC2015S04)       |
| HKUST Mandarin Telephone    | ZH    | phone        | Paid        | LDC EULA            | 2        | ~149   | [LDC2005S15](https://catalog.ldc.upenn.edu/LDC2005S15)       |
| NIST Meeting Pilot          | EN    | meeting      | Paid        | LDC EULA            | ~16      | ~15    | [LDC2004S09](https://catalog.ldc.upenn.edu/LDC2004S09)       |
| CHiME‑6                     | EN    | dinner‑party | Free        | CC BY‑SA 4.0        | 16       | 50+    | [OpenSLR SLR150](https://www.openslr.org/150/)               |
| DiPCo (Dinner Party Corpus) | EN    | dinner‑party | Free        | CDLA‑Permissive‑1.0 | 35       | ~5     | [Zenodo DOI](https://zenodo.org/records/8122551)             |
| AliMeeting (M2MeT)          | ZH    | meeting      | Free        | CC BY‑SA 4.0        | 8        | 118.75 | [OpenSLR SLR119](https://www.openslr.org/119/)               |
| AISHELL‑4                   | ZH    | meeting      | Free        |                     | 8        | ~120   | [OpenSLR SLR111](https://openslr.org/111/)                   |
| MISP‑Meeting                | ZH    | meeting      | Application |                     | 8        | 125    | [MISP 2025 Data](https://mispchallenge.github.io/mispchallenge2025/data.html) |
| AISHELL‑5                   | ZH    | in‑car       | Free        | CC BY‑SA 4.0        | 8        | 100+   | [OpenSLR SLR159](https://openslr.org/159/)                   |
| Switchboard‑1 Release 2     | EN    | phone        | Paid        | LDC EULA            | 2        | ~260   | [LDC97S62](https://catalog.ldc.upenn.edu/LDC97S62)           |
| Fisher Spanish Speech       | ES    | phone        | Paid        | LDC EULA            | 2        | ~163   | [LDC2010S01](https://catalog.ldc.upenn.edu/LDC2010S01)       |
| Fisher Levantine Arabic CTS | AR    | phone        | Paid        | LDC EULA            | 2        | ~45    | [LDC2007S02](https://catalog.ldc.upenn.edu/LDC2007S02)       |


---

### Training Strategy



---

### Our Benchmark

Based on FD-Bench and Full-Duplex-Bench (v1.5)—especially the latter, for which we extend special thanks to Professor Hung-yi Lee—we have developed an even more convenient benchmark built upon the engineering details of the [ICASSP HumDial Challenge](https://aslp-lab.github.io/HumDial-Challenge/). Our goal is to enable as close to one-click evaluation of your model as possible and ultimately provide a quantifiable score. We name this benchmark **Badcat**. For details, please refer to `Badcat-Benchmark/README.md`.

---

### Pre-LLM Era Related Research

We believe that in the age of AI, it is more important than ever to honor the foundational work of our predecessors—whose ideas can be revitalized and find new life in the era of large language models, much like how LSTM once revolutionized NLP. In the pre-LLM era, the Spoken Dialogue Systems (SDS) community had long been exploring full-duplex interaction. Therefore, we list a selection of representative works from this line of research and provide brief summaries. We encourage readers to consult the original papers to fully grasp the authors’ ideas.

---

### Citation

If you find our survey useful for your research, please 📚cite📚 the following paper:

```
@article{chen2025FD-SLMs,
  title={From Turn-Taking to Synchronous Dialogue: A Survey of Full-Duplex Spoken Language Models},
  author={Yuxuan Chen, Haoyuan Yu}
  journal={arXiv preprint arXiv:2509.14515},
  year={2025}
}
```

---

### Change log

**Update (October 31)** 

This repository will now receive regular updates to maintain the most current survey content.

I recently participated in the [ICASSP HumDial Challenge](https://aslp-lab.github.io/HumDial-Challenge/), which temporarily delayed updates to this repository. However, this experience provided valuable insights into full-duplex implementation, particularly regarding modular approaches.

Additionally, several recent full-duplex papers have been published, such as FLM-Audio[[2509.02521]](https://arxiv.org/abs/2509.02521), and will be incorporated into upcoming updates.