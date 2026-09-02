# PDF Editor & Signature Signer

Upload a PDF, sign it with a drawn or uploaded signature, drop in text boxes, delete/reorder pages, and merge multiple PDFs — real embedded PDF objects, entirely in your browser.

**Live:** <https://pdf-editor.slippylabs.com/>

## What it does

- Sign a PDF with a signature you draw in the page or upload as an image, then place it anywhere.
- Drop in text boxes at four sizes.
- Delete and reorder pages.
- Merge multiple PDFs into one.

## How it works

Edits are written as **real embedded PDF objects** — the signature becomes an image XObject, text becomes text operators in the content stream. The output is a proper PDF, not a stack of page rasters wearing a PDF extension, so it stays selectable, searchable and sharp when printed.

## Run it locally

A static site. No build step and no package manager — the two libraries it uses are
committed under `vendor/`:

```
git clone git@github.com:slippylabs/pdf-editor.slippylabs.com.git
cd pdf-editor.slippylabs.com
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Layout

| File | Purpose |
| --- | --- |
| `index.html` | The whole editor |
| `style.css` | Styling |
| `vendor/pdf-lib/` | pdf-lib — writes the edited PDF |
| `vendor/pdfjs/` | PDF.js — renders the page previews |
| `vendor-LICENSE-*.txt` | Upstream licences |

## Notes

This is the one tool here with third-party code, and it is **vendored, not loaded from a CDN**: [pdf-lib](https://github.com/Hopding/pdf-lib) writes the output and [PDF.js](https://github.com/mozilla/pdf.js) renders the preview, both served from this repo under `vendor/`. Their licences are in `vendor-LICENSE-pdf-lib.txt` and `vendor-LICENSE-pdfjs.txt`. Your PDF still never leaves the browser.

---

Part of [Slippy Labs](https://slippylabs.com). Every tool is indexed at
[projects.slippylabs.com](https://projects.slippylabs.com).
