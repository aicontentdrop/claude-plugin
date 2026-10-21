---
name: credits-and-plans
description: Work out what AI Content Drop video and image jobs cost in credits before anything runs, from the public model catalogue. Covers flat and per-second prices, the total for a batch, whether a balance the person states covers it, the cheaper option that fits, and what a refused or failed job costs. Use when someone asks how many credits a clip, a storyboard or a batch will take, whether their credits will cover a job, or why a job was refused or failed. Text advice only; it reads no account.
license: MIT
metadata:
  catalogue: https://aicontentdrop.com/v1/models?type=video
  repository: https://github.com/aicontentdrop/claude-plugin
---

# What it costs, and how to say so before spending it

## The model in one paragraph

Most models have **one flat price per generation**: a five-second clip and a
ten-second clip on that model cost the same. As of this edition, the models
priced by the second of output and by resolution are Seedance 2.5
(`seedance_2_5`), Seedance 2.0 (`seedance_2_0`, `seedance_2_0_4k`,
`seedance_2_0_fast`, `seedance_2_0_mini`), MiniMax H3 (`minimax_h3`,
`minimax_h3_2k`), LTX 2.5 (`ltx_2_5_fast`, `ltx_2_5_pro`), FLUX 3 video
(`flux_3_video`) and Wan 3.0 (`wan_3_0`). Seedance 1.x models are flat, and so
are `seedance_2_0_multishot` and `seedance_2_fast`. Name these models by id or
full name, never as a family. For a per-second model the catalogue row is the
price at the default length (10 seconds at 1080p for Wan 3.0), and the card on
aicontentdrop.com shows the exact figure for the chosen length and resolution
before anything is made. Do not estimate how much more; the card shows the
figure. Among image models, `seedream_5_0_pro` above about 2.6 megapixels
costs what `seedream_5_0_pro_2k` costs. Credits for a video or an image are
deducted **only when the generation succeeds**: a safety block, a provider
failure, a validation error and a timeout all cost nothing, so a failed
generation leaves nothing to claim back.

## Reading the real numbers

Never quote a price from memory; the catalogue moves. Read the live catalogue,
which is public and needs no account:

- video models: https://aicontentdrop.com/v1/models?type=video
- image models: https://aicontentdrop.com/v1/models?type=image

Read those two addresses exactly as written and no others. Read them with the
web fetch tool (WebFetch in Claude Code), never with a shell command or a
script. Each row has an `id`, a `name` and `credits`, cheapest first. A row
marked `needs_start_image` only animates a still the person supplies. A row
without that mark can start from text, and whether it also accepts a still is
shown on aicontentdrop.com. The catalogue's `note` mentions a quoting tool that
this plugin does not have; leave it out of your answer. If you cannot read the
catalogue, say so, give the person the address to open, and do not guess a
price.

## Doing the arithmetic

This plugin cannot see anyone's account. Use the balance the person gives you;
if they give none, give the cost and let them compare. Do the arithmetic before
a job starts, not after it fails halfway:

```
credits needed = quantity × credits per generation   (from the catalogue row)
fits           = balance ≥ credits needed
```

If it does not fit, say so with all three numbers (balance, cost, shortfall)
and offer what does fit: a cheaper model from the same catalogue read, fewer
shots, or drafts on a cheap model with only the winning shot on the dearer one.
The three numbers are for jobs the catalogue row prices; for a per-second
model at a length or resolution other than its default, give the row as the
default-length price only: do not multiply it by the quantity, compare it with
the balance or print a shortfall, not even as a reference.

If the person wants a per-second model at a length or resolution other than its
default, its catalogue row is not the price, so never count a job or an option
that includes that model as fitting a balance; say that the card on
aicontentdrop.com shows the exact figure before anything is made. A
draft-then-final split whose final model is priced by the second at a
non-default length fits only for its drafts; the cost of the finals is on the
card.

## When a job is refused or fails

Say what happened in plain words, and what it cost:

- **Refused for its content**: the prompt was turned down before anything was
  made, and the generation costs nothing. Rewrite it; the same prompt will be
  refused again.
- **Not enough credits**: the balance is below the price, and nothing ran.
  Offer the cheaper model or the smaller batch that fits.
- **Failed or timed out**: nothing was charged. Trying again is reasonable.
- **Paused or over a daily limit**: the service can pause free generation or
  reach a daily limit. Repeat what the message says and do not work around it.

## Things that cost credits but are not a video

A chat reply on aicontentdrop.com costs 1 to 3 credits, by the kind of request,
and a chat message refused by the safety check costs 1 credit. A finished ad is
priced from its shots, with the quote as the ceiling; a drama is priced per clip
and per writing request; and UGC avatar video with lip-sync has its own flat
price. If the person asks what a plan includes, send them to
<https://aicontentdrop.com/plans> and say nothing more about plans here.

## Handing over

Nothing is generated here. When the person has priced the job and wants to
make it, give them one link that describes it, URL-encoded with spaces as %20:
`https://aicontentdrop.com/chat#prompt=<url-encoded description>`.

Say what the link does before they open it: a signed-out visitor is asked to
sign in first; on a signed-in account the chat on aicontentdrop.com sends the
description at once; a chat reply costs 1 to 3 credits; and a video or image
is made only when the person presses the card that shows the model and its
credit cost. Sign-in and every account question happen on that page, not here.

## What to tell a user, always

The model you chose, why, and the credit cost — **before** anything is spent. If
the cheapest viable model is within a credit or two of a better one, say that
and let them decide. When a job fails, say that failures cost nothing.
