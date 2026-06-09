# Architecture

This workspace coordinates Build Small Hackathon submissions. The parent repo
tracks strategy, standards, model choices, and project links. Each submission
lives in its own project folder and deploys as its own Hugging Face Space.

## Workspace

```text
README.md
ARCHITECTURE.md
MODELS.md
PROJECTS.md
AWARDS.md
<project-slug>/
```

The parent repo is not a runtime app. Keep it focused on coordination and
submission documentation.

## Project Structure

Every project uses a domain-grouped layout. The root holds only the Hugging
Face Spaces entry point and project-wide config files:

```text
app.py                  ← HF Spaces entry point (must stay at root)
requirements.txt
run.sh
pyrightconfig.json
README.md

env/                    ← App infrastructure
│   __init__.py
│   config.py           ← All constants: model IDs, URLs, limits, labels
│   runtime.py          ← Environment loading and runtime patches

core/                   ← Business domain logic
│   __init__.py
│   analyzer.py         ← Orchestration, prompts, ZeroGPU entry points
│   inference.py        ← Model loading and text generation
│   parser.py           ← File reading and output section splitting

ui/                     ← Presentation layer
│   __init__.py
│   layout.py           ← Gradio components and event wiring
│   styles.py           ← Custom CSS

modal/                  ← Remote fine-tuning (optional)
    tune.py             ← Modal orchestrator and remote training function
    dataset.py          ← Training dataset and prompt builders
    CARD.md             ← Model card metadata for the HF model repository
```

### Domain ownership rules

| Package | Owns | Must never import from |
|---|---|---|
| `env/` | Constants, env vars, runtime patches | `core/`, `ui/` |
| `core/` | Business logic, model orchestration | `ui/` |
| `ui/` | Gradio layout, CSS, event wiring | model loading, parsing, or prompt internals |
| `modal/` | Remote training only | `core/`, `ui/` |
| root `app.py` | Entry point — wires `env`, `core`, `ui` | — |

Add extra files within the appropriate domain package or create new domains for them only when they own real
behaviour. Do not add files to the root beyond `app.py`.

## File Roles

- `README.md`: Space card, product explanation, demo links, model table, architecture, setup, deployment link, limitations.
- `app.py`: thin Gradio entry point. Wires `env`, `core`, and `ui`. Set runtime defaults and launch the app.
- `env/config.py`: all constants — model IDs, links, limits, labels.
- `env/runtime.py`: environment loading and runtime patches (asyncio etc.).
- `core/analyzer.py`: orchestration, prompts, ZeroGPU entry points.
- `core/inference.py`: model loading and text generation.
- `core/parser.py`: file reading and output section splitting.
- `ui/layout.py`: Gradio layout, components, and event wiring.
- `ui/styles.py`: custom CSS.
- `requirements.txt`: runtime and verification dependencies.
- `run.sh`: setup, verification, formatting, linting, and local launch.

## Dependencies

- Use one `requirements.txt` per project.
- Keep dependencies short, pinned when practical, and easy to audit.
- Remove unused dependencies before submission.
- `run.sh` must install only from `requirements.txt`.
- Do not add `requirements-dev.txt` or `pyproject.toml` unless the project genuinely needs custom tooling.
- Do not add `spaces` to `requirements.txt`; Hugging Face provides it on ZeroGPU Spaces.

## Verification

Every project must support:

```bash
./run.sh verify
```

That command should install dependencies, run Ruff format checks, run Ruff lint, run Pyright, and compile Python files.

Projects with remote model execution should also include a smoke test script
that exercises the deployed runtime or training runtime directly. Keep the
smoke command in the project README and check in the script alongside the code
so model-contract regressions can be reproduced later. For Hugging Face Spaces,
prefer a live API smoke test against the deployed Space; for Modal-backed
training or inference, prefer a `modal run ...` entrypoint.

## Code Style

- Keep files small and easy to review.
- Keep imports at the top of each file.
- Avoid inline imports except inside Modal remote functions, where container-only dependencies belong inside the remote function.
- Keep names direct and readable.
- Prefer functions over classes unless state or dependency injection is useful.
- Do not keep empty facade, exporter, or ceremony modules.
- UI code may import core callbacks for Gradio event wiring, but should not contain prompts, parsing, model loading, or business logic.
- User-facing apps should not print debug traces during normal use.
- Training scripts may print progress because remote logs are useful.

## Comments

- Every Python source file should have useful, short, meaningful comments for its main code blocks.
- Put comments above the code they explain.
- Do not comment imports or obvious assignments.
- Avoid inline comments at the end of code lines.
- Comments should explain intent, not restate syntax.
- Use short, single-line comments where possible.

## Models And Training

- Every model must stay under the 32B hackathon parameter cap.
- Fine-tuning scripts must say whether they train the current production output format or an earlier seed format.
- Before final submission, training data should match the app's user-facing sections and safety boundaries.
- Chat apps should include multi-turn examples for likely follow-up replies.
- Model cards should describe base model, training method, intended use, limitations, safety boundaries, and project links.
- Fine-tuning scripts and resources should be grouped in a dedicated `modal/` folder to separate training orchestration, dataset generation, and metadata.

## Gradio And ZeroGPU

- Prefer Gradio Spaces for every submission.
- Use ZeroGPU only when the app has a real GPU-backed model function.
- Put `@spaces.GPU` on the function that owns the model-backed behavior.
- Keep CPU-first demos on CPU hardware until GPU is genuinely needed.
- Record the Space hardware choice and switch command in the project README.

## Git And Deployment

- GitHub operations use `gh`.
- Hugging Face operations use `hf`.
- Keep commits authored as `Codex <codex@openai.com>`.
- Push normal releases through Git remotes for both GitHub and Hugging Face.
- Avoid `hf upload` for code updates because it creates a separate HF-only history.
- Keep GitHub repo names and Hugging Face Space slugs aligned when practical.
