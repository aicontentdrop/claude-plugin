---
description: Plan a storyboard or shot list as a priced, resumable batch without running it
argument-hint: <storyboard, shot list, or spreadsheet of prompts>
---

Apply the bundled `ai-video-model-picker`, `video-prompt-writer` and `api-error-handling` skills to: $ARGUMENTS

Work as an advisor. Do not submit any generation, poll any job, or write a script that does. The deliverable is a plan, as text: a table the user can take into the product.

1. Normalise the input into numbered shots. For each shot write a one-shot prompt in the `video-prompt-writer` order and mark whether it is text-to-video or image-to-video.
2. Pick one model for drafts and one for finals using `ai-video-model-picker`, reading the live catalogue at https://aicontentdrop.com/v1/models?type=video rather than quoting from memory.
3. Price the run: per shot, per model, and in total. Say what the draft pass costs versus running every shot on the final model.
4. Give each shot a stable idempotency key (shot id, not attempt id) so a rerun after a failure cannot charge twice, and note from `api-error-handling` which failures are safe to retry. Credits are charged only on success.
5. Finish by handing the user a link into the product with the first shot ready to run, URL-encoded: `https://aicontentdrop.com/chat?prompt=<encoded first prompt>`. Generation happens on that page, not here.
