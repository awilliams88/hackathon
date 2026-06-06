# Sponsor Model Plan

This file tracks sponsor-recommended models (OpenBMB, Black Forest Labs, JetBrains, Cohere) and how we utilize **Modal** ($250 credit) to fine-tune and quantize them. All models used must remain under the **32B total-parameter cap**.

---

## 1. Sponsor Model Inventory

| Sponsor | Model / Family | Size | Best Use | Notes |
| --- | --- | --- | --- | --- |
| **OpenBMB** | `openbmb/MiniCPM-1B-sft-bf16` | 1.2B | NeighborDocs, Tiny Titan reasoning | Lightweight, fast text model optimized for on-device/Gradio deployment. |
| **OpenBMB** | `openbmb/MiniCPM3-4B` | 4.0B | Pocket Tutor reasoning, agents | Advanced compact reasoning model, great balance of speed and logic. |
| **OpenBMB** | `openbmb/MiniCPM-V-4.6` | ~8B | Pocket Tutor visual OCR, diagrams | Leading multimodal model for scanned images and tutoring. |
| **Cohere** | `CohereLabs/tiny-aya-global` | 3.35B | Tiny Quest Radio multilingual narrative | Compact multilingual instruction-tuned model covering 70+ languages. |
| **Cohere** | Cohere Transcribe | ~2B | Tiny Quest Radio voice command | Speech-to-text model for audio interface. |
| **Black Forest Labs** | `black-forest-labs/FLUX.2-klein` | 4.0B | Flux Costume Booth image generation | Visual output generation; small enough to train LoRAs in under an hour. |
| **JetBrains** | `JetBrains/Milo-2-12B` | 12B | Roast My Repo code intelligence | High-quality, specialized model for repository roasts and code analysis. |

---

## 2. Modal Fine-Tuning & Quantization Strategy ($250 Credit)

We have **$250 in Modal credits** to fine-tune, quantize, and publish custom models to the Hugging Face Hub. This is key to unlocking the **Well-Tuned** and **Llama Champion** merit badges.

### Fine-Tuning (Well-Tuned Badge)
- **Image/Style Persona**: Fine-tune a LoRA on `FLUX.2-klein` using Modal GPU instances (e.g., A100/H100) with a custom style dataset (explorer, robot, puppet) in 15-30 minutes.
- **Text/Behavior**: Fine-tune `MiniCPM-1B-sft-bf16` or `tiny-aya-global` with custom dataset instructions on Modal and export the adapter to Hugging Face.

### Quantization & llama.cpp (Llama Champion Badge)
- After fine-tuning, use a Modal GPU/CPU sandbox to run `llama.cpp` tools:
  1. Convert the PyTorch/BF16 weights to GGUF.
  2. Quantize the GGUF model to 4-bit precision (Q4_K_M) to make it run extremely fast on a basic CPU Space.
  3. Publish the GGUF model repository to the Hugging Face Hub.

---

## 3. Project Model Mapping

| Project | Primary Model | Role | Runtime Target |
| --- | --- | --- | --- |
| **NeighborDocs** | `openbmb/MiniCPM-1B-sft-bf16` | Document text reasoning | CPU basic with ZeroGPU local load |
| **Pocket Tutor** | `openbmb/MiniCPM-V-4.6` | Image diagram/homework parsing & tutoring | ZeroGPU (multimodal) |
| **Flux Costume Booth** | `black-forest-labs/FLUX.2-klein` + custom Modal LoRA | Personal portrait styling | ZeroGPU / Modal inference |
| **Tiny Quest Radio** | `CohereLabs/tiny-aya-global` (quantized to GGUF) | Narrative/Adventure story generation | CPU basic (running via `llama.cpp`) |
| **Roast My Repo** | `JetBrains/Milo-2-12B` | Repository file analysis | ZeroGPU / Serverless fallback |
| **Modal-Tuner** | Custom training container on Modal | Fine-tunes and quantizes MiniCPM/Aya | Modal GPU jobs + Gradio frontend |
