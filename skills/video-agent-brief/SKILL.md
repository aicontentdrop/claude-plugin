---
name: video-agent-brief
description: Prepare a brief for Drop, the AI Content Drop video agent, as text, before anyone opens the website. Covers the one-sentence goal and the facts the agent will ask for (product or subject, audience, purpose, length, aspect, platform, references and assets the person owns), what the agent does on the website (research, concepts, a plan, a price for every render that waits for the person's yes, a score, a verdict and the Director's notes on each finished piece), what the person decides and what they never need to do, and where the brief is pasted. Use when someone wants the video agent to handle a whole piece of work from one brief, a campaign or several videos from one idea, something in the style of a clip or a still they own, or wants to know what to prepare before they go to the website. Text advice only; it starts nothing, makes no video and spends nothing.
license: MIT
metadata:
  repository: https://github.com/aicontentdrop/claude-plugin
---

# Preparing a brief for Drop, the video agent

Drop is the AI Content Drop video agent. A person gives it one goal on the
website and it carries that goal through to finished pieces: it researches ads
that already work in the category, proposes concepts, writes a plan, prices
every render and waits for the person's yes before anything is made, then
judges what came back. Every step and every piece lands on a board the person
can open.

Nothing in this skill starts, follows or approves any of that. You prepare the
brief in words, say what will happen on the website, and hand the brief to the
person. You have no tool for the agent and need none. The person needs no key
and no credential in Claude, pays for nothing inside Claude, and signs in
nowhere but the website.

## 1. When this is the right skill

Use it when the person wants the whole job handled from one brief: a campaign,
a week of videos, several videos from one idea, an ad built on what
competitors run, something in the style of a clip or a still they own, or when
they ask what to prepare before they go to the website.

A single clip from one prompt is a smaller job: write the prompt with
`video-prompt-writer` and choose the model with `ai-video-model-picker`. A
short vertical drama is `short-drama-writer`.

## 2. Write the brief

The brief has two parts: the goal in one sentence, and the facts the agent
will ask for before it plans. A goal the agent can act on names the subject,
the length, the format and the purpose: "a 15-second vertical launch ad for a
ceramic pour-over kettle, three shots, no voiceover" rather than "a kettle
ad".

Then the facts. Fill in what the person told you, say which are missing, and
ask only for the missing ones that change the plan:

```
Goal: one sentence
Product or subject: what the video is about, named precisely
Audience: who it is for
Purpose: launch, retarget, teach, entertain
Length: seconds
Aspect: vertical, square or wide
Platform: where it will run
References: a clip or a still the person owns, whose look the piece follows
Assets: a product image, a presenter image, a logo
Avoid: anything the video must not show or say
```

A finished product ad needs a product image and a presenter image; say so,
and say that the agent asks for whatever it lacks. Keep the brief to what the
person knows: do not invent a product fact, a claim or an audience, and do not
choose a model. The agent chooses and prices each render on the website.

## 3. What happens on the website

Say this in plain words, so the person knows what they are walking into:

- The run moves through phases: intake, research, concept, plan, produce,
  done. Research, concepts, the plan and the board cost nothing.
- The agent may ask questions before it plans. The person answers them on the
  page; nobody answers for them.
- Every render is priced on the page before it runs: the step in plain words
  and the number of credits, charged only if the step succeeds. Nothing is
  made until the person says yes to that step.
- A clip or a still the person owns can be read into words first. Before a
  video is read, the page asks how the person holds the rights and offers
  three answers: it is my own work, I hold a licence, I have permission. State
  that question as the website's question; never answer it for the person,
  never suggest an answer, and never say a reference can be read without it.
  Reading costs no credits and is limited per day. The words it produces (the
  kind of reference, the shots, the cast, the look, any lines) go on the brief
  as "What I saw", and the person may correct them. The result recreates the
  look with an original cast; it never uses the reference's people, its lines
  or its brand.
- Each finished piece comes back with a score from 0 to 100, a verdict
  (accept, retry, switch, accepted with notes, or unscored) with its reasons,
  and the Director's notes, which name the direction rules the agent applied
  and why. A retry or a switch is an offer of another take, priced on its own
  and made only after the person's yes; a declined offer leaves the piece as
  it is. The score is the agent's opinion in words, never a reason to approve
  anything.
- Credits are charged only when a step succeeds. A failed or refused step
  costs nothing.

Quote no price. This skill holds no price for any step; the number is on the
page, for the exact step, before it runs.

## 4. What the person decides, and what they never need to do

The person decides the goal, the answers to the agent's questions, every yes
to a priced step, and whether to take an offered retry. They never need a key
or a credential in Claude, never pay for anything inside Claude, and never
have to sign in anywhere but the website.

If the person asks what a plan includes, send them to
<https://aicontentdrop.com/plans> and say nothing more about plans here.

## 5. Hand it over

End with the brief, ready to paste, and one link:
<https://aicontentdrop.com/make>. Say what opening it does: the page takes
nothing from the link, so the brief is pasted on the page; a signed-out
visitor is asked to sign in first; every render is priced there and waits for
the person's yes. Sign-in and every account question happen on that page, not
here.
