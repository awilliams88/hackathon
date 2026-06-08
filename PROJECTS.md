# Project Slate

This file tracks the submission portfolio and the current build priority.

## Portfolio

| Project | Track | Sponsors | Prize / Badge Targets | Status |
| --- | --- | --- | --- | --- |
| **InnerSpace** | Backyard AI | OpenBMB, OpenAI | OpenBMB, OpenAI, Tiny Titan, Well-Tuned, Off-Brand | Completed |
| **Pocket Tutor** | Backyard AI | OpenBMB | OpenBMB, Backyard AI, Best Agent, Off-Brand, Well-Tuned | Ready for remote push |
| **Flux Costume Booth** | Thousand Token Wood | Black Forest Labs, Modal | BFL, Modal, Well-Tuned, Off-Brand, Best Demo | Ready for remote push |
| **Tiny Quest Radio** | Thousand Token Wood | Cohere | Cohere, Llama Champion, Off the Grid, Tiny Titan | Ready for remote push |
| **Roast My Repo** | Backyard AI | JetBrains, OpenAI | JetBrains, OpenAI, Best Agent, Sharing is Caring, Off-Brand | Ready for remote push |

## Project Notes

### InnerSpace

- Concept: local-first CBT-informed journal reflection coach.
- Model: `openbmb/MiniCPM5-1B-SFT` plus published LoRA adapter.
- Current work: polish UI, improve second-turn coaching, and keep Hub docs complete.

### Pocket Tutor

- Concept: photo-based homework helper for students and parents.
- Model: `openbmb/MiniCPM-V-4.6`.
- Current work: multimodal Gradio Space scaffold, speech input, structured tutoring output, and Modal QLoRA adapter path.

### Flux Costume Booth

- Concept: playful portrait transformation booth.
- Model: `black-forest-labs/FLUX.2-klein-4B` plus Modal LoRA.
- Current work: portrait/text/voice costume booth, FLUX prompt generation, local generation hook, and Modal LoRA staging path.

### Tiny Quest Radio

- Concept: audio-first branching adventure game.
- Model: `CohereLabs/tiny-aya-global` quantized to GGUF.
- Current work: microphone command input, llama.cpp GGUF runtime hook, structured quest state, and Modal SFT/GGUF preparation path.

### Roast My Repo

- Concept: repo review agent that produces a useful, shareable code-health card.
- Model: `JetBrains/Mellum2-12B-A2.5B-Instruct`.
- Current work: bounded file ingestion, speech review goals, structured code-health cards, and Modal QLoRA adapter path.
