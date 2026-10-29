# Setup

## From the plugin directory

In claude.ai or the Claude desktop app, open Customize, then Plugins, then Discover, search for **AI Content Drop**, and add it. In Claude Code, run `/plugin directory` (version 2.1.287 or later), search for **AI Content Drop**, and install it; a plugin you add on claude.ai also reaches Claude Code as a synced plugin. The commands appear as `/aicontentdrop:pick-model`, `/aicontentdrop:write-prompt`, `/aicontentdrop:estimate`, `/aicontentdrop:plan-batch`, `/aicontentdrop:drama-outline`, `/aicontentdrop:drop` and `/aicontentdrop:recreate`. In claude.ai chat the commands load as skills, and Claude applies them when your request fits.

## From a local clone

Load the plugin for one session without installing anything:

```bash
git clone https://github.com/aicontentdrop/claude-plugin
claude --plugin-dir claude-plugin
```

Check the manifest before loading it:

```bash
claude plugin validate --strict claude-plugin
```

## Credentials

None. Nothing in the plugin asks you to sign in, asks for a secret or reads one from your machine, and it stores nothing. Signing in happens only on aicontentdrop.com, and only if you open one of the links the plugin prints.

## What the plugin reads and sends

- It reads what you type in the conversation.
- When Claude needs current prices, it reads the public model catalogue at `https://aicontentdrop.com/v1/models?type=video` or `https://aicontentdrop.com/v1/models?type=image`. The catalogue holds no personal data, and the read carries no credential and none of your conversation.
- It sends nothing else anywhere. The other addresses in it are links you choose whether to open. `https://aicontentdrop.com/chat#prompt=...` carries the prompt Claude drafted after the `#`, which your browser leaves out of the page request. If you are signed out, the chat asks you to sign in first; on a signed-in account the chat page sends the prompt to the chat at once, and a chat reply costs 1 to 3 credits. `https://aicontentdrop.com/generate/drama` opens Drama Studio. `https://aicontentdrop.com/make` opens the Drop page for the video agent; it takes nothing from the link, so you paste the brief on the page. If you are signed out, the Drop page asks you to sign in first; every render is priced there and waits for your yes. <https://aicontentdrop.com/plans> describes the plans.

## What the plugin does not do

- It does not generate images, video or audio. Generation happens on aicontentdrop.com after you follow a link, and only when you press a card there that shows the model and its credit cost, or say yes to a render the Drop page has priced.
- It bundles no MCP server, no hooks, no agents and no scripts, and it runs no commands.
- It does not start, follow or approve a video agent run, and it quotes no price for one.
- It does not display, compare or change plans. For that, the commands point to <https://aicontentdrop.com/plans>.

## Try it

```text
/aicontentdrop:pick-model a 5-second vertical clip of a matcha latte being poured, product-ad style
/aicontentdrop:write-prompt turn a product photo of a running shoe into a short cinematic clip
/aicontentdrop:estimate 20 shots on kling_3_0, balance 300 credits
/aicontentdrop:plan-batch <paste a shot list>
/aicontentdrop:drama-outline a disowned heiress returns as the new owner of her family's hotel, 3 episodes of 30 seconds
/aicontentdrop:drop a 15-second vertical launch ad for a ceramic pour-over kettle, three shots, no voiceover
/aicontentdrop:recreate <a link to a clip you own> as a 10-second vertical ad for a desk lamp
```

## Updating

The plugin follows this repository's default branch, and each release raises `version` in `.claude-plugin/plugin.json`.
