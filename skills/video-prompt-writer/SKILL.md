---
name: video-prompt-writer
description: Write or fix a video prompt so an AI video model produces the shot someone described. Covers the shot-first structure, the camera and lighting language models follow, when a reference image is needed to keep a product or person recognisable, how long a clip should run, and how to change one thing per attempt without wasting credits. Use when someone wants a brief, a script or a storyboard frame turned into a video prompt, a prompt for animating a still image, or a diagnosis of a clip that came out wrong. Text advice only; it makes no video.
license: MIT
metadata:
  catalogue: https://aicontentdrop.com/v1/models?type=video
  repository: https://github.com/aicontentdrop/claude-plugin
---

# Writing a video prompt that survives the model

Most disappointing generations are not a model problem. They are a prompt that
described a *concept* when the model needed a *shot*.

## Decide the job before the words

**Is there a specific thing that must be recognisable?** A real product, a
particular person, a logo, an established character.

- **Yes** → you need **image-to-video**. The person supplies a still of that
  subject, or makes one first, and the clip animates it. Text-to-video
  re-invents the subject every run; no amount of prompt detail fixes that,
  because the model has never seen the thing you mean.
- **No** → text-to-video is fine and cheaper to iterate on.

**Does it need speech or synced audio?** Only some models generate native audio,
and the catalogue rows do not say which. Name the need in the brief rather than
assuming, and if the model cannot do it, plan the voiceover as a separate step
instead of hoping.

## The structure that works

Describe one shot, in this order:

1. **Subject and action** — who or what, doing one specific thing.
2. **Setting** — where, and what time of day.
3. **Camera** — the shot size and the move: *static wide*, *slow push in*,
   *handheld follow*, *low-angle tracking*.
4. **Light** — direction and quality: *hard afternoon sun from the left*,
   *soft overcast*, *single practical lamp*.
5. **Treatment** — the finish: *shallow depth of field*, *anamorphic*,
   *documentary*, *35mm grain*.

```
A barista sets a ceramic cup on a wooden counter and slides it forward.
Small independent cafe, early morning. Static medium shot, slight push in.
Warm low sun through a window on the left, soft shadows.
Shallow depth of field, 35mm, natural colour.
```

That is one shot. It has a subject doing one thing, a place, a camera, a light
source and a finish — everything the model needs and nothing it has to guess.

## The four habits that separate good prompts from bad ones

**One shot per generation.** A prompt describing three beats gets you a model
choosing between them, or cutting incoherently. Multi-beat sequences are several
generations you assemble, not one prompt.

**One action.** "Walks in, sits down, opens a laptop and smiles" is four
actions competing for a few seconds. Pick the one that carries the moment.

**Describe presence, not absence.** Negative instructions are unreliable. Rather
than "no text on the wall", describe a plain concrete wall.

**Change one variable per iteration.** If you rewrite the whole prompt between
attempts, you cannot tell which change helped. Vary the camera, or the light, or
the action — not all three.

## Length, and why the first second matters most

These models hold a coherent idea for a few seconds and then drift: hands
wander, faces soften, backgrounds reinvent themselves. Two consequences:

- Prefer the **shortest duration that carries the beat**. A clean 5 seconds
  beats a 10-second clip whose back half you will cut anyway.
- Put the **essential content early**. If the shot must show the product
  clearly, it should be clear at second one, not arriving at second eight.

On most models a longer clip costs the same credits as a shorter one; only the
models priced by the second cost more for a longer or sharper take. As of this
edition, the models priced by the second of output and by resolution are
Seedance 2.5 (`seedance_2_5`), Seedance 2.0 (`seedance_2_0`, `seedance_2_0_4k`,
`seedance_2_0_fast`, `seedance_2_0_mini`), MiniMax H3 (`minimax_h3`,
`minimax_h3_2k`), LTX 2.5 (`ltx_2_5_fast`, `ltx_2_5_pro`), FLUX 3 video
(`flux_3_video`) and Wan 3.0 (`wan_3_0`). Seedance 1.x models are flat, and so
are `seedance_2_0_multishot` and `seedance_2_fast`. Name these models by id or
full name, never as a family. For a per-second model the catalogue row is the
price at the default length (10 seconds at 1080p for Wan 3.0), and the card on
aicontentdrop.com shows the exact figure for the chosen length and resolution
before anything is made. Do not estimate how much more; the card shows the
figure.

## Iterating without burning the budget

Credits are charged only on success, so a failed run costs nothing but a
rejected-looking one costs full price. The cheap path:

1. The person finds the prompt on a **cheap** model that supports the job;
   read the prices from the live catalogue as `ai-video-model-picker`
   describes. Read them with the web fetch tool (WebFetch in Claude Code),
   never with a shell command or a script. Composition and action read fine
   at low cost. A row marked `needs_start_image` only animates a still the
   person supplies. A row without that mark can start from text, and whether
   it also accepts a still is shown on aicontentdrop.com.
2. They make the take that ships once, on the dearer model, with the winning
   prompt.

Quote the cost before step 2 — see `ai-video-model-picker`. When you point the
person at choosing the model, name the plugin's command in full:
`/aicontentdrop:pick-model`.

## Diagnosing a bad result

| What you got | The usual cause | The fix |
| --- | --- | --- |
| Subject is not the thing they meant | text-to-video invented it | Switch to image-to-video from a real still |
| Drifts or morphs late in the clip | duration beyond the coherent window | Shorter duration; put the payload early |
| Nothing moves, or it is one slow zoom | no camera or action specified | Name the move and one concrete action |
| Right idea, wrong mood | light unspecified | Give direction and quality of light |
| Refused | content gate | Rewrite; nothing was charged, so do not retry unchanged |

## What to hand back

The prompt, the model you recommend and its credit cost, and, when a first
attempt missed, what you changed and why. A user who can see the one variable
you moved can direct the next iteration themselves.

If the person wants to run it on AI Content Drop, end with one link that carries
the prompt, URL-encoded with spaces as %20:
`https://aicontentdrop.com/chat#prompt=<url-encoded prompt>`. Say what opening
it does: a signed-out visitor is asked to sign in first; on a signed-in account
the chat on aicontentdrop.com sends the prompt at once; a chat reply costs 1 to
3 credits; and a video or image is made only when the person presses the card
that shows the model and its credit cost.
