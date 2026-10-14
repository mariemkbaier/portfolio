# Mariem Kbaier — Portfolio

A single-page portfolio site. No build step, no dependencies. Open `index.html` in a browser to preview it locally.

---

## 1. Add your photo and demos

Put these files inside the `assets` folder, named exactly like this:

| File | Where it shows up |
|---|---|
| `assets/mariem.jpg` | Your photo, next to your name at the top |

A square crop works best — anything else gets centre-cropped to a square. Until you add it, the frame shows your initials.

Then the two demos:

| File | Where it shows up |
|---|---|
| `assets/tta-demo.mp4` | Test-Time Adaptation project |
| `assets/llm-demo.mp4` | LLM assistant project |

Optional still images shown before the video starts playing:

| File | Where it shows up |
|---|---|
| `assets/tta-poster.jpg` | Test-Time Adaptation project |
| `assets/llm-poster.jpg` | LLM assistant project |

**If a file isn't there yet, nothing breaks.** The page shows a neat "Demo goes here" panel with the filename it's waiting for. Add the file later and it appears automatically.

**Using a screenshot instead of a video?** Name it `assets/tta-demo.png`, then find this line in `index.html` (search for `tta-demo`) and change two things — the filename and `data-type="video"` to `data-type="image"`:

```html
<figure class="media" data-media="assets/tta-demo.png" data-type="image" ...>
```

**Video tips:** MP4 (H.264), under 20 MB each, 10–20 seconds, no audio needed — the videos autoplay silently on loop. GitHub rejects files over 100 MB.

---

## 2. It's already on GitHub

The repo is live at **https://github.com/mariemkbaier/portfolio**, and the site is
published at:

```
https://mariemkbaier.github.io/portfolio/
```

If the link 404s, GitHub Pages just needs turning on once: repo **Settings** →
**Pages** → set *Source* to `Deploy from a branch`, *Branch* to `main`, folder
`/ (root)` → **Save**. Give it a minute and refresh.

### Updating it later

Easiest way, no git needed: open the repo, click **Add file → Upload files**,
drag your images and videos into the `assets` folder, click **Commit changes**.
To edit text, open `index.html`, click the pencil icon, edit, commit.

From the command line:

```bash
git clone https://github.com/mariemkbaier/portfolio.git
cd portfolio
# ...make your changes, drop files into assets/...
git add .
git commit -m "Add demo videos"
git push
```

Changes go live in under a minute — hard-refresh your browser
(Ctrl/Cmd + Shift + R) if you still see the old version.

---

## 3. Things you'll probably want to edit

All in `index.html`, all easy to find with Ctrl+F:

- **Your name, title, and location at the top** — search for `Mariem Kbaier`.
- **Contact details** — search for `kbaiermeryem@gmail.com` (appears twice) and `kbaier-mariem`.
- **The four numbers under the hero** — search for `<div class="num">`.
- **Colors** — the `:root` block at the top of the file. `--indigo` is the accent, `--amber` is the secondary.
- **Adding a resume download** — drop `Mariem_Kbaier_Resume.pdf` into `assets/`, then in the hero add a third button next to the other two:
  ```html
  <a class="btn ghost" href="assets/Mariem_Kbaier_Resume.pdf" target="_blank">Resume</a>
  ```

---

## Notes

- Fonts load from Google Fonts, so the page needs an internet connection to look right. Offline, it falls back to system fonts and still works.
- The animated chart in the hero shows what test-time adaptation does: a decision boundary drifting off target as data shifts, versus one that adapts. It's drawn in code — nothing to upload.
- Respects "reduce motion" system settings and works down to phone width.
