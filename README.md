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
