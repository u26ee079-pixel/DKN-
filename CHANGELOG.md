# Changelog

All notable changes to DKN are listed here, newest first.
Installer naming follows the package version (e.g. `DKN-1.1.0-setup.exe`).

## [Unreleased]

### Added
- **Story Bible, Characters, World Builder and Beat Board** - four new story screens under the
  **Story** menu, saved inside the same `.dknproj` file (story schema v2, old files open unchanged).
- **Five local AI agents** (Story, World, 3D, Script, Anim) that run against a local Ollama server.
  Every draft is a suggestion card - Apply, Edit the JSON, or Discard. Nothing is auto-applied.
- **3D Sets -> 2D Frames** (Story menu) - build a scene as a light 3D set and project it into the
  flat 2D frame used by cards, previews and exports. Scenes store the set as `scene.asset3d`, and
  `story.library3d` keeps reusable places and characters.
  - 25 shapes (blocks, cylinders, cones, balls, roofs, columns, arches, trees, bushes, rocks,
    mountains, clouds, windows, doors, stairs, fences, banners, lamps, tables, chairs, shelves,
    barrels, crates, people and faces), grouped in the **Add** menu.
  - Faces for figures and heads: eight expressions plus hair colour, drawn as projected portrait
    features that turn and squash with the camera.
  - Per-object rotation, round-shape sides and visibility; camera pan; three render qualities
    (cinematic, clean, sketch) with gradients, ground shadows, depth cueing and a vignette.
  - **Blender-style viewport**: orbit, pan, cursor-anchored zoom, click-to-select, ground drag,
    Alt-raise, red/green/blue axis gizmos, arrow-key nudging, Ctrl snapping, and Reset/Top/Front/Fit.
  - Full inspector for every value, **Use as scene frame** (1280x720 PNG, one undo step), save to
    the personal library, duplicate, and remove.
  - Nine ready-made sets: rainy bedroom, forest clearing, village market, city rooftop, desert
    temple, Mira, the Stranger, the Child and the Tin Robot.
- **Draw & Build** (Story menu) - a Krita-inspired canvas studio: brushes with presets and
  stabilisers, shapes, fill, gradients, selections, layers with blend modes, colour sampler,
  assistants (ruler, isometric grid, two-point perspective, ellipse guide). Every shape is recorded,
  and **Build 3D set** turns a floor plan into an editable 3D set (`lib/sketch3d.js`);
  **Save frame** writes the painting to the scene.
- **AI art director for 3D** - the 3D agent plans the composition first, then builds the objects from
  that plan, your current set, your selection and a free-text instruction. Modes: Revise set, Add
  detail, Rebuild. The result card shows a 2D thumbnail, the reasoning and a change list, with
  **Preview in viewport**, **Use this set** or **Discard**. Suggestion cards and the preview modal
  now show the same reasoning ("Why") and change list.
- **Sound cues and dialogue notes** on a scene, shown and editable under the scene prose.
- **`docs/PHASE-2.md`** - setup, agent behaviour and troubleshooting.
- **`docs/PHASE-3.md`** - 3D set format, viewport controls, AI art director and the paint studio.

### Changed
- Applying an AI suggestion now keeps you in the **Editor** instead of jumping to a Story screen.
  The status bar confirms what was applied ("Applied: Story Bible") and the Story menu is one
  click away if you want to review it. Applying a **3D set** while you are on **3D Sets** keeps you
  there, and the viewport loads the accepted set automatically.
- Saved 3D frames use the **cinematic** quality preset at 1280x720.

### Fixed
- **Draw & Build no longer crashes at startup** - `sketch3d.js` imported a non-existent colour helper
  (`mixColors`); it now uses `mixHex`.
- **3D renderer no longer floods the console with React key warnings** - element keys are passed
  directly instead of being spread with the other SVG props.
- **The Story menu now opens.** The top bar's segmented control was clipping its dropdown, so
  clicking "Story" showed nothing and the story screens could not be opened by hand.
- Lists returned by the model (themes, world rules, palette) are kept even when the model sends
  objects instead of strings, so a palette no longer shows "0 colours".
- "Clear history" in the suggestions panel no longer throws away cards that are still waiting.

## [1.1.0] — 2026-10

### Added
- **Wire tools menu (press W)** on the Board and Timeline: ✂ cut-knife (drag a line across wires to
  cut them), delete selected wire, disconnect scene, ⇢ connect to next scene, ⤳ insert a scene into
  a wire (A → C becomes A → B → C), ⛓ auto sequence (whole story / one chapter / time order),
  ✨ beautify, ▦ arrange cards by wire flow, 🗑 remove all. Items are numbered — press 1–9.
- **Scene tools menu (press S)** over a scene card: ✎ edit, 🖼 add photo, add ＋/− ports, tag,
  move to chapter, ⧉ duplicate, ✕ delete; on the Timeline also set/clear date & time.
- **Shortcut keys you can change** — Settings > Shortcut keys (stored per computer; never fire
  while typing; Ctrl+S still saves).
- **Timeline rebuilt around scene dates**: each scene has Year · Month · Day · Time on a calendar
  you invent; scene cards sit in story time; wires show the time gap between scenes
  (`+7 h 30 min`, `+2 mo 2 d 14 h`); *⏳ Chapters in time* panel; *Not dated yet* strip; orange
  dashed flashback wires (`⟲ back …`); *⇢ Connect in time order* button.
- **In-app Help desk (❔)** — plain-English guide to every feature with live search, quick-jump
  chips and try-it buttons.
- **News tab (📣)** — What's new per version, earlier releases, *Check for updates* link, and a
  red dot until the newest item has been read.

### Changed
- Board wiring moved from *plugs* to **＋/− ports**: a wire flows from a scene's **− negative**
  (right) into another scene's **＋ positive** (left); every wire gets its own port dot.
- Board layout works as a **story graph**: new scenes auto-place beside the current scene, and the
  card layout + wire graph is saved with the story.
- Timeline redesigned from a day-grid to a **flow layout**: even-spaced cards per chapter band,
  time-gap neighbours on the axis, per-wire gap labels.
- Translate: keeps English names and everyday loanwords (Hindi + other languages), automatic
  fallback when one free service is rate-limited, provider note in the panel.

### Fixed
- **Board wires were invisible** — the wires' SVG sat at the wrong origin (~23 000 px off screen),
  so wires never appeared at the card dots; wires now start and end exactly on the ports.
- Timeline no longer blanks or crashes on a brand-new story (no timeline data yet).
- Timeline chips clipped by a CSS name clash with the Translate panel (renamed to `tlx-*`).
- Knife cut missed wires whose sample point lay exactly on the cut line (touching now counts).

## [1.0.0] — 2026

- Story → chapters → scenes; add / rename / delete / reorder scenes (drag-and-drop + buttons)
- Prose editor per scene; artwork per scene (upload, drag-drop, freehand drawing pad)
- Undo last 10 changes (button + Ctrl+Z)
- Save / Save As / Open `.dknproj` (Ctrl+S / Ctrl+O); automatic session-recovery autosave
- Whole-story PDF export (cover page, chapter page breaks, embedded artwork)
- Visual 2D Board with typed links, and a story Timeline with a custom calendar
- Dark theme; Windows installer