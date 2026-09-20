# Apps

The home for a family of tiny, single-purpose apps. Each app does one thing well, keeps its data on the device, and is designed to feel calm and easy to use.

## The collection

Apps are grouped by theme: focus, calm, habits, sleep, health, family, faith, and learning. Open the [live collection](https://edriso.github.io/apps/) to browse them.

Previously published as Tiny Apps. The [old collection address](https://edriso.github.io/tiny-apps/) redirects here. For experiments and learning projects, see [Demo Apps](https://edriso.github.io/demo-apps/).

## Editing

This is a single static `index.html` with no build step. The cards are defined in the inline `APPS` object, grouped by category. Each entry is an object with a name, live URL, icon, an English and an Arabic description, and an accent color:

```js
{ n: 'App name', u: 'https://example.com/', i: '◉', en: 'A short description.', ar: 'وصف قصير.', c: '#8a93d8' }
```

Add an entry to an existing group, or add a new group key and matching `.grid` element in the page. Keep descriptions short in both languages, write the Arabic in simple, warm Modern Standard Arabic, and make sure every URL points to the app’s live site. Card names are not translated — they stay as authored (mostly English, some already bilingual, e.g. `Maeen · مَعين`) — and render with `dir="auto"` so each name keeps its own authored order regardless of the page's active language; only the description swaps between `en` and `ar`.

Adding a new group also means adding a `t-<key>`/`d-<key>` heading pair in the markup and a matching entry in both `STR.en.groups` and `STR.ar.groups` in the script, so the group title translates too.

## Theme and language

Three controls sit fixed in the corners: a language toggle and a theme toggle top-right, and a back-to-top button that appears bottom-right once you scroll. Both toggles remember the visitor's choice in `localStorage` (`apps-theme`, `apps-lang`) and a small inline script in `<head>` applies the stored choice before the stylesheet paints, so returning visitors never see a flash of the wrong theme or direction.

- **Theme**: light/dark only, no "system" option. CSS variables under `:root[data-theme='light']` override the dark defaults.
- **Language**: English by default; the toggle switches the page's own copy (heading, group titles, footer, control labels) *and* every card's description to Modern Standard Arabic, and flips `dir`/`lang` to `rtl`/`ar`, using Cairo instead of Fraunces/Hanken Grotesk. `renderCards(lang)` rebuilds the grids with the right-language description each time the toggle fires. All translatable page copy lives in the `STR` object in the script; add a key there (both `en` and `ar`) for any new piece of chrome text, and give its element a stable `id` for `applyLang()` to update.

## Deploy

The repository is a static GitHub Pages site. Push changes to `main`; GitHub builds and publishes the repository root automatically. There is no package installation or build command.

## License

MIT.
