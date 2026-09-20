# Apps — contributor rules

This is a single static `index.html` (plus `favicon.svg`) listing a family of other apps.
It is a directory page, not an app in itself: keep it boring, fast, and dependency-free.

## Structure

- No build step, no framework, no package.json. One HTML file with inline `<style>` and
  `<script>`. Keep it that way; do not introduce a bundler or a JS framework for this page.
- The `APPS` object holds every card: `[name, liveURL, icon, description, accentColor]`,
  grouped by category. Each category also needs a matching `.grid` element with a
  `g-<key>` id and a `t-<key>`/`d-<key>` heading pair in the markup.
- Keep descriptions short (one sentence, two at most) and always link to the app's live
  URL, not a repo or a draft.

## Theme and language

- Three controls only: a language toggle, a theme toggle (light/dark, no "system"
  option), and a back-to-top button that appears after scrolling. Do not add more
  persistent chrome than that.
- English is the default language; Arabic is Modern Standard Arabic, simple and warm,
  never stiff or overly formal. All translatable chrome text lives in the `STR` object;
  every new string needs both an `en` and an `ar` entry, and the element it fills needs a
  stable `id` for `applyLang()` to update.
- Card names and descriptions are not translated by the language toggle — they are each
  app's own listing, already written in whatever language(s) that app uses, and several
  already show their own bilingual name. Cards render with `dir="ltr"` so mixed
  English/Arabic text keeps its natural reading order regardless of the page's direction.
  Do not remove that isolation; without it, mixed-direction sentences reorder oddly
  inside an RTL page.
- Both toggles persist to `localStorage` (`apps-theme`, `apps-lang`). The inline script at
  the top of `<head>` applies the stored choice before the stylesheet paints — keep that
  script tiny and synchronous so there is no flash of the wrong theme or direction.
- Respect `prefers-reduced-motion` for the card hover, the button transitions, and the
  back-to-top scroll (fall back to an instant jump).

## Delivery

- This is a static GitHub Pages site with no CI. Open the page and click through both
  languages and both themes before publishing a change to the chrome; a broken toggle is
  broken for every app in the collection, not just this page.
- Commit coherent changes with imperative subjects and no AI signatures or co-author
  trailers.
- Never put credentials or local settings into Git.
