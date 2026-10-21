# AI Content Drop for Claude

Plan AI video work in Claude before you make anything: choose an AI video model for a brief, write a video prompt a model will follow, turn a storyboard or shot list into one prompt per shot, work out what a clip or a batch will cost in credits, and write a short vertical drama from premise to episode outline. Four skills and five slash commands from AI Content Drop. Everything the plugin produces is text: it makes no images, video or audio, and when you want to make the video you follow a link to aicontentdrop.com.

## What you get

| Skill | Use it for |
| --- | --- |
| `ai-video-model-picker` | Choose a video model for a brief and price the whole job first. |
| `video-prompt-writer` | Turn a brief, script or still into a shot-first prompt, or fix one that missed. |
| `credits-and-plans` | Work out what a clip or a batch costs and whether a balance you state covers it. |
| `short-drama-writer` | Write a short vertical drama: premise, hooks, beats, shots and dialogue. |

The skills load automatically when a conversation matches their description. The commands invoke them on demand:

| Command | What it does |
| --- | --- |
| `/aicontentdrop:pick-model <brief>` | Recommends a model and works out the credit cost. |
| `/aicontentdrop:write-prompt <brief>` | Writes one shot-first video prompt. |
| `/aicontentdrop:estimate <model and quantity>` | Prices a generation or a batch. |
| `/aicontentdrop:plan-batch <storyboard>` | Turns a shot list into a priced shot plan. |
| `/aicontentdrop:drama-outline <premise>` | Writes a short-drama episode outline ready for Drama Studio. |

In Claude Code and Cowork you run a command by typing it; in claude.ai chat the commands load as skills and Claude applies them when your request fits.

Every command ends with a link to aicontentdrop.com that you choose whether to open: `https://aicontentdrop.com/chat#prompt=...` for a video or image, and `https://aicontentdrop.com/generate/drama` for a drama. If you are signed out, the chat asks you to sign in first. On a signed-in account the chat sends the drafted text at once; a chat reply costs 1 to 3 credits, and a video or image is made only when you press the card that shows the model and its credit cost.

## What it does not do

- It does not generate images, video or audio. It bundles no MCP server, no hook, no agent and no script, and it runs no commands.
- It does not sign you in, ask for a secret or read your account. Nothing in it needs one.
- It sends nothing about you anywhere. When Claude needs current prices it reads the public model catalogue at `https://aicontentdrop.com/v1/models?type=video` or `https://aicontentdrop.com/v1/models?type=image`, which holds no personal data; that read carries no credential and none of your conversation. Every other address in the plugin is a link you choose whether to open.
- It does not handle plans or payments. Questions about what a plan includes go to <https://aicontentdrop.com/plans>.

## Facts the skills rely on

- Most models cost one flat price per generation; a few video models price by the second of output and by resolution, and the skills name them. Credits for a video or an image are charged only when the generation succeeds; a chat reply on aicontentdrop.com is charged on its own.
- The model catalogue at `https://aicontentdrop.com/v1/models?type=video` and `https://aicontentdrop.com/v1/models?type=image` is public and is the source of truth; the skills tell Claude to read it rather than quote prices from memory.

## Every address in the plugin

- `https://aicontentdrop.com/v1/models?type=video` and `https://aicontentdrop.com/v1/models?type=image`: the public model catalogue, the only addresses Claude reads.
- `https://aicontentdrop.com/chat#prompt=...`: a link you choose whether to open. The drafted text rides after the `#`, which your browser leaves out of the page request; the chat page sends it to the chat only on a signed-in account.
- `https://aicontentdrop.com/generate/drama`: Drama Studio, where you paste a drama outline.
- `https://aicontentdrop.com/plans`: what each plan includes.
- `https://aicontentdrop.com/privacy-policy`: the privacy policy.
- `https://aicontentdrop.com`: the publisher's site, named in the manifest.
- `https://github.com/aicontentdrop/claude-plugin`: this repository.

## Install

See [SETUP.md](./SETUP.md). The short version:

```bash
git clone https://github.com/aicontentdrop/claude-plugin
claude --plugin-dir claude-plugin
```

## Source

The skills are advisory editions of AI Content Drop's own agent skills, rewritten for this plugin. A guard test in the source repository fails if a skill or command file contains a credential, a shell command, a generation step or an address outside the list above. README and SETUP do contain shell commands: the lines that install and check the plugin, for you to run. MIT licensed. Support: <support@aicontentdrop.com>. Privacy policy: <https://aicontentdrop.com/privacy-policy>.
