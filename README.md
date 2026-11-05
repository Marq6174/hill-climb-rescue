# Hill Climb Rescue

An emergency-services hill climber. Drive an ambulance, a police cruiser or a fire engine over five hilly maps with real physics. Keep your tank from running dry, collect pills, land flips, answer dispatch calls, and spend your pills in the garage on upgrades. Every vehicle and map is open from the start, and stream viewers can swap the vehicle or map in the middle of a run.

## Controls

| Action | Keyboard | Touch |
|---|---|---|
| Gas | `D` | **Gas** pedal (bottom right) |
| Brake / reverse | `A` | **Brake** pedal (bottom left) |
| Tilt back | `←` | Round button next to the brake |
| Tilt forward | `→` | Round button next to the gas |
| Nitro / water cannon | `W`, `↑` or `Shift` | Blue button above the gas pedal |
| Siren | `H` | Siren button (top right) |
| Pause | `Esc` or `P` | Pause button (top right) |
| Sound / music | `M` / `N` | Buttons in the garage and pause menu |
| Live swaps | `1`–`3` vehicle, `4`–`8` map, `V` / `B` next | — |
| Viewer gifts | `F` add fuel, `G` remove fuel, `J` jail, `K` KABOOM, `R` helicopter | — |

In the garage, press `D` or `Enter` to start driving.

## Crashes

Flips are fine as long as you don't land on the driver. A run ends when:

- **The driver's head hits the ground.** Each vehicle has a head zone on the roof right above the driver. If the ground touches it, at any speed, the run is over. In practice, landing roughly upside down (from about 135° to 240° of rotation) is fatal for all three vehicles. Landing on the wheels, the nose or the tail is survivable.
- **You stay flipped or stuck.** If the vehicle is on its side or tail, or wedged with no wheels down, and isn't moving, a 4-second countdown appears. Tilt with `←` / `→` to roll back onto your wheels before it runs out.
- **The tank stays empty.** At 0% an "OUT OF FUEL" panel starts a 30-second countdown while you coast. Any refill or fuel gift clears it, and it starts again from 30 if you run dry again. Press **End run** or `Enter` to stop waiting.
- **A viewer sends KABOOM** (see below). The score goes back to 0 and the next vehicle starts straight away.

## Vehicles

All three vehicles have the same four upgrades (Engine, Suspension, Tires, Tank), with 10 levels each. Every vehicle keeps its own upgrade levels. They drive very differently:

| Key | Vehicle | Class | Runs on | How it drives | Special |
|---|---|---|---|---|---|
| `1` | **Ambulance** | All-rounder | Oxygen | Balanced speed, grip, fuel and air control. | **Reserve O₂:** once per run, a backup tank refills 30% when you run dry. A patient heart-rate gauge spikes on hard bumps. |
| `2` | **Police Cruiser** | Speedster | Fuel | Light and low. Fastest top speed and the quickest flips, but bouncy, slips on steep hills and has the smallest tank. | **Nitro:** hold the ability key for a burst of speed that also works in the air. It recharges as you drive. |
| `3` | **Fire Engine** | Heavy hauler | Fuel | Long, heavy, three axles. Slow, but climbs the steepest hills, grips the best, carries the most fuel and barely bounces. Rotates slowly in the air. | **Water cannon:** hold the ability key to spray. Put out brush fires on the road for bonus pills. |

How they measure with no upgrades and fully upgraded (level 10):

| | Ambulance | Police Cruiser | Fire Engine |
|---|---|---|---|
| Top speed | 33 → 81 km/h | 49 → 117 km/h | 25 → 59 km/h |
| Steepest climb (no upgrades) | 40° | 36° | 46° |
| Spin in 1 s of air tilt | 264° | 351° | 162° |
| Tank | 34 → 104 s | 28 → 78 s | 44 → 124 s |
| Weight | medium | light | heaviest |

The garage's Vehicles tab shows Speed, Power, Grip, Tank, Air and Weight bars for each one, and they grow as you upgrade. Upgrades cost a bit more for the police cruiser (×1.2) and the fire engine (×1.4).

## Maps

Each map is one fixed course, the same every run, so you can learn it. Each has its own best distance, marked by a red "BEST" flag, and its own areas that blend into each other as you drive.

| Key | Map | Pills | Character |
|---|---|---|---|
| `4` | **City General** | ×1 | Hospital District, Countryside, Mountain Pass, Night Highway. The original course. |
| `5` | **Desert Canyon** | ×1.25 | Sand dunes with jump ramps, red canyons, a mesa sunset and a starlit desert. Sand has less grip. |
| `6` | **Frozen Peaks** | ×1.5 | Steep snowy climbs, falling snow, a slippery ice glacier and an aurora at night. |
| `7` | **Volcano Ridge** | ×2 | Jagged rock, glowing lava, embers in the air and lots of fires for the fire engine. |
| `8` | **Moon Base** | ×2.5 | Low gravity, craters and huge air time, with Earth in the sky. Supply beams let you grab refills in mid-jump. |

Your starting building changes with your vehicle: the hospital, the police department or the fire station (and a dome base on the Moon).

## Live swaps (TikTok LIVE and other streams)

Viewers can change the vehicle or the map in the middle of a run. The run keeps going from the same distance with the same pills, score and fuel level. Only the vehicle under you, or the ground and gravity, change. A banner shows "Viewer swap!" and the incident report counts the swaps. Swaps come at most every 1.2 seconds, so a burst of gifts queues up instead of strobing the screen. In the garage or on the report, the same triggers just change what you'll drive next.

There are three ways to trigger a swap:

1. **Keys**, for stream tools that can press a key when a viewer sends a gift or a chat command (for example TikFinity's keystroke actions): `1`–`3` pick a vehicle, `4`–`8` pick a map, `V` is the next vehicle and `B` is the next map. The game's browser window has to be the focused window for simulated keys to reach it.
2. **Script API** on the page: `HillClimbRescue.vehicle("police")`, `HillClimbRescue.map("moon")`, `HillClimbRescue.nextVehicle()`, `HillClimbRescue.nextMap()`. The IDs are listed in `HillClimbRescue.vehicles` and `HillClimbRescue.maps`.
3. **postMessage**, for an overlay that embeds the game in an iframe: `frame.contentWindow.postMessage({ type: "hill-climb-rescue", vehicle: "fire", map: "volcano" }, "*")`, or `next: "vehicle"` / `next: "map"`.

## Viewer gifts

Stream tools can tie these to gifts, the same way as live swaps. Each one is a key, a script call and a postMessage action.

| Gift | Key | Script call | What it does |
|---|---|---|---|
| **Add fuel** | `F` | `HillClimbRescue.addFuel(2)` | +2% each by default. The tank can overfill up to 1000%, and the HUD shows the percentage. Quick gifts add up into one notice, like "+28% FUEL". |
| **Remove fuel** | `G` | `HillClimbRescue.removeFuel(2)` | −2% each by default. |
| **Jail** | `J` | `HillClimbRescue.jail(15)` | A cage drops over the vehicle with a countdown. Vehicle, distance and fuel freeze for 15 s. More jail gifts add time, up to 60 s. |
| **KABOOM** | `K` | `HillClimbRescue.kaboom()` | The vehicle explodes: wheels fly off and the charred body tumbles. Pills and best distance are banked, the score goes back to 0, and a circle wipe reveals a different vehicle on the same map. |
| **Air medevac** | `R` | `HillClimbRescue.helicopter()` | A medical helicopter flies you 5,000 m down the course in about 9 s, then sets you down on a gentle stretch of road. Fuel is paused and no pills are collected on the way. More gifts add 5,000 m to the flight. It also frees you from jail. |

Gifts sent while the helicopter is flying wait until it lands, except KABOOM, which is ignored. With postMessage, use `{ type: "hill-climb-rescue", action: "addFuel", amount: 200 }`.

## How it works

- **Watch your tank.** It drains as you drive. Grab O₂ canisters (ambulance) or fuel cans (police and fire) to refill it. They get farther apart the deeper you go.
- **Pills are coins.** Red pills are worth 5, blue 10 and gold 25, multiplied by the map's pill bonus. You also earn bonus pills for backflips, frontflips, long air time and putting out fires. Spend them on upgrades.
- **Dispatch calls:** three missions at a time, such as "Drive 600 m in one run", "Land 3 flips", "Hit 85 km/h" or "Put out 2 fires". Finish one during a run for bonus pills. New calls get harder as you complete them, and you can swap one call after each run.
- **Garage:** the Upgrades, Vehicles, Maps and Calls tabs. Picking a vehicle or map shows it live behind the garage. A red dot on a tab means there's an upgrade you can afford or a new call.
- **Incident report** after every run: distance, pills, stunts, fires, top speed, completed calls and viewer swaps.
- **Service record:** lifetime runs, distance, flips, top speed, longest air, fires put out, calls completed and your best run.
- **Sound:** every vehicle has its own siren and engine note, and each map plays the music loop in its own key and tempo. Everything is generated live with the Web Audio API, so there are no audio files.

Your pills, upgrades, best distances and calls are saved in your browser. Saves from the first version (pills, ambulance upgrades and best distance) carry over automatically.

**Start over:** press **Reset all progress** at the bottom of the garage, under the Drive button. This isn't the same as **Restart run** in the pause menu, which only restarts the current drive. After you confirm, the game goes back to how it was on the very first launch: 0 pills, no upgrades, no best distances. Your sound and music settings are kept. The save lives in each browser separately, so resetting on one computer doesn't affect another.

## Run it

Everything is in one `index.html` file with no build step. The physics engine ([planck.js](https://github.com/piqnt/planck.js), a JavaScript port of Box2D) and the fonts load from public CDNs, so the game needs an internet connection the first time it loads.

- **Locally:** open `index.html` in a browser.
- **GitHub Pages:** push this folder to a repo, go to **Settings → Pages**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.

Adding `?debug` to the URL exposes the game state as `window.__hcr` in the browser console, for playtesting.
