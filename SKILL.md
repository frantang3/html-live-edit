---
name: html-live-edit
description: >
  Turn any static HTML mockup or page into a no-code, click-to-edit document the
  user can change in their browser: edit text in place, swap placeholder images for
  real ones, drop sticky notes, then download the result. Use whenever someone wants
  to edit an HTML page without touching code, review a mockup visually, hand a page
  to a non-technical teammate for copy/image changes, or asks to "make this editable",
  "add edit mode", "let me edit this in the browser", "I want to change the text/images
  myself", "editable mockup", or "how do non-coders edit this". Also use to produce the
  clean production version afterward (strips the editing tools back out).
---

# html-live-edit

Injects a small, self-contained editor toolbar into an HTML page so a non-coder can
edit it directly in a browser, no VSCode, no accounts, no build tools. Then exports a
clean production file with the tools removed.

## When to use

- The user built or received an HTML mockup and wants to change the words or images
  themselves without editing code.
- You want to hand a page to a teammate (e.g. a CMO or founder) for copy/image review.
- The user asks any variant of "make this editable" / "let me edit this in the browser".
- The user wants the clean, tool-free version of a page they edited.

This is a **mockup / review-stage** tool. It is not for pages already live in a CMS.

## How to apply it

1. Read `editor-kit.html` (sits next to this file).
2. Paste its entire contents into the target HTML **immediately before `</body>`**.
   Do not otherwise modify the page.
3. Deliver the file to the user (send it, or commit it to their working branch).

That is the whole job. The kit auto-tags text and image placeholders when the page
loads, so it works on any HTML without you hand-marking elements.

### Optional pre-tagging (only if you want control)

- Force an element to be image-swappable: add `data-swap` to it.
- The kit already treats every `<img>` and every element with class `shot` as
  swappable, and treats headings, paragraphs, list items, table cells, and leaf
  text spans/divs as editable text.

## What the user gets (buttons, top-right)

- **Edit text** - click any text and type, like a doc; the design stays fixed.
- **Swap image** - click a grey placeholder or image, pick a file; it is embedded as a
  data URI so it travels inside the file.
- **Add note** - click anywhere to drop a draggable sticky note (for feedback/questions).
- **Save changes** - downloads `mockup-working.html`, keeps the editor so they can keep
  editing later. Also bound to **Cmd/Ctrl+S**, so the reflex save works instead of the
  browser's save (which would silently discard on-screen edits).
- **Download final** - downloads `mockup-final.html` with the toolbar, notes, and all
  editing attributes stripped out. This is the production-facing file.

Safety: the button flags unsaved edits with a dot, and closing the tab with unsaved
edits triggers a browser warning, so changes are hard to lose.

## Getting edits back

The user edits, clicks **Save changes** (to keep iterating) or **Download final** (when
done), and sends you the downloaded file. Commit it to their branch to stay in sync,
or read it to pull their copy/image changes forward.

## Important notes and limits

- **Text and images only.** The kit does not move sections, restyle, or change layout.
  Structural changes still go through you.
- **Swapped images are embedded as base64 data URIs.** Great for portability, but many
  large images make the file heavy. Fine for mockups; optimize before production.
- **"Download final" removes the kit, not other work.** For a Squarespace target you still
  need the separate step of inlining all styles and splitting into Code-Block-safe
  chunks (Squarespace strips `<style>`). Clean export is the prerequisite, not the whole
  conversion.
- **Fonts:** if the page links a webfont (e.g. Amiri via Google Fonts), keep the editor
  online so headlines render in the real face; offline it falls back to a system serif.
