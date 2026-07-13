# html-live-edit

*Hand a webpage to someone who doesn't code and let them actually change it.* 🩷

I kept building HTML mockups, handing them to people who don't write code, and then watching them try to edit the text by… just not being able to. So I made this.

It turns any static HTML page into something you can click and edit right in your browser — change the words, swap the images, stick a note on it, then download the clean version. No VSCode, no accounts, no build step, no "wait what's a terminal."

## What it actually does

You paste one file into your page and a little toolbar shows up in the corner:

- **Edit text** — click any text and type. Like a doc. The design stays put.
- **Swap image** — click a placeholder, pick a photo (it gets baked into the file so it travels with it).
- **Add note** — drop a sticky note anywhere, for all the "can we make this pop??" feedback.
- **Save copy** — keeps the editor on so you can keep fiddling later.
- **Export clean** — spits out the real production file with all the editing bits stripped back out.

## How to use it (no coding, promise)

1. Open your HTML file.
2. Copy everything in [`editor-kit.html`](editor-kit.html) and paste it right before `</body>`.
3. Open the page in a browser. Toolbar's in the corner. Go nuts.

That's the whole thing. It auto-tags the text and images when the page loads, so you don't have to mark anything up by hand.

### Or use it as a skill

If you live in Claude Code / Cursor / Codex, drop this folder into your skills folder (`~/.claude/skills/html-live-edit/`) and just say *"make this editable."* It'll do the pasting for you.

## The fine print (a.k.a. what it won't do)

- **Text and images only.** It won't move sections around or restyle things — that's still a real-code job.
- **Swapped images get embedded as base64**, so the file travels anywhere but gets a little chunky with big images. Totally fine for mockups; optimize before it goes live.
- **"Export clean" removes the editor, not your other work.**

## License

MIT. Use it, remix it, ship it. A credit is nice but I'm not going to come find you.

Made by Frances.
