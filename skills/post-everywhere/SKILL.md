---
name: post-everywhere
description: Turn one idea, draft, blog post, link or video into a native post for every connected platform (LinkedIn, X, Threads, Bluesky, Facebook, Instagram, TikTok, YouTube, Pinterest) and publish or schedule them all in one PostOnce request. Use when the user asks to crosspost, repurpose, "post this everywhere", share something on all their socials, or adapt one post for several platforms.
metadata:
  author: PostOnce
  version: "0.1.0"
---

# Post everywhere

One source, one request, a native post on each platform. PostOnce publishes to every selected account from a single `create_post` call; each target gets its own copy through `content_override` and its own settings through `platform_options`. This skill decides what each platform should get, then sends it once.

## 1. Pick the destinations

Call `list_active_accounts` (or `list_accounts`) and read each account's `capabilities` and `media_requirements`. Use the accounts the user named; if they said "everywhere", propose every active account and let them remove any. Never guess IDs.

## 2. Find the one idea

Read the source (their text, a URL they gave you, a transcript). Pick the single most useful or surprising point; one post carries one idea. Keep facts, numbers and quotes exactly as the source has them. Don't invent results.

## 3. Write a native version per platform

Same idea, different shape. Start each version with its own first line; never paste one caption everywhere.

| Platform | Limit | What works |
| --- | --- | --- |
| LinkedIn | 3,000 | First 2 lines decide the "see more" tap. Short lines, a stance, one question at the end. Link in the body is fine; many prefer the first comment. |
| X | 280 (4,000 with Premium) | One sharp line. Numbers and specifics. Up to 4 images, 1 GIF or 1 video. |
| Threads | 500 | Conversational, a little looser than X. Up to 10 images or videos in a carousel. |
| Bluesky | 300 | Plain and direct. Links, #tags and @mentions become rich text. |
| Facebook Page | 63,206 | Warm, first person plural, a clear call to action. Up to 10 photos; video posts as a Reel. |
| Instagram | 2,200 | Needs media. Hook in line 1, value, then 3 to 5 specific hashtags. Carousel of 2 to 10, or one video as a Reel. |
| TikTok | 2,200 | Needs media: one video, or a photo slideshow. Search-style caption with the topic words people type; up to 5 hashtags. |
| YouTube | title 100, description 5,000 | Needs a video. Put the title in `platform_options.title`; a vertical video under 3 minutes becomes a Short. |
| Pinterest | title 100, description 500 | Needs an image or video. Keyword-led title and description, `link` to the source page. |

The server doesn't reject copy that's too long: it cuts it off. Count characters for each version before sending.

## 4. Match media to each destination

List what media the user has. For each target, check its media requirements. Platforms that need media and have none: drop them from this post and say so, or ask for an image or video. Don't mix images and video in one post where the platform takes one type; extras are dropped silently. For a local file, upload it with `create_upload_url` and `get_media` (see the `postonce` skill); the hosted server can't read file paths.

## 5. Confirm, then send once

Show the user a short table: platform, account, the exact text, media, time. Ask for one confirmation covering all of it. Then call `create_post` once:

```json
{
  "content": "<shared fallback text>",
  "publish_at": "2026-10-06T09:00:00-04:00",
  "media": [{"type": "image", "url": "<public URL>"}],
  "targets": [
    {"account_id": "<linkedin id>", "content_override": "<LinkedIn version>"},
    {"account_id": "<x id>", "content_override": "<X version>"},
    {"account_id": "<youtube id>", "content_override": "<description>", "platform_options": {"title": "<title>"}}
  ]
}
```

Omit `publish_at` to publish now. Staggered times need separate posts, one per time.

## 6. Report what actually happened

Call `get_post` with the returned ID and report each target on its own line: published with URL, scheduled, processing, or failed with the error. A created post isn't a delivered post. Retry only a failed target, using the recovery steps in the `postonce` skill; never re-send the whole post.

For deeper platform writing (carousels, scripts, threads, thumbnails), the per-platform plugins in `postoncehq/plugins` add skills for each network. For every future post to crosspost automatically, set up a workflow with the `postonce` skill instead.
