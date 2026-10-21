---
description: Choose an AI video model for a brief or a shot list and work out its credit cost before anything is made
argument-hint: <brief, or a shot list with quantities>
---

Apply the bundled `ai-video-model-picker` skill to: $ARGUMENTS

If the text after the colon is empty or a placeholder, apply it to the person's latest request. Work as an advisor: do not generate anything, run shell commands or scripts of any kind, or sign anyone in. Everything you produce is text.

1. Decide the job: does it need native audio or dialogue, and is there a reference image that must be preserved (image-to-video) or not (text-to-video)?
2. Read the live catalogue at https://aicontentdrop.com/v1/models?type=video rather than quoting a model or a price from memory. If you cannot read it, say so and do not guess a price.
3. Recommend one model, name the runner-up, and state the credit cost per generation and for the whole quantity. Credits for a video are charged only when it succeeds. Most video models cost one flat price per generation. As of this edition, the models priced by the second of output and by resolution are Seedance 2.5 (`seedance_2_5`), Seedance 2.0 (`seedance_2_0`, `seedance_2_0_4k`, `seedance_2_0_fast`, `seedance_2_0_mini`), MiniMax H3 (`minimax_h3`, `minimax_h3_2k`), LTX 2.5 (`ltx_2_5_fast`, `ltx_2_5_pro`), FLUX 3 video (`flux_3_video`) and Wan 3.0 (`wan_3_0`). Seedance 1.x models are flat, and so are `seedance_2_0_multishot` and `seedance_2_fast`. Name these models by id or full name, never as a family. For a per-second model, say that the catalogue row is the price at the default length (10 seconds at 1080p for Wan 3.0), that a longer or sharper take costs more, and that the card on aicontentdrop.com shows the exact figure before anything is made. Do not estimate how much more; the card shows the figure.
4. If the person asks what a plan includes, send them to https://aicontentdrop.com/plans and say nothing more about plans here.
5. Finish with one link that carries the brief, URL-encoded with spaces as %20: `https://aicontentdrop.com/chat#prompt=<url-encoded brief>`. Say what opening it does: a signed-out visitor is asked to sign in first; on a signed-in account the chat on aicontentdrop.com sends the brief at once; a chat reply costs 1 to 3 credits; and a video or image is made only when the person presses the card that shows the model and its credit cost.
