# Mise en Place VR

A physics-driven VR cooking simulator for the Meta Quest Browser (Quest 3 / 3S), built as one self-contained
`index.html`. It uses WebXR, three.js and Rapier from a CDN, with no external assets: every model, texture and
sound is generated at runtime.

## Running it

WebXR needs a secure context, so the page must be served over **HTTPS** (or `localhost`).

- **GitHub Pages** is the easiest route: enable Pages for this repo and open the URL in the Quest Browser.
- **Local:** run `npx http-server -p 8080` (or any static server) in this folder, then `adb reverse tcp:8080 tcp:8080`
  and open `http://localhost:8080` in the Quest Browser.
- **Desktop:** open the page in Chrome or Edge and click **Play on Desktop**.

## Controls

**VR**

| Action | Input |
| --- | --- |
| Grab (large items take two hands) | Grip |
| Use held item / click UI | Trigger |
| Smooth move (default left stick) | Stick |
| Teleport + snap turn (default right stick) | Push forward to aim, rotate the stick to choose facing, release to jump; flick left/right to turn |
| Point teleport | Hold grip + trigger on an empty hand |
| Force grab | Point at a distant item, hold grip, flick your wrist |
| Wrist menu | Turn your non-dominant palm toward your face; **Y/B** pins it in front of you |

Every stick function (Move / Teleport / Turn / Teleport+Turn / None) can be assigned to either hand
independently in **Menu → Comfort**. The panel shows the resolved axis layout, including auto-assigned turning.

**Desktop:** `WASD` move · mouse look · hold `LMB` to grab, release to drop/throw · `RMB` use ·
wheel = hold distance · `R` + mouse rotates the held item · `1`–`9` tools, `0` empty hand · `F` force-grab ·
hold `T` to aim a teleport · `Q`/`E` snap turn · `C` crouch · `M`/`Tab` menu · `P` perf HUD.

## Milestone status

- [x] **M1**: kitchen blockout, XR session, physics hands, grabbing/throwing, two-handed items, force grab,
  per-hand locomotion (smooth / teleport / snap & smooth turn, vignette, blink, seated, recalibrate, recenter,
  dominant hand), wrist menu, desktop fallback, settings persistence.
- [ ] M2: tools & cutting, cookware, stovetop, thermal simulation (steak, egg, onion), sizzle audio, cut-face gradient
- [ ] M3: browning/char/evaporation/carryover, thermometer, oven, boiling, pasta, liquids & pouring
- [ ] M4: remaining foods & appliances, seasoning, eating & taste cards
- [ ] M5: Sandbox complete, Challenge mode, scoring, mentor
- [ ] M6: polish, particles, audio mix, performance pass

## Code map (inside `index.html`)

Search for the banner comments: `[CONFIG] [UTIL] [SAVE] [RENDERER] [TEXTURES] [AUDIO] [HAPTICS] [PHYSICS]
[KITCHEN] [PROPS] [INPUT] [HANDS] [GRAB] [LOCOMOTION] [UI] [SIM] [DESKTOP] [PERFHUD] [XR SESSION] [MAIN]`.

- All tunables live in `CONFIG`, with units in comments. Player settings are in `DEFAULT_SETTINGS` and are saved to
  `localStorage`.
- Props are data-driven (`PROP_DEFS`). Tools are authored with the grip at the origin, the working end toward −Z
  and the edge toward −Y, so snap grips need no per-tool offsets.
- Opaque surfaces share one "uber" material: a 2048² procedural atlas plus per-vertex roughness, metalness and
  emissive. The static kitchen is 2 draw calls and each prop is 1. The measured M1 scene is about 38 draws per
  eye plus 42 shadow draws, roughly 118 per VR frame.
- `window.MEP` exposes the main systems for console debugging.
