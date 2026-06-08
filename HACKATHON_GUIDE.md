# Build Small Hackathon Guide Alignment

This checklist summarizes the Build Small Hackathon field guide requirements and
maps them to this workspace.

## Core Requirements

| Guide item | Workspace response |
|---|---|
| Submit Gradio apps as Hugging Face Spaces under `build-small-hackathon` | Every project README targets a Space under that org. |
| Keep models under 32B parameters | All listed primary models are under the cap. |
| Use sponsor models as meaningful product components | Each project maps a sponsor model to its core workflow in `MODELS.md`. |
| Include track, sponsor, and badge tags in Space README frontmatter | Each project README includes `tags:` metadata. |
| Include demo video and social post links in the Space README | InnerSpace has live links; the four new projects have explicit pending slots to fill after recording/posting. |
| Document Modal usage for Modal prize targets | Modal training/staging modules and README sections are present for every fine-tuned project. |
| Keep documentation clear enough for judges to run and inspect | Each project has setup, app, verify, architecture, model, safety, and training-data sections. |

## Project Submission Matrix

| Project | Track | Sponsor focus | Primary badges | Submission state |
|---|---|---|---|---|
| InnerSpace | Backyard AI | OpenBMB, OpenAI | Well-Tuned, Off-Brand, Tiny Titan | Published |
| Pocket Tutor | Backyard AI | OpenBMB | Best Agent, Off-Brand, Well-Tuned | Docs/code ready; demo/social pending |
| Flux Costume Booth | Thousand Token Wood | Black Forest Labs, Modal | Well-Tuned, Off-Brand, Best Demo | Docs/code ready; demo/social pending |
| Tiny Quest Radio | Thousand Token Wood | Cohere | Llama Champion, Off the Grid, Tiny Titan | Docs/code ready; demo/social pending |
| Roast My Repo | Backyard AI | JetBrains, OpenAI | Best Agent, Sharing is Caring, Off-Brand | Docs/code ready; demo/social pending |

## Final Manual Gates

Before final submission, complete these items for each of the four new projects:

1. Run the Modal training command from each `modal/tune.py`.
2. Publish the resulting model adapter or GGUF artifact to the linked Hugging Face model repo.
3. Record a short demo video.
4. Publish a social post.
5. Replace the pending demo/social links in each Space README.
6. Re-run `./run.sh verify` in each project folder.
