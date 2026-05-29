# ssfimages — Sneha Sammilana Foundation event media

This repository contains **only event media** for the foundation website. It is
served — for free — through the [Statically](https://statically.io) CDN. The
website discovers events automatically from this folder structure, so **no code
changes are ever required** to publish a new event.

```
GitHub repo (this)  ->  Statically CDN  ->  Next.js website
```

## Folder structure

Every event is one folder under `events/`. The folder name is the single source
of truth — it encodes the event number, title, and (optionally) date.

```
events/
  E01 Donated 2 Bicycles/
    img_001.webp
    img_002.webp
    img_003.webp
  E02 School Material Distribution/
    img_001.webp
    img_002.webp
```

### Folder naming

```
E<number> <Event Title> [optional date]
```

- `E01`, `E02`, ... — the event number (used for ordering, newest first).
- `<Event Title>` — free text; becomes the page title and slug.
- Optional trailing date like `26-Dec-2015` or `2015-12-26` is detected and
  shown as the event date.

Examples:

```
E26 Distribution of Groceries at Sipani Seva Sandan on 03-Jan-2021
E27 School Material Distribution
```

### Image naming

Use predictable, systematic names. The **first** image (after a natural sort)
becomes the **cover image**; the rest become the gallery.

```
img_001.webp
img_002.webp
img_003.webp
```

- Prefer **WebP** for size. JPG/PNG/GIF/AVIF/SVG also work.
- Keep numbering zero-padded so the order is predictable.

### Optional description

Add a `description.txt` or `description.md` inside an event folder. Blank lines
separate paragraphs, which render on the event detail page.

## Adding a new event (the entire workflow)

1. Compress images to WebP.
2. Create a folder: `events/E27 Event Name/`
3. Add images: `img_001.webp`, `img_002.webp`, ...
4. Commit & push this repo.
5. Redeploy the website (or wait for the next deploy).

Done. The website picks it up automatically — no manual paths, no registration.

> Note: the CDN caches content, so a redeploy of the website (which regenerates
> the manifest from the latest repo state) makes new events appear reliably.
