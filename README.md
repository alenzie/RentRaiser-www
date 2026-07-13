# RENT RAISER — Line City Properties

The marketing site for **RENT RAISER**, an idle landlord-tycoon game set in Line City.

It is written as a property brochure that believes its own copy, and it is a working
idle game in its own right: the money counter starts climbing the moment the page
loads, every card and character on the page pays out when you click it, and the wallet
follows you down the page collecting what you knock loose. The site's fine print
promises offline earnings at 50% — so the page honours that too, crediting the time
you spend away.

Roughly halfway down, the brochure loses its nerve.

## Stack

No framework, no build step, no dependencies. One hand-written `index.html`, with the
CSS and JS inline and the assets served as files. It is about 60 KB of markup over a
kit of WebP art, WOFF2 subsets, and Opus/MP3 audio.

```
index.html          the whole site
assets/img/         hand-inked art; assets/img/char/ is the crow cast
assets/fonts/       Fraunces (display), Archivo (UI), Caveat (the red pen)
assets/audio/       Line City Radio — Opus with an MP3 fallback
variants/           four earlier design directions, kept as a record of the process
```

## Notes on the build

- **Three typefaces, and only three.** Fraunces sets the voice, Archivo does the
  interface, Caveat is the marketing department's own handwriting in the margins.
- **The characters run the game's animation data.** Norm's expression cycles and his
  wave are the real frame timings from the game's `NormPortrait`, not an approximation —
  so his idle in the browser is his idle in the build.
- **The HUD has weight.** The wallet and the radio hang off the scroll on a spring
  rather than tracking it, so they lag, overshoot, and settle instead of feeling welded
  to the viewport.
- **Nothing is invisible without JavaScript running.** Scroll reveals fall back to a
  rect-based sweep, so a deep link into the middle of the page can never leave you
  looking at a blank screen.
- **Motion is optional.** `prefers-reduced-motion` stops the drift, the hops, the coin
  arcs, and the sprite cycling; the page stays fully usable and fully legible.

## Running it

Any static server. The fonts need an origin, so `file://` will not do:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

---

Line City is not a real place. The rent, however, is real.
