# Build Small Hackathon Strategy

Date context: today is June 6, 2026. The public hackathon page says the build window is June 5-15, 2026, and submissions require a Hugging Face Space, a short demo video, and a social post by June 15.

## Winning Strategy

Build a portfolio of small, finished Gradio Spaces instead of betting on one large app. The target is 5-7 submissions, with each app mapped to multiple award surfaces:

- Main tracks: Backyard AI and Thousand Token Wood.
- Sponsor awards: OpenBMB, OpenAI, NVIDIA Nemotron, Modal.
- Special awards: Bonus Quest Champion, Off-Brand, Tiny Titan, Best Demo, Best Agent, Community Choice.

Every project should be polished, demoable, and documented. A mediocre app with many sponsor logos is weaker than a small app that a judge can run, understand, and remember in 90 seconds.

## Recommended Project Slate

### 1. NeighborDocs

Track: Backyard AI.

What it is: A local-first assistant for ordinary paperwork: electricity bills, school notices, medical reports, rent receipts, warranty cards, government forms. User uploads an image/PDF, the app extracts key fields, explains the document in plain language, translates it if needed, and generates a short action checklist.

Why it can win: It is specific, useful, and fits the small-model constraint honestly. It also gives us a strong demo: upload a confusing document, get a clean explanation and next steps.

Sponsor/award mapping:

- NVIDIA: Nemotron Parse for document extraction, Nemotron/Nano for reasoning.
- Cohere: multilingual summary/translation, transcribe if we add voice notes.
- OpenAI: use Codex visibly in the build story and possibly OpenAI API for optional comparison if allowed by our final rules.
- Modal: optional batch extraction or heavier model hosting.
- Tiny Titan: use a <=4B reasoning or parser path where possible.
- Best Demo: very clear before/after flow.

Suggested models:

- `nvidia/nemotron-parse` family for document parsing.
- MiniCPM-V 4.5/4.6 or small VLM fallback for image understanding.
- Cohere Tiny Aya family (3.35B) for multilingual text.

### 2. Pocket Tutor From Photos

Track: Backyard AI.

What it is: A student or parent photographs homework, a diagram, or notes. The app identifies the topic, explains the solution step-by-step, creates a tiny quiz, and optionally reads the answer aloud.

Why it can win: Clear human value, simple enough to polish, and suitable for small models. It is also relatable for social posts.

Sponsor/award mapping:

- OpenBMB: MiniCPM-V for OCR/image reasoning and MiniCPM text model for tutoring.
- Cohere: multilingual explanations.
- OpenAI: Codex-built project, potentially agentic quiz workflow.
- Best Agent: if we implement plan -> explain -> quiz -> review loop.

Suggested models:

- MiniCPM-V 4.6 for image/OCR.
- MiniCPM 1B/4B text model for explanations.
- Cohere Tiny Aya family (3.35B) (e.g. Aya Fire/Global) for multilingual support.

### 3. Flux Costume Booth

Track: Thousand Token Wood.

What it is: A whimsical image booth that turns a selfie or uploaded image into themed tiny-world personas: miniature explorer, festival puppet, comic sprite, toy catalog character, etc. Add a small story card and shareable poster.

Why it can win: Direct Black Forest Labs alignment and high social/demo appeal. It can look polished quickly.

Sponsor/award mapping:

- Black Forest Labs: FLUX.2 [klein] image generation/editing path.
- Well-Tuned: LoRA on a compact style if time allows.
- Off-Brand: custom Gradio/`gr.Server` UI.
- Community Choice: shareable outputs.

Suggested models:

- BFL FLUX.2 [klein] (4B/9B) model path.
- Optional LoRA via AI Toolkit if we can train a style fast.

### 4. Tiny Quest Radio

Track: Thousand Token Wood.

What it is: An interactive audio story/game where a tiny model narrates a branching adventure, Cohere/OpenBMB/Nemotron handles state, and TTS voices characters. The player speaks or types choices; the world updates in small chapters.

Why it can win: It is fun, AI is load-bearing, and the demo can be memorable. This is our best shot at Best Demo or Judges' Wildcard if the experience is polished.

Sponsor/award mapping:

- Cohere: ASR or multilingual story text.
- OpenBMB: MiniCPM TTS / Omni if practical.
- NVIDIA: speech/ASR if we use Nemotron speech models.
- Best Demo, Best Agent, Thousand Token Wood.

Suggested models:

- Cohere Transcribe for ASR.
- MiniCPM or Nemotron small text model for story state.
- MiniCPM TTS / available small TTS model for voices.

### 5. Roast My Repo

Track: Backyard AI or Thousand Token Wood, depending on tone.

What it is: User provides a GitHub repo URL or zipped code. A small coding model reviews it, finds maintainability issues, creates a “tiny improvement plan,” and generates a shareable repo health card.

Why it can win: It aligns with JetBrains Milo 2 and OpenAI/Codex. It is also useful to hackathon builders.

Sponsor/award mapping:

- JetBrains: Milo 2 for code-focused reasoning.
- OpenAI: Codex workflow, agentic build story.
- Best Agent: inspect -> plan -> suggest patch -> verify.
- Community Choice: developers will engage with it.

Suggested models:

- JetBrains Milo 2 12B.
- Optional tiny embedding/retrieval for file chunking.

### 6. Gradio Workflow Remix Lab

Track: Thousand Token Wood.

What it is: A visual workflow playground where a user chains small models into creative pipelines: image -> caption -> story -> voice -> poster, or document -> summary -> quiz -> audio.

Why it can win: It uses the new Gradio Workflow angle from the kickoff and can combine multiple sponsor models. It can also become the internal demo shell for other apps.

Sponsor/award mapping:

- Off-Brand: custom UI beyond default Gradio.
- Best Agent: if workflow selection is agentic.
- Bonus Quest Champion: easiest place to stack multiple badges.

Suggested models:

- Reuse models from projects 1-4.

## Build Order

Day 1: Create shared repo template, CI-style verification, HF Space deployment workflow, and ship NeighborDocs MVP.

Day 2: Ship Pocket Tutor From Photos.

Day 3: Ship Flux Costume Booth.

Day 4: Ship Tiny Quest Radio.

Day 5: Ship Roast My Repo.

Day 6: Ship Gradio Workflow Remix Lab or improve the two strongest existing apps.

Day 7: Record videos, write READMEs, social posts, project articles, and polish UI.

Day 8-9 buffer: Fix Space runtime failures, add sponsor-specific tags/mentions, gather community engagement.

## Standard Project Contract

Every project should include:

- `app.py`: Gradio app entrypoint.
- `requirements.txt`: pinned or bounded dependencies.
- `run.sh`: one-command setup, verify, and local launch.
- `verify_code.py`: formatter/linter/type/test runner wrapper.
- `README.md`: problem, model list with parameter counts, sponsor mapping, usage, demo link, social link, limitations.
- `.gitignore`: includes `.venv`, caches, generated media.
- Optional: `tests/`, `pyproject.toml`, `ruff`, `pytest`, `mypy` or `pyright`.

`run.sh` commands:

- `./run.sh setup`: create `.venv`, upgrade pip, install dependencies.
- `./run.sh`: run the Gradio app locally.
- `./run.sh verify`: run formatting, linting, tests, and import checks.
- `./run.sh format`: apply formatter.
- `./run.sh test`: run tests only.

## Tools To Enable For Autonomy

Required:

- GitHub connector with repo create/read/write/PR permissions.
- Hugging Face access token with permission to create/update Spaces under `hackathon`.
- Browser plugin for local app testing and screenshots.
- OpenAI/Codex credits/API access if we use OpenAI APIs or need OpenAI-track evidence.

Strongly recommended:

- Slack or Discord context access if sponsor announcements/support happen there. If Discord MCP is unavailable, provide pasted updates or screenshots.
- Figma connector for custom UI planning, especially Off-Brand candidates.
- Chrome connector only if actions depend on your logged-in browser session.
- Image generation skill for posters, demo thumbnails, and custom visual assets.
- Documents/Presentations/Spreadsheets skills only if we produce reports, pitch decks, or judging trackers.

Project-specific external accounts/tokens:

- Hugging Face token.
- Modal token.
- OpenAI API key.
- Optional Cohere API key, if sponsor model use requires hosted API.
- Optional BFL/FLUX access if needed.
- Optional GitHub token if the connector is not enough for CLI operations.

## Repo And Space Management

Use one GitHub repo per submission to keep Spaces, READMEs, and videos clean:

- `neighbordocs`
- `build-small-pocket-tutor`
- `build-small-flux-costume-booth`
- `build-small-tiny-quest-radio`
- `build-small-roast-my-repo`
- `build-small-workflow-remix-lab`

For each repo, mirror to a Hugging Face Space with the same slug where possible:

- `hackathon/neighbordocs`
- `hackathon/pocket-tutor`
- `hackathon/flux-costume-booth`
- `hackathon/tiny-quest-radio`
- `hackathon/roast-my-repo`
- `hackathon/workflow-remix-lab`

Automation flow per project:

1. Create GitHub repo from template.
2. Implement locally.
3. Run `./run.sh verify`.
4. Run app locally and test in Browser.
5. Push to GitHub.
6. Create or update HF Space.
7. Verify Space build and runtime.
8. Add demo video link and social post link to README.

## Decision Rule

Prioritize projects that can stack at least three award surfaces:

- A main track.
- A sponsor award.
- A special award or bonus badge.

The first two projects should be practical Backyard AI because that track rewards specificity and real use. The next two should be delightful Thousand Token Wood because they create community/demo upside. The final projects should be chosen based on which sponsors appear most responsive and which earlier apps are actually stable.
