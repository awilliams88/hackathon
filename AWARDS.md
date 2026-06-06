# Award & Badge Strategy

This document maps the official Build Small Hackathon cash prizes and merit badges to our project portfolio. The goal is maximum prize coverage and stacking all merit badges.

## 1. Trophy Cabinet (Cash Prize Pools)

### Main Track Awards ($18,000)
- **Backyard AI** (Practical everyday apps): 
  - 1st Place: **$4,000** | 2nd Place: **$2,500** | 3rd Place: **$1,500** | 4th Place: **$1,000**
- **Thousand Token Wood** (Whimsical, playful, creative apps):
  - 1st Place: **$4,000** | 2nd Place: **$2,500** | 3rd Place: **$1,500** | 4th Place: **$1,000**
- **Community Choice (by Hugging Face)**:
  - 1 Winner (voted by the community): **$2,000**

### Sponsor Awards
- **OpenBMB Awards** ($10,000 total): Three prizes in each of the two main tracks for outstanding OpenBMB picks (utilizing MiniCPM models):
  - 1st Place: **$2,500** | 2nd Place: **$1,500** | 3rd Place: **$1,000**
- **OpenAI Track** ($10,000 total): OpenAI's own podium across all submissions (evidence of Codex-authored commit logs and OpenAI utility):
  - 1st Place: **$5,000** | 2nd Place: **$3,000** | 3rd Place: **$2,000**
- **Other Cash/Sponsor Awards**:
  - **Cohere Awards**: **$5,000** cash prize pool.
  - **JetBrains Awards**: **$5,000** cash prize pool.
  - **Black Forest Labs Awards**: **$3,000** cash prize pool.
  - **Modal Awards**: **$20,000** in Modal credits for top Modal-powered submissions.

### Special Awards ($8,000)
- **Bonus Quest Champion ($2,000)**: The most merit badges stacked on a single project sash.
- **Off-Brand Award ($1,500)**: Best custom UI pushing past default Gradio styling (`gr.Server` is your friend).
- **Tiny Titan ($1,500)**: Best app built on a genuinely tiny model (<=4B parameters).
- **Best Demo ($1,000)**: Great app, outstanding demo video, and clear social post.
- **Best Agent ($1,000)**: Best agentic app (under the 32B parameter cap).
- **Judges' Wildcard ($1,000)**: Standout creative entry that fits no other category.

---

## 2. Merit Badge Stacking Strategy (For "Bonus Quest Champion")

To win the **Bonus Quest Champion ($2,000)** and maximize our special award chances, we target every single merit badge across our portfolio, with a special focus on stacking them in our meta-tool **Modal-Tuner**:

| Badge | Criteria | How we target it |
| --- | --- | --- |
| **Off the Grid** | Run models entirely locally within the app environment (no third-party cloud APIs). | Run models locally on CPU/WebGPU in the app or on ZeroGPU. |
| **Well-Tuned** | Use a fine-tuned model published on Hugging Face. | Fine-tune MiniCPM or Tiny Aya using our **$250 Modal credit**, export to Hugging Face, and load it. |
| **Off-Brand** | Implement custom UI beyond the default Gradio look. | Use custom CSS overrides and custom JS (`styles.py` and `gr.HTML`/`gr.Server`). |
| **Llama Champion** | Run the model locally using `llama.cpp` / GGUF. | Deploy a GGUF format model and run it via `llama-cpp-python` in the Space. |
| **Sharing is Caring** | Share the agent trace/run details on the Hugging Face Hub. | Publish structured run execution logs, user inputs, and outputs to a Hugging Face dataset automatically. |
| **Field Notes** | Publish a detailed report or blog post detailing the build and lessons learned. | Create a comprehensive markdown report of the project's architecture, training run, and findings. |

---

## 3. Project Portfolio Award Map

| Project | Trail | Target Sponsor | Badge Stacking | Special Awards Targeted |
| --- | --- | --- | --- | --- |
| **NeighborDocs** | Backyard AI | OpenBMB, OpenAI | Off the Grid, Off-Brand | Tiny Titan (1.2B), Best Demo |
| **Pocket Tutor** | Backyard AI | OpenBMB | Off the Grid, Off-Brand | Best Agent, Tiny Titan (4B) |
| **Flux Costume Booth** | Thousand Token Wood | Black Forest Labs, Modal | Well-Tuned (Modal LoRA), Off-Brand | Best Demo, Community Choice |
| **Tiny Quest Radio** | Thousand Token Wood | Cohere | Off the Grid, Llama Champion (llama.cpp) | Judges' Wildcard, Tiny Titan |
| **Roast My Repo** | Backyard AI | JetBrains, OpenAI | Off the Grid, Sharing is Caring | Best Agent, OpenAI Track |
| **Modal-Tuner** | Backyard / Developer | Modal, OpenBMB, Cohere | **All Badges** (Off-Grid, Well-Tuned, Off-Brand, Llama, Sharing, Field Notes) | Bonus Quest Champion, Best Agent, Judges' Wildcard |
