---
name: ai-video-model-picker
description: Choose which AI video model to use for a shot, a storyboard or a batch of clips, and work out the credit cost before anything is made, from the public AI Content Drop model catalogue. Use when someone asks which video model fits a brief, whether a shot needs image-to-video or native audio, which model to draft on and which to finish on, or what a list of clips will cost. Text advice only; it makes no video.
license: MIT
metadata:
  catalogue: https://aicontentdrop.com/v1/models?type=video
  repository: https://github.com/aicontentdrop/claude-plugin
---

# Picking an AI video model (and knowing what it costs)

Use this when someone has a brief, a shot list or a storyboard and has to decide
*which model* to make it with, or wants to know what a batch will cost before
committing. You advise and price; nothing is generated here.

## The one rule

Price it before anyone generates. Video models differ in cost by more than ten
times across the catalogue, so "just use the best one" can turn a 20-clip
storyboard into an expensive surprise. Never quote a price from memory; the
catalogue moves. Read the live catalogue, which is public and needs no account:

- video models: https://aicontentdrop.com/v1/models?type=video
- image models: https://aicontentdrop.com/v1/models?type=image

Read those two addresses exactly as written and no others. Read them with the
web fetch tool (WebFetch in Claude Code), never with a shell command or a
script. Each row has an `id`, a `name` and `credits`, the price of one
generation at the model's default settings, cheapest first. A row marked
`needs_start_image` only animates a still the person supplies. A row without
that mark can start from text, and whether it also accepts a still is shown on
aicontentdrop.com. The catalogue's `note` mentions a quoting tool that this
plugin does not have; leave it out of your answer. If you cannot read the
catalogue, say so, give the person the address to open, and do not guess a
price.

## Choosing

Ask two questions before looking at the list.

**1. Does the shot need dialogue or synced audio?**
If yes, you need a model that generates native audio. The catalogue rows do not
say which models do, so do not name one from memory: put the need in the brief
you hand over, and if the model has no native audio, plan the voiceover as a
separate step. If no, you have the whole catalogue and should optimise for cost.

**2. Is there a reference image?**
Text-to-video and image-to-video are different jobs. If the user has a product
photo, a still, or a character they want preserved, you want image-to-video —
starting from text will not preserve identity, and no amount of prompt detail
fixes that.

Then pick by budget:

- **Draft, storyboard, or a variant you will throw away** → the cheapest model
  that supports the job. Iterate here, not on the expensive one.
- **The take that ships** → move up only for the shot that survived.
- **Batches** → price the whole list from one read of the catalogue: quantity
  times credits for each model, then the total.

## Handing over

Nothing is generated here. When the person has chosen and wants to make it,
give them one link that carries the brief, URL-encoded with spaces as %20:
`https://aicontentdrop.com/chat#prompt=<url-encoded brief>`.

Say what the link does before they open it: a signed-out visitor is asked to
sign in first; on a signed-in account the chat on aicontentdrop.com sends the
brief at once; a chat reply costs 1 to 3 credits; and a video or image is made
only when the person presses the card that shows the model and its credit
cost. Sign-in and every account question happen on that page, not here.

## What to tell the user

Report the model you picked, why, the runner-up, and the credit cost for one
generation and for the whole quantity, before anything is spent. If the
cheapest viable model is within one credit of a better one, say so and let them
choose.

## Facts you can rely on

- Most video models cost one flat price per generation. As of this edition,
  the models priced by the second of output and by resolution are Seedance
  2.5 (`seedance_2_5`), Seedance 2.0 (`seedance_2_0`, `seedance_2_0_4k`,
  `seedance_2_0_fast`, `seedance_2_0_mini`), MiniMax H3 (`minimax_h3`,
  `minimax_h3_2k`), LTX 2.5 (`ltx_2_5_fast`, `ltx_2_5_pro`), FLUX 3 video
  (`flux_3_video`) and Wan 3.0 (`wan_3_0`). Seedance 1.x models are flat, and
  so are `seedance_2_0_multishot` and `seedance_2_fast`. Name these models by
  id or full name, never as a family. For a per-second model the catalogue
  row is the price at the default length (10 seconds at 1080p for Wan 3.0),
  so a longer or sharper take costs more; say so, and say that the card on
  aicontentdrop.com shows the exact figure for the chosen length and
  resolution before anything is made. Do not estimate how much more; the
  card shows the figure.
- Credits for a video are charged **only when it succeeds**. Safety blocks,
  provider failures and timeouts cost nothing, so a failed generation leaves
  nothing to claim back. A chat reply is charged on its own, as above.
- If the person asks what a plan includes, send them to
  <https://aicontentdrop.com/plans> and say nothing more about plans here.
