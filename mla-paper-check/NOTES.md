# MLA Paper Check: build notes

Built 8 October 2026 from `mla-check-build-brief.md`. Decisions Lynne made before the build:

| Question | Answer |
|---|---|
| Look | Editor's desk: cream paper on a dark desk, graphite ink, highlighter spotlight, red-pencil rulers |
| Hosting | Canvas Files. Upload `MLA_Paper_Check.html`, then embed `/files/<id>/preview` in an iframe |
| Completion | Ungraded practice. No copy box |
| Sample heading | Neutral placeholders (Student Name / Teacher Name / Course Name), header reads "Last Name 1" |
| House rules | None beyond MLA |
| Bonus round | Built now: a second paper with six planted mistakes and three decoys |

## Google Docs menu paths: what to confirm in a live doc

Google's help site and the current how-to guides were unreachable from the build sandbox, so these paths come from the brief plus the 2026 guides' search summaries. Each one is a single line in the `STOPS` object at the top of the script.

| Stop | Path used in the page | Confidence |
|---|---|---|
| Running header | **Insert → Page numbers → top-right tile (numbers every page)** | Verify. Guides from 2026 agree on `Insert → Page numbers` with four preset tiles plus `More options`. Older guides show `Insert → Headers & footers → Page numbers` or `Insert → Header & page number`. If live Docs differs, change `pick: "Page numbers"` in the `header` stop and the `Insert` list in `MENUS`. |
| Margins | File → Page setup → Pages tab → Top/Bottom/Left/Right = 1 → OK | Stable |
| Double spacing | Format → Line & paragraph spacing → Double; then → Custom spacing → Before 0, After 0 → Apply | Stable |
| Indent | Format → Align & indent → Indentation options → Special indent: First line, 0.5 → Apply | Stable |
| Font / size | Toolbar font box and size box | Stable |
| Title | Ctrl+Shift+E to center, Ctrl+Shift+L to left-align | Stable |

The mock editor's menu lists (`MENUS`) are abbreviated to the items that matter. Long menus show a window of nine items around the one being picked.

## What differs from the brief

- **No GSAP.** The page is a stepped tour, not a scroll narrative, so every effect is plain CSS transitions and keyframes. Nothing loads from a CDN except the two Google Fonts. It works with the CDN blocked.
- **Phone leader line.** On one-column layouts the leader line from the bubble to the target draws only when the target is within about 300px of the bubble. Further than that it crossed the whole paper and looked like a mistake. The spotlight still marks the target.
- **Windows / Mac toggle.** The walkthrough header has a two-button switch. Step text uses a `{{mod}}` token that renders as Ctrl or Cmd, and the key chip in the mock editor follows it. It defaults to Windows and remembers the choice in `localStorage` when allowed.
- **Double spacing stop** spotlights the whole text area, with 2.0 brackets on the heading and body and a "whole page" bracket down the side, so nobody double-spaces only the paragraphs.
- **Zoom in.** A toggle under the paper widens it to 760px inside a scrollable frame and scrolls to the current target. Useful on phones where to-scale 12-point text is about 7px.

## Adding stops later (Works Cited, annotated bibliography)

Append an object to the end of `STOPS` with `id`, `label`, `short`, `rule`, `target` (a selector inside `#paper`), `mark` (one of the drawing routines in `drawMarks`, or a new one), `docsTitle`, `steps`, `watch`, and optional `video`. The rail, finish list, counts, and saved progress all read the array length. A second sample page would need its own `.paper` block and a `target` pointing into it.

## Narration

`NARRATION` at the top of the script holds one URL per key (`intro`, `finish`, and each stop id). Fill a URL and an audio player appears in that stop's bubble. `MLA_Check_Narration_Script.txt` has the words.

## Canvas Studio video

Each stop has a `video: ""` slot. Paste a Canvas Studio embed URL and a 16:9 player appears under the walkthrough steps for that stop.

## Tested

- All 8 stops in order; Not yet → walkthrough → Done, recheck returns to the same stop.
- 860px iframe width and 375px phone width, no horizontal page scroll (zoom mode scrolls inside its own frame).
- `localStorage` throwing on access: no errors, page runs without saving.
- `prefers-reduced-motion`: spotlight, rulers, bubble, and cursor jump to their end states.
- Keyboard only: Tab + Enter completes the whole tour. Escape closes the walkthrough and returns focus to the bubble.
- Bonus round: six finds, decoys answer "is fine, look again", Show what's left reveals the rest.
- No Works Cited or annotation content.
