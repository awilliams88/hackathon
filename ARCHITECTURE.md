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

Use a small flat structure by default:

```text
README.md
app.py
config.py
ui.py
styles.py
requirements.txt
run.sh
```

Add extra modules only when they own real behavior:

- `analyzer.py`: orchestration, prompts, and ZeroGPU entry points.
- `inference.py`: model loading and generation.
- `parser.py`: file parsing and output parsing.
- `runtime.py`: local runtime patches or environment loading.
- `tune.py`: training or fine-tuning jobs.
- `core.py`: optional business logic only; never use it as a re-export facade.

## File Roles

- `README.md`: Space card, product explanation, model table, architecture,
  setup, deployment link, limitations, demo/social placeholders.
- `app.py`: thin Gradio entry point. Set runtime defaults and launch the app.
- `config.py`: constants, model IDs, links, limits, labels.
- `ui.py`: Gradio layout, components, and event wiring.
- `styles.py`: custom CSS.
- `requirements.txt`: runtime and verification dependencies.
- `run.sh`: setup, verification, formatting, linting, and local launch.

## Dependencies

- Use one `requirements.txt` per project.
- Keep dependencies short, pinned when practical, and easy to audit.
- Remove unused dependencies before submission.
- `run.sh` must install only from `requirements.txt`.
- Do not add `requirements-dev.txt` or `pyproject.toml` unless the project
  genuinely needs custom tooling.
- Do not add `spaces` to `requirements.txt`; Hugging Face provides it on
  ZeroGPU Spaces.

## Verification

Every project must support:

```bash
./run.sh verify
```

That command should install dependencies, run Ruff format checks, run Ruff lint,
run Pyright, and compile Python files. Tests are optional for hackathon projects.

## Code Style

- Keep files small and easy to review.
- Keep imports at the top of each file.
- Avoid inline imports except inside Modal remote functions, where container-only
  dependencies belong inside the remote function.
- Keep names direct and readable.
- Prefer functions over classes unless state or dependency injection is useful.
- Do not keep empty facade, exporter, or ceremony modules.
- UI code should not contain prompts, parsing, model loading, or business logic.
- User-facing apps should not print debug traces during normal use.
- Training scripts may print progress because remote logs are useful.

## Comments

- Every Python source file should have useful comments for its main code blocks.
- Put comments above the code they explain.
- Do not comment imports or obvious assignments.
- Avoid inline comments at the end of code lines.
- Comments should explain intent, not restate syntax.
- Use short, single-line comments where possible.

## Models And Training

- Every model must stay under the 32B hackathon parameter cap.
- Fine-tuning scripts must say whether they train the current production output
  format or an earlier seed format.
- Before final submission, training data should match the app's user-facing
  sections and safety boundaries.
- Chat apps should include multi-turn examples for likely follow-up replies.
- Model cards should describe base model, training method, intended use,
  limitations, safety boundaries, and project links.

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
- Avoid `hf upload` for code updates because it creates a separate HF-only
  history.
- Keep GitHub repo names and Hugging Face Space slugs aligned when practical.
