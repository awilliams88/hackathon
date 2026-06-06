# Local Model Feasibility

Target machine: Apple Silicon M1 iMac with 16 GB RAM.

This machine is useful for local development, UI testing, prompt iteration, and
small quantized model experiments. It should not be treated as the main runtime
for larger multimodal, image-generation, or speech models.

## Practical local tiers

| Model size | Local feasibility on M1 / 16 GB | Notes |
| --- | --- | --- |
| <=1B | Good | Best fit for local experiments and Tiny Titan paths. |
| 2B-4B | Usually workable if quantized | Good target for local-first demos using MLX, llama.cpp, or small Transformers paths. |
| 7B-8B | Possible but tight when quantized | Expect slower responses and memory pressure. Keep context short. |
| 12B | Not recommended locally | Might run heavily quantized, but too slow/tight for productive demo work. |
| 30B+ | Not practical locally | Use HF ZeroGPU, Modal, inference providers, or smaller alternatives. |

## Project implications

NeighborDocs:

- Local M1 is fine for the current rule-based version.
- A <=4B quantized text reasoner may be feasible.
- Nemotron Parse should be evaluated on Hugging Face/Modal rather than assumed
  local on M1.

Pocket Tutor:

- MiniCPM-V class models may be tight locally depending on runtime and
  quantization.
- Better target: HF Space/ZeroGPU or a smaller distilled path.

Flux Costume Booth:

- Flux image generation/editing is not a good fit for M1 / 16 GB.
- Use ZeroGPU, Modal, or sponsor starter Spaces.

Tiny Quest Radio:

- Small ASR/TTS may be possible locally if quantized and CPU-friendly.
- Full interactive voice/omni models should use HF/Modal.

Roast My Repo:

- Milo 2 12B is not a good local target on this machine.
- Use HF/Modal/inference provider or a smaller local reviewer fallback.

## Recommendation

Use the M1 iMac for:

- local Gradio UI testing,
- docs and repo work,
- small quantized <=4B experiments,
- quick rule-based and prompt-flow validation.

Use Hugging Face Spaces, ZeroGPU, Modal, or inference providers for:

- image generation/editing,
- larger VLMs,
- 8B-12B code models,
- speech/omni models,
- anything that needs reliable public demo performance.
