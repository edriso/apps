# Apps

The home for a family of tiny, single-purpose apps. Each app does one thing well, keeps its data on the device, and is designed to feel calm and easy to use.

## The collection

Apps are grouped by theme: focus, calm, habits, sleep, health, family, faith, and learning. Open the [live collection](https://edriso.github.io/apps/) to browse them.

Previously published as Tiny Apps. The [old collection address](https://edriso.github.io/tiny-apps/) redirects here. For experiments and learning projects, see [Demo Apps](https://edriso.github.io/demo-apps/).

## Editing

This is a single static `index.html` with no build step. The cards are defined in the inline `APPS` object, grouped by category. Each entry contains a name, live URL, icon, description, and accent color:

```js
['App name', 'https://example.com/', '◉', 'A short description.', '#8a93d8']
```

Add an entry to an existing group, or add a new group key and matching `.grid` element in the page. Keep descriptions short and make sure every URL points to the app’s live site.

## Deploy

The repository is a static GitHub Pages site. Push changes to `main`; GitHub builds and publishes the repository root automatically. There is no package installation or build command.

## License

MIT.
