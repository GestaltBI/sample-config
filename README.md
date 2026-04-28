# sample-config

Sample configuration for [`GestaltBI/gestaltbi-core`](https://github.com/GestaltBI/gestaltbi-core).

Visit the live demo:

> https://gestaltbi.github.io/gestaltbi-core/gh/GestaltBI/sample-config

The client at `gestaltbi-core` reads the files in this repo via jsDelivr (`https://cdn.jsdelivr.net/gh/GestaltBI/sample-config/`) and renders the full visualization stack — maps, charts, tables, glossary — without anyone needing to rebuild or redeploy the app.

## Repo contract

A GestaltBI config repo has six files at the root:

| File | What it does |
|---|---|
| `data.csv` | The dataset to visualize. Comma-separated, header row required. |
| `mapping.json` | Renames raw CSV columns to the canonical names used by `structure.json`. |
| `structure.json` | Column metadata: types, tags, aggregation rules. The tags drive everything — which columns are dimensions, dates, geo coordinates, currencies, aggregable measures. |
| `processing.json` | The process graph (`@gestaltbi/stream` config). Named processes that wire ops together — clean, format, geocode, geojsonify, aggregate, filter, etc. |
| `modes.json` | The list of analysis modes the left sidebar shows (long, sync, point, …). Each entry references a process by name plus an MDI icon. |
| `it.json` | Column-label dictionary: human-readable labels for each column code, used by the legend, filter, and chart components. |

UI translations (`en.json`, `it.json` for app strings) live inside the client app, not here.

## Pinning a version

To pin to a specific commit / tag / branch:

```
https://gestaltbi.github.io/gestaltbi-core/gh/GestaltBI/sample-config/<ref>
```

Example with a tag:

```
https://gestaltbi.github.io/gestaltbi-core/gh/GestaltBI/sample-config/v1.0.0
```

jsDelivr resolves `<ref>` against your default branch, a tag, or a commit SHA — same as on the GitHub URL bar.

## Authoring your own

1. Fork this repo (or start fresh with the same six files).
2. Replace `data.csv` with your dataset.
3. Update `mapping.json` to map your CSV columns to canonical names.
4. Adjust `structure.json` tags so the right columns flow through the right ops.
5. Tweak `modes.json` to expose the analyses you care about.
6. Push to GitHub.
7. Share `https://gestaltbi.github.io/gestaltbi-core/gh/<your-org>/<your-repo>`.

## License

The files in this repo follow the MIT license of `gestaltbi-core`.
