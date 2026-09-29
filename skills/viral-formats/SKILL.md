---
name: viral-formats
description: Pick and script a proven short-form video format from 49 formats ranked by how consistently they go viral on TikTok, Instagram Reels and YouTube Shorts, each with its hook, structure, ending and a real example. Use when the user asks for video ideas, a viral video format, what to film, a Reel, TikTok or Shorts idea, or a format that works on every platform.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# Viral formats

`references/formats.json` holds 49 short-form formats, ranked by the number of examples with over a million views, how many platforms they work on, and median views. Browse them with videos at [postonce.to/free/viral-formats](https://postonce.to/free/viral-formats).

Each entry has: `rank`, `name`, `structure`, `hook`, `middle`, `ending`, `length`, `effort` (`phone-only`, `needs editing`, `needs other people`), `works_on_every_platform`, `adapt` (how to change it per platform), `good_for` (niches) and `example` (a real video).

## Choose a format

Ask, or infer, three things: the user's niche, how much effort they can put in, and where they post. Then shortlist 3 formats:
- Prefer `works_on_every_platform: true` when they post to several platforms; one video can then go everywhere unchanged.
- Match `effort`: someone filming alone on a phone should get `phone-only` formats.
- Match `good_for` to their niche, or pick formats marked for any category.
- Lower rank numbers are more proven; don't ignore a strong fit further down.

Share each option's name, one line on why it fits, and its `example` link so they can watch it first.

## Script the chosen format

Write a shot-by-shot script in the format's own structure:
1. **Hook (0 to 2 s):** the spoken line and the on-screen text, using the format's `hook` pattern. The `hook-vault` skill can supply stronger openers.
2. **Middle:** each beat with what's said, what's shown, and on-screen text, following `middle`.
3. **Ending:** following `ending`, plus one call to action that fits (follow, comment, save).
4. **Specs:** length from `length`, vertical 9:16, captions on.
5. **Per platform:** apply `adapt` (for example, a carousel version for Instagram and LinkedIn, or a still for X).

Use only facts the user gives you. No invented numbers or results.

## Publish

Once the video exists, write each platform's caption with the `post-everywhere` skill and publish or schedule it through PostOnce: TikTok, Reels, Shorts and Facebook Reels in one request.
