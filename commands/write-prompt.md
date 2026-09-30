---
description: Turn a brief, script or existing image into a shot-first video prompt a model will follow
argument-hint: <brief or script, and the model if already chosen>
---

Apply the bundled `video-prompt-writer` skill to: $ARGUMENTS

Work as an advisor. Do not call any generation endpoint or run a command that generates media. The output is a prompt and a short explanation, as text.

1. Decide whether the shot needs image-to-video (a specific product, person or character must stay recognisable) or text-to-video.
2. Write one shot in the skill's order: subject and action, setting, camera, light, treatment. One shot, one action, presence not absence.
3. Recommend the shortest duration that carries the beat, and say which single variable to change if the first attempt misses.
4. Finish by handing the user a link into the product with the finished prompt, URL-encoded: `https://aicontentdrop.com/chat?prompt=<encoded prompt>`. Generation happens on that page, not here.
