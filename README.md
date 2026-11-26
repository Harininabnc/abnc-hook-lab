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
  products/                    4 product shots (the "pick your product" step)
  hooks/                       80 storyboards, one per hook
    01-side-turn-reveal.webp
    02-top-down-hand.webp
    03-snap-push-in.webp
    …
```

## Swap a storyboard

Every hook has exactly one image: `assets/hooks/<id>-<slug>.webp` (e.g. `25-curtain-snap.webp`).

- **Keep the file name** — the page maps hook ID → file in the `HOOK_IMG` object, generated from this folder.
- **16:10, 1000 × 625 px**, WebP or JPEG, white background.
- Replace the file, reload, done. No other change needed.
- Missing image = empty card, so check the name matches the ID.

## Edit the hooks

All 80 hooks live in one array inside `index.html`. Search for `var HOOKS`:

```js
var HOOKS = [
  ["01","A","Side-Turn Reveal","Side view. She turns to the lens.","This is what calm skin looks like.","all",1],
  ...
];
```

| # | Field | Meaning |
|---|-------|---------|
| 0 | `"01"` | ID — also the image file prefix and the `?hook=01` link |
| 1 | `"A"` | Type: `A` camera · `B` motion · `C` reaction · `D` texture · `E` proof · `F` story · `G` props · `H` edit |
| 2 | title | English hook name (shown on the card) |
| 3 | shot | where the phone goes / what happens |
| 4 | line | what the creator says on camera |
| 5 | product | `all`, `serum`, `lumi`, `mask`, `cream`, or `serum+lumi` |
| 6 | difficulty | `1` easy · `2` one prop · `3` needs an edit |

If you change an ID, rename the image to match.

Deep links: `index.html?hook=21` opens that hook on load.

## Links

- Brand — <https://abnc.com/>
- TikTok Shop — <https://shop.tiktok.com/us/store/abnc-us-store/8656968372695634186>
- Samples, scripts, page direction — **Harin@abnc.com** · WhatsApp **+82 10-3965-7894**
