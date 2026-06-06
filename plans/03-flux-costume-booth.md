# Flux Costume Booth Implementation Plan

## Summary

Flux Costume Booth transforms an uploaded image or selfie into a playful themed
persona and shareable poster. It is designed for strong social engagement and a
clear Black Forest Labs alignment.

## Target awards

- Thousand Token Wood.
- Black Forest Labs sponsor prize.
- Off-Brand through a custom polished Gradio UI.
- Community Choice through shareable outputs.
- Well-Tuned if a small LoRA can be trained in time.

## Architecture

```text
Image upload + theme
  -> prompt builder
  -> FLUX image edit/generation path
  -> poster text generation
  -> shareable image/card output
```

## Model plan

- Black Forest Labs FLUX.2 [klein] (4B/9B) model path.
- Optional FLUX.2 [klein] LoRA trained with AI Toolkit for a distinctive style.
- Modal credits may be used for LoRA training if it improves the final demo.

## Implementation phases

1. Gradio image upload and theme selector.
2. Wire image generation/editing backend.
3. Add polished poster output and downloadable result.
4. Add examples and README model documentation.
5. Record the strongest visual demo.

