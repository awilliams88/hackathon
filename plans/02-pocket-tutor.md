# Pocket Tutor From Photos Implementation Plan

## Summary

Pocket Tutor From Photos helps parents and students understand homework from an
uploaded image. It explains the problem, generates a small quiz, and can produce
a short study checklist.

## Target awards

- Backyard AI.
- OpenBMB via MiniCPM-V and MiniCPM text models.
- Cohere Tiny Aya family multilingual support if we target South Asian or multilingual use.
- Best Agent through an explain -> quiz -> review workflow.

## Architecture

```text
Homework image
  -> OCR / image understanding
  -> topic classification
  -> step-by-step explanation
  -> quiz generation
  -> review feedback
```

## Model plan

- MiniCPM-V for image/OCR reasoning.
- MiniCPM 1B/4B or another eligible small text model for explanations.
- Optional Cohere Tiny Aya family for multilingual explanations.

## Implementation phases

1. Gradio image upload and OCR placeholder.
2. Integrate MiniCPM-V or hosted small VLM path.
3. Add quiz generation and answer review.
4. Add examples for math, science, and notes.
5. Finalize README, video, and social proof.

