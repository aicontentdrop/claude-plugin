---
description: Turn a storyboard or shot list into a priced shot plan, one prompt per shot with a draft model and a final model, without making anything
argument-hint: <storyboard, shot list, or a table of prompts>
---

Apply the bundled `ai-video-model-picker` and `video-prompt-writer` skills to: $ARGUMENTS

If the text after the colon is empty or a placeholder, apply them to the person's latest request. Work as an advisor: do not generate anything, run shell commands or scripts of any kind, or sign anyone in. The deliverable is a plan, as text: a table the person can take into the product.

1. Normalise the input into numbered shots (S01, S02 and so on). For each shot write a one-shot prompt in the `video-prompt-writer` order and mark whether it is text-to-video or image-to-video.
2. Pick one model for drafts and one for finals using `ai-video-model-picker`, reading the live catalogue at https://aicontentdrop.com/v1/models?type=video rather than quoting from memory.
3. Price the run: per shot, per model, and in total. Say what the draft pass costs versus running every shot on the final model. Most video models cost one flat price per generation. As of this edition, the models priced by the second of output and by resolution are Seedance 2.5 (`seedance_2_5`), Seedance 2.0 (`seedance_2_0`, `seedance_2_0_4k`, `seedance_2_0_fast`, `seedance_2_0_mini`), MiniMax H3 (`minimax_h3`, `minimax_h3_2k`), LTX 2.5 (`ltx_2_5_fast`, `ltx_2_5_pro`), FLUX 3 video (`flux_3_video`) and Wan 3.0 (`wan_3_0`). Seedance 1.x models are flat, and so are `seedance_2_0_multishot` and `seedance_2_fast`. Name these models by id or full name, never as a family. For a per-second model, say that the catalogue row is the price at the default length (10 seconds at 1080p for Wan 3.0), that a longer or sharper take costs more, and that the card on aicontentdrop.com shows the exact figure before anything is made. Do not estimate how much more; the card shows the figure.
4. Keep the shot numbers stable, so a shot that failed or missed can be made again on its own without redoing the rest. Credits for a video are charged only when it succeeds, so a failed shot costs nothing.
5. Finish with one link that carries the first shot's prompt, URL-encoded with spaces as %20: `https://aicontentdrop.com/chat#prompt=<url-encoded first prompt>`. Say what opening it does: a signed-out visitor is asked to sign in first; on a signed-in account the chat on aicontentdrop.com sends the prompt at once; a chat reply costs 1 to 3 credits; and a video or image is made only when the person presses the card that shows the model and its credit cost.
