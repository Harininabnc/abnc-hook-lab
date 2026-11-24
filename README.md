# ABN°C Hook Lab

A one-page hook library for ABN°C TikTok creators (US market).

**80 visual hooks · 8 types · 4 products · one phone.**

![preview](preview.jpg)

---

## What it does

- **Pick the product you got** — the whole page re-fits to that bottle (names, product art, which hooks still apply).
- **80 hooks, 8 types** — camera, motion, reaction, texture, proof, story, props, edit.
- **"Your three"** — gives 3 random hooks plus a code, so every creator gets a different combination. The code persists, so they can screenshot it and send it back.
- **Every hook opens a mini shot recipe** — where the phone goes, what to say, which product, how hard it is.
- **Harin is reachable from every card** — sample, script help, page direction, shop link.

## Run it

No build step, no dependencies. Open `index.html` directly, or serve the folder:

```bash
python3 -m http.server 8000
```

## Publish with GitHub Pages

1. Push this folder to a repository (contents at the repo root).
2. **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`**.
3. The page appears at `https://<user>.github.io/<repo>/`.

Every path in `index.html` is relative, so it also works from a subfolder or a CDN.

## Structure

```
index.html                     the whole page (markup + CSS + JS + hook data)
preview.jpg                    screenshot used in this README
assets/
  favicon.svg
  abnc-wordmark.jpg            red wordmark, white background
  abnc-wordmark-white.png      white wordmark, transparent (dark sections)
  products/
    cica-bubble-serum.jpg
    glow-peeling-bubble-serum.jpg
    iced-green-tea-sheet-mask.jpg
    cica-soothing-cream.jpg
```

## Swap a product photo

Replace the file and keep the same name — nothing else to change.

- Portrait crop, roughly **3:4**, product centred, ~**900 px** tall.
- White or very light background works best (the tiles blend it away).
- `iced-green-tea-sheet-mask.jpg` is currently upscaled from a small original — swap it when a sharper shot is available.

## Edit the hooks

All 80 hooks live in one array inside `index.html`. Search for `var HOOKS`:

```js
var HOOKS = [
  ["01","A","Side-Turn Reveal","Side view. She turns to the lens.","This is what calm skin looks like.","all","turn",1],
  ...
];
```

| # | Field | Meaning |
|---|-------|---------|
| 0 | `"01"` | ID, shown on the card and in `?hook=01` links |
| 1 | `"A"` | Type: `A` camera · `B` motion · `C` reaction · `D` texture · `E` proof · `F` story · `G` props · `H` edit |
| 2 | title | English hook name |
| 3 | shot | where the phone goes / what happens |
| 4 | line | what the creator says on camera |
| 5 | product | `all`, `serum`, `lumi`, `mask`, `cream`, or `serum+lumi` |
| 6 | scene | illustration key (`turn`, `hand`, `macro`, `split`, …) |
| 7 | difficulty | `1` easy · `2` one prop · `3` needs an edit |

Deep links: `index.html?hook=21` opens that hook on load.

## Links

- Brand — <https://abnc.com/>
- TikTok Shop — <https://shop.tiktok.com/us/store/abnc-us-store/8656968372695634186>
- Samples, scripts, page direction — **Harin@abnc.com** · WhatsApp **+82 10-3965-7894**
