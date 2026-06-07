# Sponsor Models

All submission models must stay under the hackathon 32B parameter cap.

## Model Inventory

| Sponsor | Model / Family | Size | Project Fit |
| --- | --- | --- | --- |
| OpenBMB | `openbmb/MiniCPM5-1B-SFT` | 1.2B | InnerSpace text reflection |
| OpenBMB | `openbmb/MiniCPM-V-4.6` | ~1B | Pocket Tutor image + text tutoring |
| OpenBMB | `openbmb/MiniCPM3-4B` | 4B | Backup compact reasoning model |
| Cohere | `CohereLabs/tiny-aya-global` | 3.35B | Tiny Quest Radio narrative |
| Cohere | Cohere Transcribe | ~2B | Tiny Quest Radio voice input |
| Black Forest Labs | `black-forest-labs/FLUX.2-klein-4B` | 4B | Flux Costume Booth image generation |
| JetBrains | Mellum2 family | 12B MoE | Roast My Repo code reasoning |

## Project Mapping

| Project | Primary Model | Runtime |
| --- | --- | --- |
| InnerSpace | `openbmb/MiniCPM5-1B-SFT` + LoRA adapter | ZeroGPU / local Space runtime |
| Pocket Tutor | `openbmb/MiniCPM-V-4.6` | ZeroGPU multimodal |
| Flux Costume Booth | `black-forest-labs/FLUX.2-klein-4B` + Modal LoRA | ZeroGPU or Modal |
| Tiny Quest Radio | `CohereLabs/tiny-aya-global` GGUF | CPU via llama.cpp |
| Roast My Repo | JetBrains Mellum2 family | ZeroGPU or local runtime |
| Modal-Tuner | Modal training containers | Modal GPU jobs |

## Modal Use

- Fine-tune small adapters for Well-Tuned badge candidates.
- Include app-format examples and multi-turn examples before final adapter runs.
- Quantize compatible models to GGUF for Llama Champion candidates.
- Publish adapters, metrics, and field notes to Hugging Face.
