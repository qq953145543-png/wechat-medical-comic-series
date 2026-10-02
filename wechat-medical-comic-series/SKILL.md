---
name: wechat-medical-comic-series
description: Create a five-page Chinese WeChat medical-education comic series from a title, with a fixed nurse character, varied tall-poster layouts, verified medical copy, and a local one-click rich-text preview. Use for requests such as “根据标题生成公众号医学科普长图” or “做 5 张可拼接医学漫画长图”.
---

# WeChat Medical Comic Series

Turn one Chinese medical-education title into a five-page portrait comic series for a WeChat article. Each page is 821×1916 px. The output includes five images, one approximately 300-Chinese-character summary, and a local HTML preview that copies rich text and embedded images for manual paste into the WeChat Official Account editor.

## Inputs

- Required: a title or topic.
- Optional: nurse and patient reference images. When supplied, preserve the characters’ facial features, hairstyle, uniform/clothing, and proportions throughout.
- Default roles if no references are supplied: a warm female nurse educator in purple scrubs, white cap, black-rim glasses, low bun, and a young adult female patient in a pink top.
- Default region for medical guidance: mainland China. State this outside the images when it matters.

## Visual system

Use `assets/layout-01.png` through `assets/layout-05.png` as the layout and visual-system references. Preserve their warm cream background, navy headline type, coral-red emphasis, pale-blue outlines, rounded modules, and polished chibi medical-comic rendering.

Do not use the same layout on every page. Map the topic across these five distinct page structures:

1. Question-led opening: large headline, lifestyle scene, a clear conclusion panel, and short timeline.
2. Side-by-side contrast: two scenes, cause or technique arrows, then a repeated-progress strip.
3. Three-scene progression: time or behavior sequence, short reminder strips, and a central risk/solution hub.
4. Population or misconception page: portrait row or categories, then a wrong-question/right-question comparison.
5. Safety closing: central problem or symptom vignette, surrounding callouts, action list, and a calm final takeaway.

The sequence must teach progressively rather than force identical content into each layout. Retain enough breathing room for Chinese text. Do not add watermarks, QR codes, English filler, or unreadable small text.

## Medical and copy workflow

1. Verify time-sensitive claims against current Chinese health authority, professional-society guidance, or primary research before generating. Do not present a single study as settled consensus.
2. Plan the five page titles and all in-image copy first. Keep claims patient-friendly, qualified, and suitable for general education. Do not give individualized diagnosis or tell readers to start, stop, or adjust prescription medication.
3. Generate one image per page with ImageGen, passing the matching layout asset and any supplied character references. Inspect every image for Chinese text, units, anatomy, and character continuity; regenerate a page with medically meaningful or illegible errors.
4. Save the five final images as `01.png`–`05.png` in a user-facing output directory.
5. Write one 260–340 Chinese-character summary paragraph before the image sequence. It should complement the images, include safe action guidance, and distinguish routine follow-up from emergency care.
6. Build a standalone local preview with all five images embedded as `data:` URLs. The preview needs a `复制排版正文（含图片）` button that remains disabled until all images decode.
7. For copied HTML, force every image wrapper to `margin:0; padding:0; line-height:0;` and every image to block display with zero margins, zero border, and zero border radius. This prevents WeChat from adding blank gaps between consecutive images.

## Handoff

Report the image dimensions, article/preview paths, and the markdown-image, HTML-image, and embedded-image counts. Never log in to WeChat, publish, or claim a draft was saved. Tell the learner to open the preview, click the copy button, paste into the WeChat editor, confirm the images remain gapless, then manually save the draft.
