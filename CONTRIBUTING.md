# Contributing a logo

Want to add a logo to the collection? Awesome — here's the whole process.

## 1. Add your SVG file

Drop your file in [`logos/`](./logos):

- **Naming:** lowercase, hyphenated — `my-brand.svg` (e.g. `google-wallet.svg`, not `GoogleWallet.svg`).
- **Variants:** the icon goes in `my-brand.svg`; if you also have a logotype (icon + name), add it as `my-brand-wordmark.svg`.
- **Valid standalone SVG:** must parse as XML (declare `xmlns`, and `xmlns:xlink` if you use `xlink:href`). No `<script>`, no raster images (`<image>`/base64), no external references.
- **Optimized:** run it through [SVGO](https://github.com/svg/svgo) or [SVGOMG](https://jakearchibald.github.io/svgomg/). Keep it under ~50 KB.
- **Check for duplicates:** search [`logos/`](./logos) (and think about aliases — `vscode` is already there as `visual-studio-code`).

## 2. Declare its category

Open [`scripts/gen.py`](./scripts/gen.py), find the `CONTRIBUTED LOGOS` section and add one line:

```python
add("dev", "my-brand")
```

Category keys: `ai` `lang` `fw` `dev` `cloud` `db` `design` `social` `pay` `prod` `shop` `media` `os` `mkt` `sec` `web` `corp`.

If you skip this step the logo lands in 📦 Others — it still works, just less discoverable.

## 3. Regenerate the catalog

```bash
python3 scripts/gen_site.py
```

This rebuilds `README.md`, the `categories/*.md` tables and `index.html` from the `logos/` folder. (Optional, maintainer-only: `python3 scripts/gen_og.py` regenerates the social image — needs Pillow + ImageMagick.)

## 4. Open a Pull Request

Commit your logo **and** the regenerated files, then open a PR with:

- [ ] `logos/my-brand.svg` (kebab-case, optimized, valid XML)
- [ ] Category declared in `scripts/gen.py`
- [ ] `README.md`, `categories/*.md` and `index.html` regenerated
- [ ] A link to the official brand source (press kit, brand page…)

## Legal note

Only submit logos you have the right to share — official brand assets or marks you own. All logos remain trademarks of their respective owners (see [LICENSE](./LICENSE)); inclusion here doesn't grant usage rights nor imply endorsement.
