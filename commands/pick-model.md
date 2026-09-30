---
description: Choose an AI video model for a brief and estimate its credit cost before anything runs
argument-hint: <brief, or a shot list with quantities>
---

Apply the bundled `ai-video-model-picker` skill to: $ARGUMENTS

Work as an advisor. Do not call any generation endpoint, run any command that generates media, or attempt to sign the user in. Everything you produce is text.

1. Decide the job: does it need native audio or dialogue, and is there a reference image that must be preserved (image-to-video) or not (text-to-video)?
2. Read the live catalogue at https://aicontentdrop.com/v1/models?type=video (no credential needed) rather than quoting a model or a price from memory.
3. Recommend one model, name the runner-up, and state the credit cost per generation and for the whole quantity. Credits are charged only on success; a model that prices by the second (the catalogue shows which) costs more for a longer or sharper take, so price the duration and resolution you recommend.
4. Finish by handing the user a link into the product with the brief ready to run, URL-encoded: `https://aicontentdrop.com/chat?prompt=<encoded brief>`. Say that generation, sign-in and any account question happen on that page, not here. Plan questions go to https://aicontentdrop.com/plans.
