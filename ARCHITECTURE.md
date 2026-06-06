# Architecture

This workspace coordinates multiple Build Small Hackathon submissions. Each
submission is a separate GitHub repo and a separate Hugging Face Space. The
parent repo tracks strategy, shared standards, model choices, and project links.

## Parent workspace

```text
README.md
ARCHITECTURE.md
GUIDELINES.md
MODELS.md
plans/
projects/
  <project-slug>/  # Git submodule for the independent project repo
```

The parent repo is not a runtime app. It should stay focused on coordination,
documentation, project links, submission status, and shared decisions.

## Standard project structure

Every project repo should follow this structure unless the project has a clear
reason to differ:

```text
README.md
app.py
requirements.txt
run.sh
src/
  <project_slug>/
    __init__.py
    config.py
    core.py
    ui.py
```

Optional folders:

```text
assets/      # images, screenshots, demo media, CSS, examples
examples/    # sample inputs for demos and screenshots
```

## File responsibilities

- `README.md`: Hugging Face Space card, submission documentation, GitHub link,
  model table, architecture notes, local setup, demo/social links, limitations.
- `app.py`: small entry point only. It sets safe runtime defaults, imports the
  UI factory, and launches the Gradio app.
- `requirements.txt`: one runtime dependency file for Space and local setup.
- `run.sh`: creates `.venv`, installs dependencies, installs local-only tooling,
  runs lint/format checks, and launches the app.
- `src/<project_slug>/config.py`: project constants, model names, limits, labels.
- `src/<project_slug>/core.py`: project logic and model orchestration.
- `src/<project_slug>/ui.py`: Gradio layout and event wiring.

## Dependency policy

- Use a single `requirements.txt` per project.
- Do not add `requirements-dev.txt`.
- Do not add `pyproject.toml` unless a future project genuinely needs custom
  configuration.
- Put runtime dependencies and local verification tools in `requirements.txt`.
- `run.sh` must install only from `requirements.txt`; it should not manually add
  dependencies behind the reader's back.
- Keep dependency lists short, pinned, and easy to audit.
- Lint/format should use Ruff's default rules through `run.sh`; no custom config
  unless there is a project-specific reason.

## Quality policy

The hackathon priority is polished, understandable apps and complete
documentation. Tests are optional, not part of the default structure.

Each project still needs a lightweight verification flow:

```bash
./run.sh verify
```

That command should install dependencies, run Ruff format checks, run Ruff lint,
and compile Python files. It should not require a test suite.

## Code design

Keep separation of concern without adding ceremony:

- UI code should not contain model prompts, extraction logic, or business rules.
- Core logic should not import Gradio.
- `app.py` should stay thin enough to review quickly.
- Add modules only when they separate real responsibilities.
- Keep names direct and boring. Prefer clear functions over premature classes.
- Classes are useful for stateful services, model clients, or configuration that
  needs dependency injection. Do not add them only to look more formal.

## Documentation standard

Every project README must include:

- HF Space front matter.
- GitHub repo link.
- Short product explanation.
- What the app does.
- Hackathon fit and target awards.
- Model table with parameter counts and sponsor alignment.
- Architecture overview.
- Local setup and run instructions.
- Deployment link.
- Demo video and social post placeholders until final.
- Current limitations and next steps.

## Git and deployment standard

- GitHub operations use `gh`.
- Hugging Face operations use `hf`.
- Browser use is reserved for local app testing and screenshots.
- Commit history should remain authored by `Codex <codex@openai.com>`.
- After a project repo exists, push normal releases to both GitHub and the HF
  Space Git remote. Avoid `hf upload` as the normal path because it creates a
  separate HF-only commit history.
- Repo names should match between GitHub and Hugging Face Space slugs whenever
  possible.
