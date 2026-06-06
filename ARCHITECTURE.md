# Architecture

This workspace coordinates multiple Build Small Hackathon submissions. Each
submission is a separate GitHub repo and a separate Hugging Face Space. The
parent repo tracks strategy, shared standards, model choices, and project links.

## Parent workspace

```text
README.md
ARCHITECTURE.md
MODELS.md
PROJECTS.md
AWARDS.md
projects/
  <project-slug>/  # Git submodule for the independent project repo
```

The parent repo is not a runtime app. It should stay focused on coordination,
documentation, project links, and submission status.

## Standard project structure

Every project repo should follow this simplified flat structure:

```text
README.md
app.py
config.py
core.py
ui.py
styles.py      # optional, for custom CSS
runtime.py     # optional, for runtime patches
requirements.txt
run.sh
```

## File responsibilities

- `README.md`: Hugging Face Space card, submission documentation, GitHub link,
  model table, architecture notes, local setup, demo/social links, limitations.
- `app.py`: small entry point only. It sets safe runtime defaults, imports the
  UI factory, and launches the Gradio app.
- `requirements.txt`: one runtime dependency file for Space and local setup.
- `run.sh`: creates `.venv`, installs dependencies, installs local-only tooling,
  runs lint/format/type checks, and launches the app.
- `config.py`: project constants, model names, limits, and labels.
- `core.py`: project logic, model loading, GPU/ZeroGPU detection, and model inference.
- `ui.py`: Gradio layout and event wiring.
- `styles.py`: custom CSS for premium styling.


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
- **Clean Code & Imports**: Put all imports at the very top of each file. Avoid dynamic or inline imports inside functions. **Exception**: Modal remote functions (decorated with `@app.function`) must import their container-only dependencies (e.g. `torch`, `peft`, `datasets`) inside the function body, because those packages are installed inside the remote GPU container and are not available in the local development environment.
- **Comment Styling**: Place comments above the code or code block they describe. Never write inline comments (in front of code on the same line). Ensure comments are short, single-lined, and meaningful. Do not use structural or numeric labels (like `Step 1`, `Step 2`).
- **No Ignores**: Fix all lint, formatting, or type-checking issues directly in the code rather than using comments (like `# type: ignore` or `# noqa`) to disable/bypass rules. If necessary, adjust project-wide tool configurations (e.g. `pyrightconfig.json`).


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

## GPU and ZeroGPU standard

- Prefer Gradio + ZeroGPU for projects whose main model needs GPU and can run
  through PyTorch-compatible inference.
- Keep CPU-first demos on `cpu-basic` until they have a real model-backed
  `@spaces.GPU` function.
- Do not set a Space to ZeroGPU just to reserve hardware; Hugging Face can fail
  startup when no decorated function is detected.
- Do not add `spaces` to `requirements.txt`; the Hugging Face runtime provides
  it for ZeroGPU.
- Put every ZeroGPU entry point (decorated with `@spaces.GPU`) directly in the project's `core.py`, allowing the app to run on CPU, ZeroGPU, or any GPU seamlessly by default.
- Record the exact hardware choice and switch command in each project README.

