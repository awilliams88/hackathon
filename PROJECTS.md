# Project Slate & Plans

This file coordinates the portfolio of submissions for the Build Small Hackathon. To maximize our chances, each project targets a specific track and maps to sponsor awards and special badges.

---

## 1. Portfolio Map

| Project | Trail | Target Sponsor | Targeted Prizes & Badges | Status |
| --- | --- | --- | --- | --- |
| **1. NeighborDocs** | Backyard AI | OpenBMB, OpenAI | OpenBMB ($10k), OpenAI ($10k), Tiny Titan ($1.5k), Off-Brand, Off-Grid | **Completed & Pushed** |
| **2. Pocket Tutor** | Backyard AI | OpenBMB | OpenBMB ($10k), Backyard AI, Best Agent ($1k), Off-Grid | Planned |
| **3. Flux Costume Booth** | Thousand Token Wood | Black Forest Labs, Modal | BFL ($3k), Modal ($20k), Well-Tuned, Off-Brand, Best Demo | Planned |
| **4. Tiny Quest Radio** | Thousand Token Wood | Cohere | Cohere ($5k), Llama Champion, Off-Grid | Planned |
| **5. Roast My Repo** | Backyard AI | JetBrains, OpenAI | JetBrains ($5k), OpenAI ($10k), Best Agent ($1k), Sharing is Caring | Planned |
| **6. Modal-Tuner** | Backyard AI (Dev tool) | Modal, OpenBMB, Cohere | Modal ($20k), Bonus Quest Champion ($2k), All Merit Badges | Planned |

---

## 2. Project Plans

### 1. NeighborDocs (Completed)
- **Concept**: A plain-English parser and summarizer for everyday household paperwork (receipts, bills, forms).
- **Badge targeting**:
  - *Off the Grid*: Runs locally on ZeroGPU when active.
  - *Off-Brand*: Premium Codex/GitHub IDE dark theme.
- **Model**: `openbmb/MiniCPM-1B-sft-bf16` (1.2B).

---

### 2. Pocket Tutor From Photos
- **Concept**: A student/parent helper where users take a photo of a homework diagram or worksheet. The app uses a multimodal VLM to solve/explain step-by-step and generate follow-up quizzes.
- **Sponsor & Model**: OpenBMB (`openbmb/MiniCPM-V-4.6`).
- **Badge targeting**:
  - *Off the Grid*: Runs on ZeroGPU locally.
  - *Off-Brand*: Interactive dashboard with scratchpad.
  - *Best Agent*: Implements a plan -> tutor -> quiz -> review loop.

---

### 3. Flux Costume Booth
- **Concept**: Whimsical image transformation booth that takes a user's portrait and generates themed personas ( explorer, robot, puppet).
- **Sponsor & Model**: Black Forest Labs (`black-forest-labs/FLUX.2-klein`) + Modal LoRAs.
- **Badge targeting**:
  - *Well-Tuned*: Uses a custom style LoRA fine-tuned on Modal and hosted on HF.
  - *Off-Brand*: Pushes beyond standard layouts for a photo-booth style interface.
- **Modal use**: Fine-tune the style models using A10G/A100 instances on Modal.

---

### 4. Tiny Quest Radio
- **Concept**: An audio-first text/voice adventure game. A tiny model narrating a branching story in short chapters, utilizing speech recognition for user inputs and TTS for narration.
- **Sponsor & Model**: Cohere (`CohereLabs/tiny-aya-global` quantized to GGUF) + Cohere Transcribe.
- **Badge targeting**:
  - *Llama Champion*: Runs the Aya global model locally on the Space CPU via `llama.cpp` (`llama-cpp-python`).
  - *Off the Grid*: Fully offline voice-to-text and story generator.

---

### 5. Roast My Repo
- **Concept**: A repository reviewer that looks at code health, documentation gaps, and commits, outputting a code roast card.
- **Sponsor & Model**: JetBrains (`JetBrains/Milo-2-12B`) + OpenAI Track.
- **Badge targeting**:
  - *Sharing is Caring*: Saves the code review steps and outputs as an shareable dataset on Hugging Face Hub.
  - *Best Agent*: Visible reasoning path (fetch repo -> scan -> compile roast card).

---

### 6. Modal-Tuner: 1-Click Fine-Tuner & Deployer
- **Concept**: A meta-developer app that allows any hackathon participant or developer to upload a small text dataset, configure training, and spin up a fine-tuning job on Modal in 1 click. The app outputs the fine-tuned adapter, compiles it into GGUF format, and uploads it directly to Hugging Face Hub.
- **Why it wins**: It is an incredibly useful utility for all small-model developers, showing off Modal's capabilities and OpenBMB/Cohere adaptability. It acts as our **Bonus Quest Champion** anchor.
- **Merit Badge Stack (All 6 Badges)**:
  - **Off the Grid**: The Gradio UI runs locally, checking state, and the resulting quantized GGUF model runs locally in the preview tab via llama.cpp.
  - **Well-Tuned**: The core purpose is to fine-tune models (e.g., MiniCPM or Aya) and publish them to HF.
  - **Off-Brand**: High-fidelity terminal-themed dashboard displaying real-time training loss plots and logs.
  - **Llama Champion**: Automatically compiles and quantizes the fine-tuned model to GGUF for llama.cpp execution.
  - **Sharing is Caring**: Automatically uploads training metrics, logs, and datasets to the Hugging Face Hub.
  - **Field Notes**: Automatically generates a comprehensive markdown "Field Notes" training report of the run.
