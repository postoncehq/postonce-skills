---
name: content-calendar
description: Plan one to four weeks of social posts across every connected platform, draft each one natively, and schedule them all through PostOnce. Use when the user asks for a content calendar, a posting schedule, a week or month of content, content ideas to schedule, or to repurpose a blog, podcast, newsletter or video into a series of posts.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# Content calendar

Plan a realistic run of posts, write them, and schedule them with PostOnce so the user doesn't have to come back every day. A calendar the user can keep up with beats an ambitious one they abandon.

## Inputs

Get or infer, then confirm in one message:
- **Goal:** what the posts should lead to (followers, signups, sales, a launch, a page).
- **Source:** their topics, or material to mine (blog URLs, a transcript, a newsletter, product notes). Prefer real material over invented topics.
- **Platforms and accounts:** from `list_active_accounts`.
- **Cadence and length:** how many posts a week they can sustain, and 1 to 4 weeks.
- **Timezone** for every time you schedule.

## Build the plan

1. **Pillars:** 3 to 4 recurring themes from the goal and source (for example: how-to, behind the scenes, proof, opinion). Rotate them so no pillar runs twice in a row.
2. **Give each weekday a job.** One content type per day, the same on every platform, keeps the mix balanced. A simple default: Mon teach, Tue tip, Wed personality or humor, Thu how-to, Fri product or offer. Leave a day empty rather than posting filler.
3. **One idea per slot.** Each post carries one point. Break a long source into several atoms (a stat, a mistake, a step, a quote) and spread them across the weeks; never use the same atom twice in a week.
4. **Platform fit per slot:** video ideas go to TikTok, Reels, Shorts and Facebook Reels; carousels to Instagram, LinkedIn and Threads; short takes to X, Threads and Bluesky; keyword-rich pins to Pinterest. Skip platforms a slot doesn't suit rather than forcing it.
5. **Times:** use the audience's local weekday mornings or lunchtimes unless the user knows better. Space posts on the same account at least a few hours apart.

Show the plan as a table (date, time, pillar, idea, platforms, media needed) and get approval before writing.

## Write and schedule

- Write every post natively per platform, following the `post-everywhere` skill's limits and style table. Keep facts exactly as the source has them.
- List the media each slot needs. Slots that need an image or video the user doesn't have yet become drafts (`create_draft`), not scheduled posts.
- Schedule each ready slot with one `create_post` per time: `publish_at` as an ISO timestamp with the offset, one target per account, platform copy in `content_override`, settings like a YouTube title in `platform_options`.
- Save every returned post ID next to its slot.

## Hand back

Return the calendar with each slot's status: scheduled (with ID), draft (what's missing), or skipped (why). Remind the user that scheduled posts can be changed or cancelled before they go out with `update_post` or `cancel_post`, and that nothing is delivered until each post's status says published.

Need hooks or formats for the slots? Use the `hook-vault` and `viral-formats` skills.
