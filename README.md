# html-live-edit

Turn any static HTML mockup into a no-code, click-to-edit page — edit text in place,
swap placeholder images for real ones, drop sticky notes, then export a clean
production file with the editing tools removed. No VSCode, no accounts, no build step.

Built as an [agent skill](SKILL.md) (works with Claude Code, Cursor, Codex), but the
core is a single self-contained file — `editor-kit.html` — you can paste into any page.

## Quick use (no agent needed)

1. Open your HTML file.
2. Paste the entire contents of [`editor-kit.html`](editor-kit.html) immediately before `</body>`.
3. Open the page in a browser. A small toolbar appears top-right:
   - **Edit text** — click any text and type; the design stays fixed.
   - **Swap image** — click a placeholder/image, pick a file (embedded as a data URI).
   - **Add note** — drop a draggable sticky note for feedback.
   - **Save copy** — download a working copy, editor kept.
   - **Export clean** — download the production file with all editing tools stripped out.

## Use as a skill

Drop this folder into `~/.claude/skills/html-live-edit/` (or your Cursor/Codex skills path).
The agent will inject the kit and hand you an editable page on request — e.g.
"make this editable" / "let me edit this in the browser."

## Notes & limits

- **Text and images only** — it does not move sections or restyle layout.
- Swapped images are embedded as base64, so the file is portable but grows with large images.
- "Export clean" removes the kit, not your other work.

## License

MIT — see [LICENSE](LICENSE).
