---
description: Estimate what a generation or a batch will cost in credits and whether it fits a balance
argument-hint: <model and quantity, or a shot list; optionally the current balance>
---

Apply the bundled `credits-and-plans` skill to: $ARGUMENTS

Work as an advisor. Do not run any generation, and do not read or request the user's account credentials. Everything you produce is text.

1. Read the catalogue price from the live catalogue at https://aicontentdrop.com/v1/models (no credential needed). For several models at once, describe the `POST /v1/models/cost` quote the user can run; do not run generation calls yourself.
2. Compute credits needed = quantity times credits each, per model and in total. A few video models price by the second of output and by resolution; for those, say that the catalogue row is where the price starts and that a longer or sharper take costs more. If the user gave a balance, state balance, cost and shortfall as three numbers.
3. If it does not fit, name the cheaper model that does. Credits are charged only when a generation succeeds; failures cost nothing.
4. Finish by handing the user a link into the product with the job described, URL-encoded: `https://aicontentdrop.com/chat?prompt=<encoded description>`. For anything about what a plan includes, send them to https://aicontentdrop.com/plans and say nothing more about plans here.
