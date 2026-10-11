---
name: chatcut-xiaohongshu-editor
description: Edit Chinese short-form talking-head videos in ChatCut while preserving an editable timeline. Use for speech cleanup, Chinese captions, consistent information graphics, picture-in-picture layouts, media and sound effects, asset relinking, visual QA, and platform-ready covers.
---

# ChatCut Short-Form Video Editor

Create a polished, editable short-form video. Treat the user's latest approved reference as the source of truth. Inspect actual timeline and asset properties before editing; never estimate values from memory.

## Hard rules

1. **Visual unification MUST be complete.** When the user says “统一,” inspect the master asset and update every relevant property—not only `fontSize`. Confirm `fontFamily`, fallback behavior, weight, line height, spacing, color, card geometry, and alignment.
2. **Units MUST remain explicit.** If the user gives a physical unit such as `16pt`, convert deliberately for the rendering environment and keep it separate from any existing display-text scale. Never silently mix unit systems.
3. **Completion MUST follow rendered QA.** Do not report completion until representative previews have been checked and any mismatch has been corrected.

## Workflow

1. Inspect the project, affected timeline items, captions, and Motion Graphic source.
2. Remove pauses, false starts, duplicate takes, fillers, and clear mistakes without changing meaning.
3. Review both sides of every cut and repair unnatural or disconnected joins.
4. Generate or repair Chinese captions after the speech edit. Keep captions clear of faces and graphics.
5. Add concise information cards, relevant media, and restrained sound effects only when they improve comprehension.
6. Relink unavailable assets and verify that they render.
7. Preserve cuts, captions, graphics, audio, and effects as separate editable items. Do not flatten the timeline.

## Visual consistency rules

Select one approved frame or card as the master. Extract its exact:

- font families and fallbacks
- title, subtitle, body, label, and numeric sizes
- weights, line heights, colors, spacing, padding, borders, radii, and alignment
- animation timing and easing

Map like to like: title-to-title, body-to-body, label-to-label, and statistic-to-statistic.

Confirm the chosen font actually renders. A font name in source code is not sufficient proof.

## Information graphics and media

- Turn spoken structure into short, readable questions, points, comparisons, numbers, or conclusions.
- Show promised lists or questions when the speaker introduces them.
- Match all added graphics and media to the approved visual system.
- Verify factual claims and show a compact source when appropriate.
- Prefer relevant screenshots or explanatory visuals over generic stock.
- Keep effects subtle and quieter than speech.

## Picture-in-picture

Keep related face windows in one consistent position and size. Add one border around the visible cropped image, not the uncropped source box.

```text
visible_top = top + height * cropTop
visible_height = height * (1 - cropTop - cropBottom)
visible_left = left + width * cropLeft
visible_width = width * (1 - cropLeft - cropRight)
```

Match the border's aspect ratio to this visible rectangle. Remove duplicate or misaligned guide frames and check the rendered result for blank bands.

## Cover

When requested, create a separate cover at the platform's exact ratio. Use a sharp, expressive real frame, preserve identity, derive styling from the finished video, keep copy short, respect safe zones, and verify spelling and thumbnail readability. Add an AI-editing badge only with user approval.

## Mandatory QA

Before reporting completion:

1. Preview every edited graphic and picture-in-picture interval.
2. Compare related cards side by side with the master.
3. Check fonts, semantic text sizes, wrapping, clipping, alignment, and caption collisions.
4. Check borders against the visible media and confirm no unintended blank space.
5. Review changed speech joins and user-reported timestamps.
6. Refresh captions when timeline edits require it.
7. Confirm every external asset renders.
8. Validate cover ratio, identity, copy, and thumbnail readability.

If a preview exposes a mismatch, revise and preview again. State exactly what changed and what was checked in the handoff.
