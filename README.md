# Scribble to Story

A child draws a scribble. Gemma 4 looks at it, works out what it is, and writes a caption, an image prompt and a short story. SDXL-Turbo then turns the scribble into a finished illustration.

## What Gemma does

1. **Understands the drawing.** It reads the sketch and returns a caption, a child-friendly image prompt and a 2-sentence story.
2. **Makes the safety decision.** If the drawing or any text in it is violent, scary, sexual or hateful, Gemma returns a refusal and the app says "Let's draw something nice instead!". This is a model decision, not a keyword filter.
3. **Rewrites on request.** The user types a change ("make it night", "add a rainbow") and Gemma rewrites the prompt and story. Change requests go through the same safety check.

## Flow

Scribble -> Gemma (caption, prompt, story, safety check) -> optional change request -> Gemma rewrite -> SDXL-Turbo image-to-image -> illustration

## How to run

1. Open `scribble-to-story.ipynb` in Google Colab.
2. Set the runtime to **T4 GPU** (Runtime -> Change runtime type).
3. Run the cells in order. The first run downloads SDXL-Turbo (about 7 GB, a few minutes).
4. When prompted, paste your own Gemini API key. It is typed at runtime and is never stored in the notebook.
5. Open the `gradio.live` link, draw, and click "1. What did I draw?", then "2. Make it real".

## Limitations

- Runs on a Colab T4 and calls Gemma through the API, so it is **not offline**.
- The safety check is prompt-based and not perfect. It has been tested on a small number of cases only.
- Image quality varies between runs. The "How much to change your drawing" slider trades faithfulness to the sketch against creativity.
- Very vague scribbles may be misidentified. The prompt box is editable so users can correct it.
- Colab sessions disconnect, so a cold start needs the model download again.

## Tech

Gemma 4 (via the Gemini API), SDXL-Turbo (diffusers), Gradio, Google Colab.

## Screenshots
<img width="1329" height="594" alt="Screenshot 2026-10-24 115902" src="https://github.com/user-attachments/assets/3fd4c47a-2f61-4d19-a056-07a03b67552b" />
