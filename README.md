# AI Learner's Permit

A free, fact-checked course for complete beginners on using AI assistants such as Claude, ChatGPT, and Gemini.

It is one self-contained `index.html` with no build step and no server code: 21 lessons in five units, hands-on demos (token splitter, next-word prediction, prompt builder, agent loop), a local prompt checker, prompt makeovers, a searchable prompt library, a 12-question final quiz, a printable cheat sheet, a glossary, and a sources page.

Progress, drafts, and theme are saved in the visitor's own browser (localStorage), under keys prefixed `ai-learners-permit:` because every project on the same github.io address shares one storage area. Drafts that look like they contain a card number, password, or ID number are never saved. A Content-Security-Policy tag blocks all outgoing connections. Nothing is sent to a server. The only external request is Google Fonts (Overpass, Overpass Mono, Source Serif 4); the page falls back to system fonts if that fails.

## Home screen icon

`apple-touch-icon.png` (180×180) is what iPhones and iPads use when someone taps Share, then Add to Home Screen. `manifest.json` with `icon-192.png` and `icon-512.png` does the same for Android and desktop browsers. After updating an icon, delete the old home screen shortcut and add it again; phones cache the old icon.

## Changing the name

Open `index.html`, search for `const APP_NAME` and `const APP_MARK` (the short text in the yellow badge), and change them. The wordmark and page titles update automatically. Also update the `<title>` and `<meta name="description">` tags near the top so search engines and link previews show the new name.

## Put it on GitHub Pages

1. Create a new public repository on GitHub.
2. Upload `index.html`, `manifest.json`, `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`, and this `README.md` to the root of the repository (on github.com: **Add file**, then **Upload files**). The `.nojekyll` file is optional for this site.
3. In the repository, open **Settings**, then **Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose `main` and `/ (root)`, and save.
5. After a minute or two the site is live at `https://<your-username>.github.io/<repository-name>/`.

## Editing content

All content lives in the `<script>` near the bottom of `index.html`:

- `SOURCES`: every cited link, keyed by a short id
- `LESSONS`: each lesson's title, summary, unit, minutes, `src` (source ids), and HTML
- `LIBRARY`, `MAKEOVERS`, `QUIZ`, `GLOSS`, `TF`: prompt library, makeovers, final quiz, glossary, true/false checks

## Checks to run after changes

- The avoid-ai-ui-tells audit at 390, 320 and 1280px. On 22 September 2026 all 15 main screens scored 0 at every width. The only remaining notes are table cells inside horizontally scrolling tables, which is intended.
- The web-app-security scan (`security-scan.py index.html`). Its HTML-sink findings were each reviewed: all user text passes through the `esc()` function, and injection payloads render as plain text.

## Keeping it accurate

Facts were checked on 22 September 2026. These will drift first and should be re-checked every few months:

- Lesson 4 (assistant table, prices), Lesson 5 (privacy setting names), Lesson 14 (feature comparison), Lesson 17 (harness examples), Lesson 21 (model names)
- Known upcoming change: OpenAI retires custom GPTs on 11 December 2026. Anthropic says Claude Sonnet 5.5 and Haiku 5.5 are coming "in the coming weeks."

When you change a fact, update its entry in `SOURCES` and the "Corrections found while checking" list on the sources page.
