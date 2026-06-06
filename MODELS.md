# Model Plan

This file tracks sponsor-recommended model options and maps them to projects.
The goal is not to use every model everywhere; the goal is to choose distinctive
projects that each target different awards cleanly.

## Portfolio model priorities

| Project | Primary model path | Secondary model options | Sponsor surface | Prize angle |
| --- | --- | --- | --- | --- |
| NeighborDocs | `nvidia/NVIDIA-Nemotron-Parse-v1.1` + <=4B reasoner | `openbmb/MiniCPM-V-4.6`, Cohere Tiny Aya family (3.35B) | NVIDIA, OpenBMB, Cohere | Backyard AI, Tiny Titan, Best Demo |
| Pocket Tutor From Photos | `openbmb/MiniCPM-V-4.6` | MiniCPM 1B/4B text, Cohere Tiny Aya family (3.35B) | OpenBMB, Cohere | Backyard AI, Best Agent, multilingual usefulness |
| Flux Costume Booth | `black-forest-labs/FLUX.2-klein` | FLUX.2 [klein] LoRA/fine-tune path | Black Forest Labs, Modal | Thousand Token Wood, Off-Brand, Well-Tuned |
| Tiny Quest Radio | Cohere Transcribe | OpenBMB VoxCPM / MiniCPM-o voice path, small text model | Cohere, OpenBMB | Thousand Token Wood, Best Demo, Best Agent |
| Roast My Repo | `JetBrains/Milo-2-12B` | OpenAI/Codex build logs, Modal sandbox | JetBrains, OpenAI, Modal | Best Agent, Codex evidence, developer utility |
| Gradio Workflow Remix Lab | Gradio Workflow + small HF models | MiniCPM, Cohere, Flux, Nemotron components | Gradio/HF, multi-sponsor | Bonus Quest Champion, Off-Brand |

## Sponsor-recommended model inventory

| Sponsor | Model or family | Approx size | Best use in our portfolio | Notes |
| --- | --- | ---: | --- | --- |
| NVIDIA | `nvidia/NVIDIA-Nemotron-Parse-v1.1` | <1B | NeighborDocs document parsing | Extracts structured text, tables, classes, and bounding boxes from documents. |
| NVIDIA | Nemotron Nano / Nano Omni family | under 32B | Reasoning, multimodal document reasoning, agents | Candidate for stronger document and agent flows. |
| NVIDIA | Nemotron speech / ASR models | under 32B | Tiny Quest Radio | Candidate for voice and accessibility tasks. |
| NVIDIA | Nemotron safety models | under 32B | Any public user-input app | Optional input/output safety layer. |
| OpenBMB | `openbmb/MiniCPM-V-4.6` | 1B class | Pocket Tutor, NeighborDocs scanned docs | Strong image understanding, OCR-heavy, document/photo tutoring model. |
| OpenBMB | MiniCPM 1B text model | 1B | Tiny local assistant path | Strong Tiny Titan candidate. |
| OpenBMB | MiniCPM 4.1 8B text model | 8B | Stronger tutoring/reasoning fallback | Use when 1B quality is not enough. |
| OpenBMB | MiniCPM-o / Omni / VoxCPM voice path | under 32B | Tiny Quest Radio | Candidate for voice, TTS, and omni interaction. |
| Black Forest Labs | `black-forest-labs/FLUX.2-klein` | 4B / 9B | Flux Costume Booth | Image generation and editing; small enough to fine-tune with LoRA in an hour. |
| Black Forest Labs | FLUX.2 [klein] LoRA fine-tuning path | adapter | Flux Costume Booth | Modal-backed fine-tune route for Well-Tuned badge. |
| JetBrains | `JetBrains/Milo-2-12B` | 12B | Roast My Repo | Code-focused model for repo review and developer tooling. |
| Cohere | Cohere Transcribe | 2B | Tiny Quest Radio, accessibility docs | Low-latency ASR path. |
| Cohere | Tiny Aya multilingual LLM family | 3.35B | NeighborDocs, Pocket Tutor | Cohere's official multilingual family (Global/Water/Fire/Earth) covering 70+ languages. |
| Modal | Modal sandboxes and GPU jobs | platform | Fine-tune, batch jobs, repo sandboxing | Use for work that directly improves prize odds. |
| OpenAI | Codex / GitHub commit history | toolchain | All projects | Maintain visible Codex-authored commits for OpenAI sponsor evaluation. |

## Sponsor resource links

| Sponsor | Link |
| --- | --- |
| Black Forest Labs Flux guide | https://huggingface.co/blog/blackforestlabs/flux-1-finetuning |
| Black Forest Labs AI Toolkit | https://github.com/ostris/ai-toolkit |
| OpenBMB MiniCPM GitHub | https://github.com/OpenBMB/MiniCPM |
| OpenBMB model hub | https://huggingface.co/openbmb |
| NVIDIA NeMo cookbooks | https://github.com/NVIDIA/NeMo |
| NVIDIA Nemotron collection | https://huggingface.co/models?search=nvidia%2Fnemotron |
| JetBrains Milo 2 | https://huggingface.co/JetBrains/Milo-2-12B |
| Cohere Labs blog | https://cohere.com/blog/ |

## Per-project uniqueness

NeighborDocs:

- A practical document helper for real paperwork.
- Primary sponsor signal: NVIDIA document intelligence.
- Distinctive hook: turns messy everyday forms into obligations, deadlines, and
  next actions.

Pocket Tutor From Photos:

- A photo-based tutor for homework, worksheets, and study notes.
- Primary sponsor signal: OpenBMB MiniCPM-V.
- Distinctive hook: local-first image understanding with multilingual support.

Flux Costume Booth:

- A playful image transformation booth.
- Primary sponsor signal: Black Forest Labs Flux.
- Distinctive hook: shareable visual outputs and possible LoRA style fine-tune.

Tiny Quest Radio:

- A voice-driven micro adventure app.
- Primary sponsor signal: Cohere Transcribe plus OpenBMB voice/TTS.
- Distinctive hook: audio-first demo with a tiny story agent.

Roast My Repo:

- A developer-facing repo review agent.
- Primary sponsor signal: JetBrains Milo 2 plus OpenAI/Codex build evidence.
- Distinctive hook: useful code review with public Codex-authored commits.

Gradio Workflow Remix Lab:

- A visual pipeline playground using Gradio Workflow.
- Primary sponsor signal: Hugging Face / Gradio ecosystem.
- Distinctive hook: lets judges remix small-model workflows themselves.

## NeighborDocs first project decision

NeighborDocs should expose multiple sponsor-aligned model strategies in the UI,
but the recommended default is:

1. `nvidia/NVIDIA-Nemotron-Parse-v1.1` for document extraction.
2. A <=4B text model for summary, obligations, deadlines, and next actions.
3. Optional `openbmb/MiniCPM-V-4.6` for scanned documents and screenshots.
4. Optional Cohere tiny multilingual model for non-English explanation.

This keeps the app focused while making sponsor targeting visible to judges.

Runtime note: NeighborDocs should stay on `cpu-basic` while the rule-based MVP
is live. The project has a ZeroGPU hook for the final NVIDIA/OpenBMB/Cohere
model path, and the Space should move to `zero-a10g` only after the real model
call is attached inside the decorated function.
