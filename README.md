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
| Cut | Hold a knife and push the edge down through food (sawing helps; serrated knife saws skins). Tiny pieces become a minced pile; keep chopping it to mince finer |
| Crush garlic | Press the flat of the blade down onto a clove |
| Stove | Grip a knob and twist your wrist: OFF → click-click → HI → LO |
| Peel onion / crack egg | Pull the skin off with your second hand (or press trigger); tap an egg on a pan rim (or press trigger) |
| Tongs | Hold trigger to close them on food |
| Pat dry | Wipe food with a paper towel |
| Oven | Twist the left dial (temperature) and the right dial (OFF / BAKE / CONVECT / BROIL); grip the door handle and pull it down; with the door open, grip a rack's front bar and slide it out |
| Faucet | Grip the lever: lift for flow, swing left/right for cold/hot. Hold hands or food under the stream to wash them |
| Pour | Tilt any pan, pot, jug, bottle, ladle or spoon past its rim. Dip a spoon/ladle into a (tilted) pan to scoop, then tip it over food to baste |
| Thermometer | Push the probe into food or liquid; trigger toggles °C/°F |
| Salt | Turn the salt box over and shake (or press trigger) |
| Pasta | Trigger snaps dry spaghetti in half |
| Droplets | Flick a wet hand (after the faucet) to throw water drops, e.g. onto a hot pan (Leidenfrost) |
| Fryer | Twist the fryer knob (thermostat 120–200°C, gauge on the wall); lower the basket into the oil, hang it on the back bracket to drain |
| Grill | Twist the grill knob (click-click → HI → LO); food on the grate gets sear marks where the bars touch; fat drips flare up |
| Grease fire | Put a lid on it, dump baking soda on it (trigger with the box), or use the extinguisher (trigger). Never water! |
| Dredge | Dip food in the flour, egg-wash and breadcrumb bowls by the fryer, in that order |
| Season | Shake the salt, paprika or chili shakers (turn over and shake, or trigger); twist or trigger the pepper grinder; trigger near the salt cellar with an empty hand takes a pinch, releasing it sprinkles |
| Eat | Hold food (or a spoon, ladle or bowl with liquid) at your mouth for a moment to take a bite (or a sip); a taste card appears |
| Smash / scoop / mash | Press the spatula down hard on a burger; drag a spoon through a cut avocado half; press a spoon or whisk into an avocado or potato pile |

Every stick function (Move / Teleport / Turn / Teleport+Turn / None) can be assigned to either hand
independently in **Menu → Comfort**. The panel shows the resolved axis layout, including auto-assigned turning.

**Desktop:** `WASD` move · mouse look · hold `LMB` to grab, release to drop/throw · `RMB` use ·
wheel = hold distance · `R` + mouse rotates the held item · `1`–`9` tools, `0` empty hand · `F` force-grab ·
hold `T` to aim a teleport · `Q`/`E` snap turn · `C` crouch · `M`/`Tab` menu · `P` perf HUD ·
`RMB` with a knife chops at the crosshair (`Shift`+`RMB` crushes with the flat) · `LMB`-drag a stove knob to twist it ·
hold `RMB` with tongs to grip · `X` toggles Chef's Eye · `LMB`-drag the oven door, a rack or the faucet lever ·
`R` + mouse tilts a held vessel to pour · `RMB` with the salt box shakes it · `V` flicks water off a wet hand ·
`B` bites (or sips) the held item · `G` takes a pinch from the salt cellar under the crosshair, `G` again sprinkles it.

**Test mode:** open the page with `?test` (e.g. `index.html?test`) to run the headless thermal scenarios and show
a pass/fail table.

## Milestone status

- [x] **M1**: kitchen blockout, XR session, physics hands, grabbing/throwing, two-handed items, force grab,
  per-hand locomotion (smooth / teleport / snap & smooth turn, vignette, blink, seated, recalibrate, recenter,
  dominant hand), wrist menu, desktop fallback, settings persistence.
- [x] **M2**: tools & plane-slicing with inherited thermal state, minced piles, garlic crush, two-node pan
  thermals (cast iron / stainless / nonstick / saucepan), gas range with twist knobs and flames, 1D thermal sim
  with evaporation, crust formation and carryover, ribeye / egg / onion / garlic, Maillard browning and char,
  smoke and steam, sizzle audio, Chef's Eye, `?test` mode
- [x] **M3**: instant-read thermometer, oven (bake / convection / broil, hinged door with window and light,
  sliding racks, preheat indicator, door-open heat loss, broil radiation), sink and faucet (flow and temperature,
  washing food and hands), water and boiling (real heat capacity, lids, salt concentration by evaporation, boil
  visuals and audio), spaghetti and penne (hydration timing, al dente to mushy, salt uptake, snap and limp
  coil), rice by absorption with scorching, liquids (fill surfaces with wobble, weir-law pouring by viscosity,
  streams, transfers, puddles, oils with smoke points and shimmer), butter (melt, foam, noisette, burnt,
  basting), pan crowding with pooled juices, and Leidenfrost droplets
- [x] **M4A**:
  - Deep fryer: 18 L, thermostat, gauge, basket with hang-to-drain, oil drop and recovery, crackle and spatter.
  - Grill: bars plus radiant flames, per-face sear-mark stripes, fat flare-ups, embers.
  - Dredging: flour → egg → crumbs as ordered coating layers that brown and crisp.
  - Grease fires: water flare-up; lid, baking soda or extinguisher puts them out.
  - Proteins: filet, burger (smash), chicken breast and thigh (crisping skin), pork chop, bacon (renders), sausage (splits), salmon (skin, albumin), cod, shrimp (curls), tofu.
  - Vegetables: tomato (squashes under a non-serrated knife), peppers and jalapeño, potato (fries, cubes, baked), carrot, mushroom, broccoli, zucchini, corn, spinach (wilts), lettuce, avocado (pit, scoop, mash), garlic bulb.
  - Seasoning that sticks to food.
  - Eating: carved bites with teeth marks, chew audio by texture, taste cards, reactions.
- [ ] M4B: dough, batters, bread, mixing, appliances, dairy & fruit, all §7 dishes
- [ ] M5: Sandbox complete, Challenge mode, scoring, mentor
- [ ] M6: polish, particles, audio mix, performance pass

## Code map (inside `index.html`)

Search for the banner comments: `[CONFIG] [UTIL] [SAVE] [RENDERER] [TEXTURES] [AUDIO] [HAPTICS] [PHYSICS]
[THERMAL] [KITCHEN] [PROPS] [FOOD] [STOVE] [SIZZLE] [PARTICLES] [CHEF'S EYE] [TEST MODE] [CONTROLS] [OVEN]
[THERMOMETER] [LIQUIDS] [SINK] [BOIL AUDIO] [FRYER] [GRILL] [FIRE] [SEASONING] [DREDGE] [EATING] [UTENSILS]
[INPUT] [HANDS] [GRAB]
[LOCOMOTION] [UI] [SIM] [DESKTOP] [PERFHUD] [XR SESSION] [MAIN]`.

- `[THERMAL]` is pure JS (no rendering or physics): `THERMO` constants, data-driven `FOOD_DEFS` and `PAN_DEFS`,
  the `Thermo` finite-volume food model, the two-node `PanThermo`, vessel `Contents` (water, oil, butter, salt,
  rice), the two-node `OvenThermo` and the test scenarios.
- `[LIQUIDS]` gives every vessel a `Contents`. It finds the free-surface height by sorting interior sample points,
  pours past the lowest rim point with a weir law, and traces streams to decide where liquid lands.

- All tunables live in `CONFIG`, with units in comments. Player settings are in `DEFAULT_SETTINGS` and are saved to
  `localStorage`.
- Props are data-driven (`PROP_DEFS`). Tools are authored with the grip at the origin, the working end toward −Z
  and the edge toward −Y, so snap grips need no per-tool offsets.
- Opaque surfaces share one "uber" material: a 2048² procedural atlas plus per-vertex roughness, metalness and
  emissive. The static kitchen is 2 draw calls and each prop is 1. The measured M1 scene is about 38 draws per
  eye plus 42 shadow draws, roughly 118 per VR frame.
- `window.MEP` exposes the main systems for console debugging.
