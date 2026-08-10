# FL-IT

Command reference for day-to-day FL work — WHS App, SSH, and TC27.

**→ https://akashsasikumar47.github.io/FL-IT/**

## How it works

`index.html` reads the markdown files at runtime and renders them as tabs. There is no build step and no dependencies — the `.md` files are the single source of truth.

| File         | Tab     |
| ------------ | ------- |
| `WHS-APP.md` | WHS App |
| `SSH.md`     | SSH     |
| `TC27.md`    | TC27    |

Click any command line to copy it. Barcodes in the Test Barcodes table are click-to-copy too. Press `/` to filter.

## Updating

Edit a `.md` file and push — the site picks it up, nothing to rebuild.

To add a fourth doc, drop the `.md` in and add one line to the `DOCS` array near the top of the `<script>` in `index.html`.

## Local preview

Browsers block `fetch()` on `file://`, so serve the folder:

```bash
python3 -m http.server 8080
```
