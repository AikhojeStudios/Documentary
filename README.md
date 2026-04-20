# field notes — an archive of looking

A single-page brutalist portfolio for personal/documentary work.
A project by [Aikhoje Studios](https://aikhojestudios.github.io/RealEstate/).

## Current state

Twenty-eight frames are sequenced and loaded, ready to deploy. Lagos (2017) and NC (ongoing) blended into a single stream — no chapters, no location grouping. The sequence is intentional: geography jumps, visual rhymes carry across, full-bleed moments are spaced out. Editing the order means editing the `frames` array (see below).

## Structure

```
/
├── index.html          → the site (everything lives here)
├── images/             → 28 photo files, sequenced 001–028
│   ├── 001.jpg
│   ├── 002.jpg
│   ├── ...
│   └── 028.jpg
└── README.md
```

Single HTML file + `images/` folder. No build step, no dependencies.

## Before you deploy — check the captions

The `date` values in the `frames` array are **placeholder approximations**. Some Lagos shots have real dates from filenames (`2017.03.17`, `2017.03.21`, `2017.03.25`); others are set to `2017.03` generically. NC dates are rough guesses. Walk through the array and correct any you care about. Or leave them — the captions read fine as approximate stamps.

`loc` values: `"lagos, ng"`, `"nc"`, `"nyc"`. Adjust if you want something more specific (e.g. `"makoko, ng"`, `"raleigh, nc"`).

## Adding / editing frames

Open `index.html` and find the `frames` array (~line 495). Each frame is one line:

```js
{ loc: "lagos, ng", date: "2017.03", src: "images/001.jpg", w: 8, off: 2, a: "a-23" },
```

- `loc` → location shown in caption
- `date` → YYYY.MM or YYYY.MM.DD (shown right-aligned)
- `src` → path to image file
- `w` → column width on 12-col grid: `4, 5, 6, 7, 8, 9, 10, 12`
- `off` → optional left offset column: `null` (flush left) or `1–6`
- `a` → aspect ratio class: `a-32` (3:2 horizontal), `a-23` (2:3 vertical), `a-11` (square), `a-43`, `a-34`, `a-169`, `a-219`

Frame numbers (`001`, `002`, ...) are auto-assigned from array position. Reorder the array to reorder the stream.

## Sequencing principles (for when you add new work)

- **Don't cluster by geography.** Every 3–4 frames, jump to somewhere else.
- **Pair frames by visual rhyme.** Silhouette next to silhouette. Portrait near portrait. Environment near environment.
- **Vary width and aspect.** Square → wide → vertical → full-bleed. The rhythm is the point.
- **Space out hero frames.** One full-bleed moment per ~7 frames. Stronger images are strongest when they have room to breathe.

## Deploy to GitHub Pages

```bash
cd /path/to/field-notes
git init
git add .
git commit -m "initial"
git branch -M main
git remote add origin https://github.com/aikhojestudios/<repo-name>.git
git push -u origin main
```

Then GitHub → Settings → Pages → source = `main` branch, `/` root.
Live at `https://aikhojestudios.github.io/<repo-name>/`.

Suggested repo names: `field-notes`, `stream`, `archive`, `looking`.

## Customization

**Statement** — edit the `<section class="statement">` block (~line 270).
**Colors** — CSS variables at top (~line 14): `--bg`, `--fg`, `--accent`.
**Footer** — the four `.col` blocks (~line 330).
**Font** — currently JetBrains Mono. Change the Google Fonts link + `--mono` variable.

## Notes

- Lightbox: click any frame → fullscreen. ESC closes. Arrow keys navigate.
- Bottom-right pill shows current frame number as you scroll.
- Subtle film grain overlay at ~3.5% opacity. Adjust on `body::before` (~line 46) or remove.
- Frame 010 is `.png` (the original file format of that scan). Everything else is `.jpg`.

## Image notes

- Sizes: the originals range from ~1300px (medium format scans) to 4700px (35mm). For faster page loads later, consider resizing longest edge to ~2000px at JPEG quality 82–85. Current files should work fine as-is.
- The TLR self-portrait (frame 027) sits near the end, paired with the Lagos sunset (026) and the NC lake (028). Closing triptych: *there / the one looking / here*.
