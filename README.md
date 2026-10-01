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
| Fridge / microwave | Grip the door handle and swing it open (LMB-drag on desktop). The fridge keeps food at 4°C. Microwave: close the door and twist the timer dial (up to 5 min); the turntable spins and heating is uneven |
| Toaster | Drop slices into the slots, push the lever down; the dial sets the browning; they pop up with a ding |
| Stand mixer / blender | Set the mixer bowl on the base (it locks), twist the speed dial. Put the blender jar on its base, press the button (8 s). Without the lid it sprays everywhere |
| Kettle | Fill it at the faucet and put it on a burner; it whistles at the boil |
| Dough | Mix flour + water (+ yeast) in a bowl until it comes together. Squeeze with both hands to knead (builds gluten), pull apart to stretch (needs gluten), roll with the rolling pin (or RMB with the pin). Leave it somewhere warm to proof |
| Batter | Pour batter or beaten egg on a hot pan for pancakes or an omelette; flip when bubbles stay open (spatula: trigger flips, or folds an omelette). Bake cake batter in a dish |
| Dairy & fruit | Rub cheese down the grater; squeeze a cut lemon or lime over food or into a bowl; peel a banana (trigger) |
| Challenge | Tickets print on the rail by the pass (left wall). Plate each dish on a plate or bowl on the steel pass and ring the bell (tap it, or grab + trigger). The scoreboard beside it shows the breakdown |
| Food safety | After raw chicken, rinse the board, knife or your hands under the running faucet (~1.5 s). Hush a smoke alarm with the button on the wall |

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
  - Deep fryer: 8 L, thermostat, gauge, basket with hang-to-drain, oil drop and recovery, crackle and spatter.
  - Grill: bars plus radiant flames, per-face sear-mark stripes, fat flare-ups, embers.
  - Dredging: flour → egg → crumbs as ordered coating layers that brown and crisp.
  - Grease fires: water flare-up; lid, baking soda or extinguisher puts them out.
  - Proteins: filet, burger (smash), chicken breast and thigh (crisping skin), pork chop, bacon (renders), sausage (splits), salmon (skin, albumin), cod, shrimp (curls), tofu.
  - Vegetables: tomato (squashes under a non-serrated knife), peppers and jalapeño, potato (fries, cubes, baked), carrot, mushroom, broccoli, zucchini, corn, spinach (wilts), lettuce, avocado (pit, scoop, mash), garlic bulb.
  - Seasoning that sticks to food.
  - Eating: carved bites with teeth marks, chew audio by texture, taste cards, reactions.
- [x] **M4B**:
  - Dough: two-hand kneading builds gluten, stretching needs it, rolling pin, yeast proofing by temperature (dies above 60°C), baking to 93–99°C internal with crust.
  - Batters: pancakes with flip-time bubbles (overmixing makes them tough), cake that rises and sets, cookies that spread.
  - Mixing: homogeneity, egg whites (soft → stiff → grainy), whipped cream, vinaigrettes that separate, carbonara that scrambles when too hot, mounted butter sauces.
  - Appliances: fridge (4°C, hinged door), stand mixer, blender (lid or spray), toaster, microwave (uneven heating, no browning), whistling kettle, wok (hot centre, toss).
  - Dairy and fruit: cheddar, mozzarella and parmesan (grate, melt); milk and cream; lemon/lime juice; banana and apple browning; strawberries; tortillas; bread and buns.
  - Every §7 dish has a `?test` scenario walking its states.
- [x] **M5**:
  - Main menu: a board standing in the kitchen with Sandbox, Challenge, Settings and Recipe Book.
  - Sandbox: time scale 1/2/5/10×, Chef's Eye, no fire hazards, infinite burners and oil, gravity scale, mentor tips, clean-up, reset (with confirmation), and 3 kitchen save slots.
  - Recipe Book: all 24 dishes, with live step checks and a ghost-hint marker on the next tool or ingredient.
  - Challenge: 24 levels in 4 tiers, with a ticket rail with countdowns, special requests, the pass and service bell, a scoreboard showing the full breakdown, 1–3 stars, personal bests, and unlockable knife skins, aprons and kitchen themes.
  - Tier 1 levels are tutorials for grabbing, cutting, heat control and the thermometer.
  - Tier 4 adds incidents: burner failure and smoke alarm.
  - Food safety: raw chicken contaminates boards, knives and hands until they're washed at the sink. The smoke alarm penalises burnt food.
  - Chef mentor: context-aware lines with a cooldown.
- [x] **M6**:
  - Perf HUD (P / Settings): fps, worst frame, draw calls, triangles, live food pieces, particles, and sim / physics / CPU / submit ms.
  - Adaptive quality in VR: the shadow map updates every other frame, the shadow-caster radius shrinks and particles thin out, then everything recovers once there's headroom.
  - Hot-path fixes: dredge lookup once per tick, and "thermal sleep" for idle food. With 100 food pieces (40 of them cooking) the cooking tick fell from 15.4 ms to about 2.3 ms.
  - Appetizing shading: crust relief that builds with browning, an oily sheen from pans and the fryer, and a warm subsurface tint on raw red meat and fish.
  - New particles: juice drips when cutting cooked meat, and flour puffs while kneading. Grease spatter now falls under gravity.
  - Heat shimmer over very hot pans (toggleable). Render-scale setting.
  - Audio mix: cooking, sfx, UI and music buses into a master limiter; the mentor's voice ducks the cooking bed; optional procedural jazz radio.
  - Comfort audit: every locomotion mode on the left hand, right hand and both hands, plus all 50 L×R×dominant-hand combinations, with no stick conflicts.
  - `?test` adds live checks for §13.4 (Challenge scorecard), §13.8 and §13.10.

## Upgrade pass (post-M6)

This pass came out of real-input playtests that drive the game the way a player does: actual mouse and keyboard on desktop, and simulated Quest controller poses for VR.

- **VR grabbing fixed.** Empty hands no longer collide with props. Before, reaching for a knife lying on the board shoved it away or grabbed the board instead. Grab priority now favours tools by their handle and food over boards, plates and towels.
- **Desktop fixes:**
  - Hinged doors (fridge, microwave) follow the mouse. Dragging away from the hinge, or downward, pulls the door open.
  - Buttons (blender, smoke-alarm hush) respond to a click.
  - The menu (M) opens in your line of sight, even when you're looking down at the counter.
- **More desktop fixes:**
  - Hold RMB with the thermometer on a food or pot to probe it.
  - Tongs (RMB) and shakers (salt, pepper, spices: RMB) reach to whatever the crosshair is on.
  - Tongs slide around food instead of shoving it.
- **Visuals:**
  - Smooth-shaded food and gloves (meshes were flat-shaded per triangle).
  - Produce detail: tomato calyx and stem, apple stem and blush, strawberry leaves, potato eyes, onion root and tip, carrot shoulders.
  - Printed packaging labels and pantry decor (glass jars, bread).
  - Cream retro-enamel fridge with chrome handle.
  - Fine satin brushed steel (no more zebra streaks).
  - A painted garden and village view through the window.
  - Khronos Neutral tone mapping for true-to-life food colours.
  - Nitrile-glove material with a proper sleeve cuff.
  - Rim-glow hover highlight (no more solid orange objects).
  - Raw beef with streaky marbling and fibre grain; meat sears to a mottled mahogany crust.
  - Translucent golden butter and oils.
  - Real box grater (satin steel with grating teeth).
  - Real-sized bites with smooth bite marks.
- **Audio:**
  - Procedural room reverb on every sound.
  - Modal impact synthesis per material (metal, ceramic, glass, wood, stone, plastic, produce).
  - Richer chop: blade swish, snap and board knock.
  - Sizzle with crackle grain and a bubbling layer.
  - Ambience: ticking wall clock, birds and a distant street through the window.
  - Footsteps on the plank floor.

## Code map (inside `index.html`)

Search for the banner comments: `[CONFIG] [UTIL] [SAVE] [RENDERER] [TEXTURES] [AUDIO] [HAPTICS] [PHYSICS]
[THERMAL] [KITCHEN] [PROPS] [FOOD] [STOVE] [SIZZLE] [PARTICLES] [CHEF'S EYE] [TEST MODE] [CONTROLS] [OVEN]
[THERMOMETER] [LIQUIDS] [SINK] [BOIL AUDIO] [FRYER] [GRILL] [FIRE] [SEASONING] [DREDGE] [EATING] [UTENSILS]
[APPLIANCES] [BAKERY] [DAIRY, FRUIT & EGGS] [SCORING] [INPUT] [HANDS] [GRAB]
[LOCOMOTION] [UI] [SIM] [DESKTOP] [PERFHUD] [PROGRESS] [COSMETICS] [MENTOR] [SAFETY] [GAME] [PASS] [CHALLENGE] [RECIPES] [POLISH] [MIX] [AMBIENCE] [JAZZ] [XR SESSION] [MAIN]`.

- `[THERMAL]` is pure JS (no rendering or physics): `THERMO` constants, data-driven `FOOD_DEFS` and `PAN_DEFS`,
  the `Thermo` finite-volume food model, the two-node `PanThermo`, vessel `Contents` (water, oil, butter, salt,
  rice, dairy, batters, sauces), the two-node `OvenThermo` and the test scenarios.
- `[SCORING]` is pure as well. `DISH_SPECS` are data-driven per-component judges. `scoreDish()` applies the weights: doneness 30, crust 15, seasoning 15, texture 15, plating 10, serve temperature 5, speed 10. Undercooked poultry fails the dish outright (the food-safety gate). Contamination costs 15 points per component.
- `[LIQUIDS]` gives every vessel a `Contents`. It finds the free-surface height by sorting interior sample points,
  pours past the lowest rim point with a weir law, and traces streams to decide where liquid lands.

- All tunables live in `CONFIG`, with units in comments. Player settings are in `DEFAULT_SETTINGS` and are saved to
  `localStorage`.
- Props are data-driven (`PROP_DEFS`). Tools are authored with the grip at the origin, the working end toward −Z
  and the edge toward −Y, so snap grips need no per-tool offsets.
- Opaque surfaces share one "uber" material: a 2048² procedural atlas plus per-vertex roughness, metalness and
  emissive. The static kitchen is 2 draw calls and each prop is 1. Food inside the shut fridge isn't drawn, and
  only props within about 1.9 m of the player cast shadows. Measured draw calls: 106 at the spawn point, 23–52 at the stations,
  and 86 with 40 food pieces cooking on 3 burners plus the fryer.
- `window.MEP` exposes the main systems for console debugging.
