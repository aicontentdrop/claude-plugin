# AI Content Drop for Claude Code

Plan AI video and image generations from Claude Code: pick the right AI video model for a brief, write a video prompt a model will follow, turn a product photo or storyboard into a shot list, estimate the credit cost before anything runs, and write a short vertical drama ready for Drama Studio. Five skills and five slash commands from AI Content Drop, the AI video and image generation platform. The plugin is text advice only: it generates no images, video or audio, and generation happens on aicontentdrop.com after you follow a link.

## What you get

| Skill | Use it for |
| --- | --- |
| `ai-video-model-picker` | Choose a video model for a brief and estimate the whole job first. |
| `video-prompt-writer` | Turn a brief, script or still into a shot-first prompt. |
| `credits-and-plans` | Explain what a generation costs and whether it fits a balance. |
| `api-error-handling` | Read an API failure correctly and decide whether to retry. |
| `short-drama-writer` | Write a short vertical drama: premise, hooks, beats, shots and dialogue. |

The skills load automatically when a conversation matches their description. The commands invoke them on demand:

| Command | What it does |
| --- | --- |
| `/aicontentdrop:pick-model <brief>` | Recommends a model and estimates the credit cost. |
| `/aicontentdrop:write-prompt <brief>` | Writes one shot-first video prompt. |
| `/aicontentdrop:estimate <model and quantity>` | Prices a generation or a batch. |
| `/aicontentdrop:plan-batch <storyboard>` | Turns a shot list into a priced, resumable plan. |
| `/aicontentdrop:drama-outline <premise>` | Writes a short-drama episode outline ready for Drama Studio. |

Every command ends with a link into the product, so the next step is one click: `https://aicontentdrop.com/chat?prompt=...` for a video or image, and `https://aicontentdrop.com/generate/drama` for a drama.

## What it does not do

- It does not generate media. There is no MCP server, no hook and no sub-agent in this plugin.
- It does not sign you in or read your account. No credential is needed to install or use it.
- It does not handle plans or billing. Questions about what a plan includes go to <https://aicontentdrop.com/plans>.

## Facts the skills rely on

- Most models cost one flat price per generation; a few video models price by the second of output and by resolution. Credits are charged only when a generation succeeds.
- The model catalogue and cost estimates at <https://aicontentdrop.com/v1/models> need no credential and are the source of truth; the skills tell Claude to read them rather than quote from memory.

## Install

See [SETUP.md](./SETUP.md). The short version:

```bash
git clone https://github.com/aicontentdrop/claude-plugin
claude --plugin-dir claude-plugin
```

## Source

The skills are exported byte for byte from the [`aicontentdrop`](https://www.npmjs.com/package/aicontentdrop) package by `scripts/build-claude-plugin.mjs`, and a test fails the build if the two copies drift. MIT licensed. Support: <support@aicontentdrop.com>.
