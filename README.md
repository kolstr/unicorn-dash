# 🦄 Unicorn Dash

A dreamy endless runner in the spirit of Chrome's offline dinosaur — rebuilt as a
pastel 3D platformer with a very cute unicorn, a rainbow trail, and a
"Rainbow Rush" super mode.

Everything (the character, the world, the particles, the music, and the sound
effects) is generated procedurally in code. There are no image, model, or audio
assets.

![style](https://img.shields.io/badge/three.js-r170-blueviolet) ![style](https://img.shields.io/badge/WebGL-yes-ff69b4) ![style](https://img.shields.io/badge/dependencies-none%20(CDN)-mintgreen)

---

## ▶️ Running it

**Fastest way:** double-click `index.html` (or drag it into a browser tab).

> The game loads Three.js from the jsDelivr CDN, so the very first load needs an
> internet connection. Everything else is self-contained.

Prefer a local server? Any static server works:

```bash
cd unicorn
python3 -m http.server 8000
# then open http://localhost:8000
```

Tested in current Chrome / Edge / Firefox / Safari. Requires WebGL 2.

---

## 🎮 Controls

| Action | Keyboard | Touch |
| --- | --- | --- |
| Jump / start / restart | `Space`, `↑` or `W` | `JUMP` button or tap the scene |
| Double jump | press jump again in mid-air | tap `JUMP` again |
| Hold for a higher jump | keep the jump key down | — |
| Duck / slide | `↓` or `S` | `DUCK` button |
| Dive (fast fall) | `↓` while airborne | `DUCK` in mid-air |
| Pause / resume | `P` or `Esc` | ⏸ button |
| Mute | `M` | 🔊 button |

---

## ✨ What's in the game

**The unicorn**
- Built from low-poly primitives: pearl body, chest, neck, expressive head,
  big glossy eyes with glints, blush, pink ears, and a spiral gold horn.
- Rainbow mane and a flowing tail that react to the run.
- Procedural gallop cycle: diagonal leg pairs, body bounce, head bob, ear
  wiggles, blinking, and a sparkle fountain from the horn tip.
- Squash-and-stretch slide, airborne tuck pose, velocity-based pitch, and a
  tumble on defeat.

**The endless world**
- Endless pastel valley with three parallax mountain ridges, drifting clouds,
  floating crystal islands, lollipop trees, mushrooms, flowers, and glowing
  crystals.
- A five-minute day/night cycle: the sky gradient, fog, sun→moon, lighting, and
  bloom shift from a bright morning to a starry violet night.
- Animated "road" dashes, soft shadows, floating firefly dust, and a dynamic
  rainbow ribbon trail behind the unicorn.

**Gameplay**
- Jump, double jump, variable-height jumps, duck, and air-dive.
- Obstacles: crystal clusters, mossy boulders, tall crystal towers (need a
  double jump), and floating gloom wisps with glowing eyes (duck under them).
- Stars build a combo multiplier (up to ×8) and charge the **Rainbow Rush**.
- Collectibles: stars, hearts (restore a life), magnet orbs (pull stars to you),
  and rainbow orbs (instant rush).
- **Rainbow Rush**: 7 seconds of invincibility, extra speed, brighter bloom,
  a screen vignette, and obstacles shattering into rainbow confetti.
- Three hearts, a shield bubble during invulnerability, milestone bonuses every
  250 m, live "NEW BEST!" celebration, and a persistent high score
  (`localStorage`).

**Presentation**
- Three.js WebGL renderer with ACES tone mapping, soft shadows, and
  UnrealBloom post-processing.
- Custom GPU particle system (900 particles) for sparkles, dust, confetti, and
  fireflies.
- Glassmorphism HUD, animated gradient title, combo pops, floating score
  popups, and a hit flash.
- Fully responsive: a wider, pulled-back camera for phones in portrait, plus
  on-screen touch controls.
- Synthesised sound effects and a gentle generative music loop (WebAudio), no
  audio files. Mute as you like.

---

## 🛠️ Tweaking it

Everything lives in `index.html`. A few handy knobs:

| What | Where |
| --- | --- |
| Jump feel | `GRAVITY`, `JUMP_V`, `DOUBLE_JUMP_V` |
| Rush length | `RUSH_DURATION` |
| Difficulty ramp | `baseTarget` in `updatePlaying()` |
| Obstacle density | `nextObstacleAt` gap in `updatePlaying()` |
| Camera framing / portrait mode | `applyViewport()` |
| Unicorn size | `modelScale` |
| Bloom | the `UnrealBloomPass` constructor and `updateSky()` |
| Day/night speed | the `worldTime / 300` term in `updateSky()` |

There is also a small debug handle in the console:

```js
unicornDash.game          // score, speed, state, rush…
unicornDash.scene         // the three.js scene
unicornDash.obstacles     // live obstacles
```

Handy for experimenting: `unicornDash.game.rush = 100` triggers a Rainbow Rush
on the next frame.

---

## 📁 Files

```
unicorn/
├── index.html   ← the whole game (markup, CSS, JS, shaders)
└── README.md
```

---

## 📜 Credits

Made with [three.js](https://threejs.org/) (MIT). All geometry, animation,
particles, sound, and music are generated at runtime. No third-party art or
audio assets are used.
