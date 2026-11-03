# DKN — Storyboard for Novelists

> From story writing to its completion.

DKN is a free, offline desktop app for novelists. You write scenes chapter by chapter, see your
whole story as a **Board** of wired scene cards, and pin each scene to your own story calendar on
the **Timeline** — so you always know what happens when, and how much time passes in between.
You can also build each scene's picture in **3D Sets**, or paint it in the Krita-inspired
**Draw & Build** studio, with five local AI agents drafting alongside you.

Built with **Electron + React**. Works on Windows, macOS and Linux.

---

## ✨ What's new in v1.1.0

- **Wire & scene tool menus** — press **W** on the Board or Timeline for wire tools (a ✂ cut-knife,
  connect-to-next, insert-a-scene-into-a-wire, auto sequence, beautify, arrange cards by wire flow,
  remove all). Press **S** over a scene for scene tools (edit, photo, ports, tag, move to chapter,
  duplicate, delete; on the Timeline also set/clear the date). Each menu item has a number — press
  **1–9** to use it instantly.
- **Adjustable shortcut keys** — W and S can be changed in *Settings → Shortcut keys*. Keys never
  fire while you are typing, and Ctrl+S still always saves.
- **Timeline rebuilt around scene dates** — every scene has its own **Year · Month · Day · Time**
  on a calendar *you* invent (fantasy years, 13-month years, whatever you like).
- **Time gaps everywhere** — every Timeline wire shows the time that passes between scenes
  (`+2 mo 2 d 14 h`), plus a *⏳ Chapters in time* panel, a *Not dated yet* strip, and orange
  dashed **flashback** wires (`⟲ back 1 mo 2 d 6 h`).
- **Board wires that actually work** — always visible, flowing **negative → positive** with
  direction chevrons, each wire on its own port, a *Thread bend* slider (0% straight, 100% curvy)
  and a *Beautify* command that untangles crossing wires.
- **Board as a story graph** — new scenes snap into place near the scene you're looking at, and
  your card layout is restored when you reopen the story.
- **Help desk & News** — an in-app ❔ Help desk answers every feature in plain English (with
  search), and the 📣 News tab announces what's new in each version.
- **Smarter translate** — keeps English names and *everyday loanwords* (friends, park, meeting)
  intact in Hindi and other languages, with automatic fallback to a second free service.

See **[CHANGELOG.md](CHANGELOG.md)** for the full release history.

---

## 🧭 How it works

### 1. Write (Editor)
A story is organised as **chapters → scenes**. Every scene is a title, prose, an optional picture,
and a story date. Scene numbers like `2.3` mean *chapter 2, scene 3* — that order is what the
Board and Timeline use. The small **When** row under the prose sets the scene's story date.

### 2. See it (Board)
The Board is a big canvas with one card per scene. Cards connect with **wires**:

- Wires always leave a scene's **− negative** ports (right edge) and enter another scene's **＋
  positive** ports (left edge).
- To connect **A → B**: drag from a **−** dot on A and drop it onto a **＋** dot on B. Every wire
  gets its own dot, so two wires never pile onto one port.
- Click a wire's label chip to select it; the little chevrons show the direction the story flows.
- New scenes appear right beside the scene you were viewing, and the layout is saved with the story.

### 3. When does it happen (Timeline)
The Timeline runs on a calendar **you build** — name your years, and set how many months and days
each year has. Then:

- Click any scene card and give it **Year · Month · Day · Time** — it instantly moves into story
  time.
- Wires show the **time gap** between scenes, and *⏳ Chapters in time* shows each chapter's span.
- Scenes without a date wait in the **Not dated yet** strip; a scene with an earlier date than the
  ones around it becomes a dashed orange **flashback** wire.

### 4. Power tools (W / S menus)
Press **W** for wire tools, **S** over a scene for scene tools — on the Board *and* the Timeline.
Cut wires with the ✂ knife (drag a line across them), auto-sequence the whole story, insert a
scene into the middle of a wire (A → C becomes A → B → C), beautify the wiring, or rearrange cards
so every wire flows left → right.

### 5. Settings (⚙)
**Thread bend** makes Board wires perfectly straight (0%) or loose and springy (100%). **Shortcut
keys** lets you change the W and S keys to whatever you like.

---

## ⌨️ Shortcuts

| Keys | What it does |
| --- | --- |
| `Ctrl+S` / `Ctrl+O` | Save / open a `.dknproj` story |
| `Ctrl+Z` | Undo (last 10 steps) |
| `W` | Wire tools menu (change in Settings) |
| `S` | Scene tools menu (change in Settings) |
| `1`–`9` | Pick an item in the open tool menu |
| `Esc` | Close a menu / cancel |
| `Ctrl+Scroll` | Zoom on the Board and Timeline |
| Drag / Shift+drag / wheel | Orbit / pan / zoom in the 3D viewport |
| Arrow keys / Alt+drag | Nudge / raise a selected 3D object |

---

## 🚀 Get started

The easiest way: download the Windows installer **`DKN-1.1.0-setup.exe`** from the
[DKN homepage on itch.io](https://nisargmpatel.itch.io/dkn-storyboard-for-novelists) — or build it
yourself below.

### Install

```bash
$ npm install
```

### Development

```bash
$ npm run dev
```

### Build

```bash
# For windows
$ npm run build:win

# For macOS
$ npm run build:mac

# For Linux
$ npm run build:linux
```

---

## 📚 More in this repository

- **[ROADMAP.md](ROADMAP.md)** — the shared feature wishlist (done → ideas)
- **[CHANGELOG.md](CHANGELOG.md)** — release notes for every version
- **[docs/PHASE-2.md](docs/PHASE-2.md)** — story screens and the writing agents
- **[docs/PHASE-3.md](docs/PHASE-3.md)** — 3D sets, the viewport, Draw & Build and the AI art director

DKN is **free forever**. Stories live in one `.dknproj` file — pictures, card layout and your
story calendar travel with it. Nothing is uploaded anywhere unless you choose to translate.

---

## Story screens and local AI

DKN also has a Story Bible, Characters, World Builder and Beat Board (open them from **Story** in the
top bar), plus five AI agents that draft story material with a model running on your own computer.
Nothing the AI writes is applied automatically: every draft arrives as a suggestion card with
Apply, Edit and Discard, and applying one is a single undo step.

Setup, agent behaviour and troubleshooting live in **[docs/PHASE-2.md](docs/PHASE-2.md)**.

---

## 🧊 3D sets → 2D frames

**Story → 3D Sets** lets you build the picture for a scene as a small 3D set: blocks, trees, houses,
props and people. There is no heavyweight 3D engine — each object is a handful of numbers, so it
stays light on a 16 GB laptop — and the set is projected with an isometric camera into the same flat
drawing DKN uses everywhere else.

- **Orbit like Blender** — drag empty space to turn around the set, Shift+drag to pan, wheel to zoom
  around the cursor. **Reset / Top / Front / Fit** snap the camera.
- **Touch the scene** — click an object to select it, drag it along the ground, hold **Alt** to raise
  it, or drag the red/green/blue axis handles to move on one axis only. Arrow keys nudge, Ctrl snaps.
- **Edit every attribute** — position, size, rotation, sides, colours, visibility, expression and hair
  for people, plus the set's sky/horizon/ground colours, camera and light. The grouped **＋ Add…**
  menu has 25 shapes: buildings, doors, windows, stairs, fences, banners, lamps, tables, chairs,
  shelves, barrels, crates, trees, bushes, rocks, mountains, clouds, people and faces.
- **Faces** — figures and heads can wear any of eight expressions (neutral, smile, grin, angry, sad,
  surprised, determined, worried) with hair that turns and squashes with the camera.
- **Three looks** — cinematic (gradients, shadows, rim light, vignette), clean, or sketch.
- **Use as scene frame** renders a 1280×720 PNG and saves it to the scene as one undo step.
  **Save to my library** keeps a reusable set; built-ins are copied, never overwritten.

Nine ready-made sets are included: five places (rainy bedroom, forest clearing, village market, city
rooftop, desert temple) and four characters (Mira, the Stranger, the Child, the Tin Robot).

## 🖌 Draw & Build

**Story → Draw & Build** is a canvas paint studio built around the parts of Krita that matter for
building a set: brushes with stabilisers and presets, shapes, fill, gradients, selections, layers,
blend modes, assistants (ruler, isometric grid, two-point perspective, ellipse guide) and recorded
shapes.

Every rectangle, ellipse, polygon and bezier is remembered. Press **Build 3D set** and `sketch3d.js`
reads those bounds, guesses a primitive (rect → block, ellipse → cylinder/ball, tapered polygon →
cone/tree, thin shape → fence/window) and turns your floor plan into a normal 3D set you can orbit
and edit. **Save frame** writes the painting to the scene instead.

## 🤖 The AI art director

The 3D agent thinks in two steps: it first **plans** the composition (read, foreground/midground/
background, detail plan, face notes, risks), then **builds** the object JSON from that plan plus your
current set and your instruction. Write what you want in plain words — “add two market crates and a
warm lamp in the foreground, and give Mira a worried face” — and pick a mode:

- **Revise set** — keep the set, change only what you asked for.
- **Add detail** — keep every object and add 4–10 new props.
- **Rebuild** — build a fresh set from the story and scene.

You get a 2D thumbnail, the reasoning and a change list, then **Preview in viewport** (try it without
saving), **Use this set**, or **Discard**. Nothing touches the story until you save, and the same
suggestion also appears in the AI panel with a “Why” block and a 1280×720 cinematic preview.

Full details: **[docs/PHASE-3.md](docs/PHASE-3.md)**.