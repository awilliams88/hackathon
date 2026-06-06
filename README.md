# Avenium Build Small Hackathon Workspace

This repository coordinates Avenium's Build Small Hackathon submissions. The goal is to maximize our chances in the cash prize pools by shipping public, polished Gradio Spaces targeting sponsor tracks, special categories, and merit badges.

## 1. Project Slate & Status

| Project | Trail | Target Sponsor | GitHub | Hugging Face Space | Status |
| --- | --- | --- | --- | --- | --- |
| **NeighborDocs** | Backyard AI | OpenBMB, OpenAI | [neighbordocs](https://github.com/awilliams88/neighbordocs) | [neighbordocs Space](https://huggingface.co/spaces/build-small-hackathon/neighbordocs) | **Completed & Pushed** |
| **Pocket Tutor** | Backyard AI | OpenBMB | Pending | Pending | Planned |
| **Flux Costume Booth** | Thousand Token Wood | Black Forest Labs, Modal | Pending | Pending | Planned |
| **Tiny Quest Radio** | Thousand Token Wood | Cohere | Pending | Pending | Planned |
| **Roast My Repo** | Backyard AI | JetBrains, OpenAI | Pending | Pending | Planned |
| **Modal-Tuner** | Backyard / Developer | Modal, OpenBMB, Cohere | Pending | Pending | Planned |

---

## 2. Repository Structure

- [projects/neighbordocs/](file:///Volumes/Code/HuggingFace/hackathon/projects/neighbordocs/) - Git submodule pointing to the `neighbordocs` project repository.
- [PROJECTS.md](file:///Volumes/Code/HuggingFace/hackathon/PROJECTS.md) - Consolidated implementation plans and conceptual slate for all projects.
- [MODELS.md](file:///Volumes/Code/HuggingFace/hackathon/MODELS.md) - Target sponsor models (OpenBMB, Black Forest Labs, JetBrains, Cohere) and Modal fine-tuning/quantization guides.
- [AWARDS.md](file:///Volumes/Code/HuggingFace/hackathon/AWARDS.md) - Cash prize distributions, sponsor tracks, and merit badge stacking guidelines.
- [ARCHITECTURE.md](file:///Volumes/Code/HuggingFace/hackathon/ARCHITECTURE.md) - Shared coding standards, separation of concerns, and quality rules.

---

## 3. Submission Checklist

Every project repository must include:
* A Hugging Face Space-compatible `README.md` with frontmatter.
* A public GitHub repository link in the Space README.
* A model table detailing model names, parameter counts, and sponsor alignment.
* Standard structure: `app.py`, `requirements.txt`, `run.sh`, and `src/<project_slug>/`.
* A verification script (`./run.sh verify`) that runs Ruff formatting/linting and compilation checks.

Every final submission must include:
* Public Hugging Face Space under the `build-small-hackathon` organization.
* A short demo video link and a social post link in the Space README.

---

## 4. Operating Rules
* **Git Commit Signatures**: All commits must be authored as `Codex <codex@openai.com>` for OpenAI track evaluation.
* **Remote Synchronization**: Push identical Git branches to both GitHub (`origin`) and Hugging Face (`hf`) to maintain a single, synchronized commit history. Do not use `hf upload` for code updates.
* **Separation of Concerns**: UI logic resides in `ui.py` with custom dark styling, and core inference/logic resides in `core.py` (with no Gradio imports). ZeroGPU decorators must reside in `gpu.py` to keep entry points lightweight.
* **Model Constraints**: No model in any submission may exceed the **32B total-parameter cap**.
