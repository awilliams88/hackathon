# Avenium Build Small Hackathon Workspace

This repo coordinates Avenium's Build Small Hackathon submissions. The goal is
to maximize award chances by shipping multiple small, polished, public Gradio
Spaces with clear sponsor alignment, readable documentation, demo videos, and
social posts.

## Current status

| Project | Track | GitHub | Hugging Face Space | Status |
| --- | --- | --- | --- | --- |
| NeighborDocs | Backyard AI | [neighbordocs](https://github.com/awilliams88/neighbordocs) | [build-small-hackathon/neighbordocs](https://huggingface.co/spaces/build-small-hackathon/neighbordocs) | Scaffolded |
| Pocket Tutor From Photos | Backyard AI | Pending | Pending | Planned |
| Flux Costume Booth | Thousand Token Wood | Pending | Pending | Planned |
| Tiny Quest Radio | Thousand Token Wood | Pending | Pending | Planned |
| Roast My Repo | Backyard AI / Thousand Token Wood | Pending | Pending | Planned |
| Gradio Workflow Remix Lab | Thousand Token Wood | Pending | Pending | Planned |

## Repository structure

- `projects/neighbordocs/` is a Git submodule that points to the independent
  `neighbordocs` project repo.
- `plans/` contains the portfolio strategy and implementation plans for each
  project.
- `ARCHITECTURE.md` defines the shared project structure and code standards.
- `MODELS.md` tracks model choices and sponsor alignment across submissions.
- `AWARDS.md` maps every visible award surface to the project portfolio.
- `DECISIONS.md` records thread decisions so future project repos stay
  consistent.
- `LOCAL_MODELS.md` documents what can realistically run on the local M1 iMac.
- `GUIDELINES.md` summarizes the hackathon rules, awards, and submission
  checklist.
- `RESOURCES.md` collects every link from the kickoff transcript.
- `build-small-strategy.md` keeps the original working strategy notes.

Each project must remain deployable as its own Hugging Face Space and public
GitHub repo.

## Submission contract

Every project repo must include:

- A Hugging Face Space-compatible `README.md` with frontmatter.
- A GitHub repo link in the Space README.
- Clear setup and local run instructions.
- A model section with model names, sponsors, and parameter-count compliance.
- Multiple models are allowed in one project if every model is under 32B total
  parameters.
- A short architecture section.
- `app.py`, `requirements.txt`, `run.sh`, and `src/<project_slug>/`.
- Lint, format-check, and Python compile support through `./run.sh verify`.
- One `requirements.txt` only, containing both runtime dependencies and local
  verification tools. No `requirements-dev.txt`, no default tests, and no
  `pyproject.toml` unless a project truly needs custom tooling.

Every final submission must include:

- Public Hugging Face Space under `build-small-hackathon`.
- Public GitHub repo under `awilliams88`.
- Demo video link in the Space README.
- Social post link in the Space README.
- Mention of relevant sponsors, badges, and model constraints.

## Build order

1. Ship `NeighborDocs` as the first practical Backyard AI submission.
2. Build `Pocket Tutor From Photos` to target OpenBMB and multilingual tutoring.
3. Build `Flux Costume Booth` for Black Forest Labs and social/demo appeal.
4. Build `Tiny Quest Radio` for Thousand Token Wood, ASR/TTS, and Best Demo.
5. Build `Roast My Repo` for JetBrains Milo 2 and Codex/GitHub log evidence.
6. Use the final window for `Gradio Workflow Remix Lab` or polish the strongest
   submissions.

## Operating rules

- Use CLI operations for GitHub and Hugging Face. Browser usage is only for
  local app testing and screenshots.
- Keep all GitHub repos public.
- Keep all Spaces public unless the hackathon rules require otherwise.
- Preserve Codex-authored GitHub history for OpenAI/Codex-related evaluation.
- Push the same Git commits to GitHub and the HF Space remote so project commit
  history is consistent across both surfaces.
- Prefer small, complete apps over large unfinished systems.
- Use Modal credits for training, batch jobs, sandboxes, or heavier experiments
  only where they improve award chances.
