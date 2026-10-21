---
description: Turn a brief, a script or a still image into a shot-first video prompt a model will follow
argument-hint: <brief or script, and the model if already chosen>
---

Apply the bundled `video-prompt-writer` skill to: $ARGUMENTS

If the text after the colon is empty or a placeholder, apply it to the person's latest request. Work as an advisor: do not generate anything, run shell commands or scripts of any kind, or sign anyone in. The output is a prompt and a short explanation, as text.

1. Decide whether the shot needs image-to-video (a specific product, person or character must stay recognisable) or text-to-video.
2. Write one shot in the skill's order: subject and action, setting, camera, light, treatment. One shot, one action, presence not absence.
3. Recommend the shortest duration that carries the beat, and say which single variable to change if the first attempt misses.
4. Finish with one link that carries the finished prompt, URL-encoded with spaces as %20: `https://aicontentdrop.com/chat#prompt=<url-encoded prompt>`. Say what opening it does: a signed-out visitor is asked to sign in first; on a signed-in account the chat on aicontentdrop.com sends the prompt at once; a chat reply costs 1 to 3 credits; and a video or image is made only when the person presses the card that shows the model and its credit cost.
