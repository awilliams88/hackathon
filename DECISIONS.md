# Project Decisions

This file records decisions made in the thread so future projects stay
consistent.

## Repository and deployment

- The parent workspace is a coordination repo, not an app repo.
- Each project gets its own GitHub repo and its own Hugging Face Space.
- Project folders are tracked in the parent workspace as Git submodules.
- GitHub and Hugging Face repo slugs should match when possible.
- GitHub operations use `gh`.
- Hugging Face operations use `hf`.
- Browser usage is reserved for local app testing and screenshots, not GitHub or
  Hugging Face operations.

## Commit history

- Commits should be authored as `Codex <codex@openai.com>`.
- GitHub history matters for the OpenAI/Codex sponsor track.
- Hugging Face Spaces are also Git repos. To keep GitHub and HF commit histories
  aligned, push the same Git branch to both remotes.
- Avoid using `hf upload` for normal project deployment once a project repo is
  established, because `hf upload` creates separate HF-only commits.

Recommended project remotes:

```bash
git remote add origin https://github.com/awilliams88/<project>.git
git remote add hf https://huggingface.co/spaces/build-small-hackathon/<project>
git push origin main
git push hf main
```

If histories diverge, force-push the known-good project branch to the HF remote
after verifying the files are correct:

```bash
git push --force-with-lease hf main
```

## Project file structure

Use this default shape:

```text
README.md
app.py
requirements.txt
run.sh
src/<project_slug>/
  __init__.py
  config.py
  core.py
  runtime.py     # only when needed
  ui.py
examples/
assets/
```

Rules:

- One `requirements.txt` only.
- No default `requirements-dev.txt`.
- No default `pyproject.toml`.
- No default test suite unless the project risk justifies it.
- `run.sh` installs only from `requirements.txt`.
- `app.py` stays thin.
- Core logic does not import Gradio.
- UI logic stays in `ui.py`.

## Hackathon rules

- Multiple models are allowed in one project.
- Every individual model must be under 32B total parameters.
- The 32B limit is based on total parameters, not active parameters.
- Each submission needs a Gradio Space under `build-small-hackathon`.
- Each final submission needs a demo video and social post.

## Product strategy

- Build multiple focused projects to maximize prize coverage.
- Each project needs one primary award story and one or two secondary stories.
- Complete, polished apps are more valuable than large unfinished systems.
- Every README must be judge-readable even if GPU quota or API limits affect
  runtime.
- UI quality matters, especially for Off-Brand, Best Demo, and Community Choice.

## Project 1: NeighborDocs

Current positioning:

- Practical document helper for everyday paperwork.
- Primary award: Backyard AI.
- Sponsor target: NVIDIA Nemotron Quest.
- Secondary targets: Tiny Titan, Best Demo, Off-Brand, OpenAI Track.
- Default model strategy: NVIDIA Nemotron Parse plus a <=4B reasoner.
- Candidate add-ons: OpenBMB MiniCPM-V for scanned documents, Cohere tiny
  multilingual model for translation/local-language explanation.
