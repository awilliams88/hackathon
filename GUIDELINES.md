# Build Small Hackathon Guidelines

This summary combines the official Hugging Face Build Small Hackathon page with
the kickoff transcript attached to this workspace.

## Timeline

- Registration opened May 7, 2026 and closed June 3, 2026.
- Build window: June 5-15, 2026.
- Submission deadline: June 15, 2026.
- Winners: date to be announced.

## Core rules

1. Small models only: every model must be at or under 32B total parameters.
2. Built on Gradio: each app must be a Gradio app hosted as a Hugging Face
   Space under the `build-small-hackathon` org.
3. Show, do not just tell: every submission needs a short demo video and a
   social post.

Transcript clarification: multiple models are allowed as long as each model is
under the 32B total-parameter cap. The cap is based on total parameters, not
active parameters.

Practical interpretation for our portfolio: a single app may combine a parser,
vision model, text reasoner, ASR model, TTS model, embedding model, safety
model, or fine-tuned adapter. Each individual base model must stay below the
32B total-parameter limit, and the project README must list every model used.

## Main tracks

Backyard AI:

- Solve a specific real problem for someone.
- The person or use case should feel concrete.
- Judging emphasizes usefulness, real fit, the small-model constraint, and app
  polish.

Thousand Token Wood:

- Build something delightful, strange, playful, or creative.
- AI should be essential to the experience.
- Judging emphasizes originality, delight, AI-native behavior, and app polish.

## Bonus badges

- Off the Grid: no cloud APIs; the model runs in the app environment.
- Well-Tuned: uses a fine-tuned model published on Hugging Face.
- Off-Brand: custom frontend beyond default Gradio styling.
- Llama Champion: model runs through llama.cpp.
- Sharing is Caring: share the agent trace on the Hub.
- Field Notes: publish a blog post or report about what was built and learned.

## Award surfaces

- Backyard AI: top four practical submissions.
- Thousand Token Wood: top four whimsical or creative submissions.
- Community Choice: one community-voted winner.
- OpenBMB Awards: three prizes in each of the two main tracks.
- OpenAI Track: OpenAI's own podium across all submissions.
- NVIDIA Nemotron Quest: two physical GPUs for standout Nemotron builds.
- Modal Awards: top Modal-powered apps.
- Bonus Quest Champion: most merit badges stacked on one project.
- Off-Brand Award: best custom UI beyond the default Gradio look.
- Tiny Titan: best app built on a genuinely tiny model, around <=4B parameters.
- Best Demo: great app, demo video, and social post.
- Best Agent: best agentic app under the 32B cap.
- Judges' Wildcard: standout project that does not fit a normal category.

## Sponsor notes from kickoff

- OpenAI: sponsor track prizes and Codex credits. We should preserve visible
  Codex-authored GitHub commits.
- OpenBMB: MiniCPM models are strong for on-device, vision, document, tutoring,
  and voice/omni projects.
- NVIDIA: Nemotron models are important for document intelligence, parsing,
  retrieval, speech, safety, and general reasoning. Nemotron builds target the
  physical GPU prizes.
- Modal: use credits for fine-tuning, batch processing, sandboxes, and temporary
  GPU jobs where they materially improve the submission.
- Black Forest Labs: Flux-based image generation/editing projects are strong
  for whimsical and visual demos.
- JetBrains: Milo 2 is a strong fit for code-focused developer tooling.
- Cohere: transcription and small multilingual models are strong for audio,
  translation, summarization, and cross-lingual apps.

## Submission checklist

Each final project needs:

- Public Hugging Face Space under `build-small-hackathon`.
- Public GitHub repo linked from the Space README.
- Space README with model list and parameter counts.
- Demo video link.
- Social post link.
- Clear sponsor/badge targeting.
- Clean app behavior on the live Space.

## Winning strategy

- Ship complete apps rather than broad unfinished systems.
- Keep the first screen usable, not a landing page.
- Make the demo path obvious within 10 seconds.
- Stack sponsor relevance and bonus badges only when they strengthen the app.
- Keep README files complete enough that judges can evaluate even if GPU or
  quota issues affect runtime.
- Use example inputs and clear outputs so the demo video is easy to record.
