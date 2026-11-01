# Hill Climb Rescue

An emergency-services hill climber. Drive an ambulance, a police cruiser or a fire engine over five hilly maps with real physics. Keep your tank from running dry, collect pills, land flips, answer dispatch calls, and spend your pills in the garage on upgrades, new vehicles and new maps.

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

In the garage, press `D` or `Enter` to start driving.

## Vehicles

All three vehicles have the same four upgrades (Engine, Suspension, Tires, Tank), with 10 levels each. Every vehicle keeps its own upgrade levels.

| Vehicle | Unlock | Runs on | What makes it different |
|---|---|---|---|
| **Ambulance** | Free | Oxygen | Balanced. **Reserve O₂:** once per run, a backup tank refills 30% when you run dry. A patient heart-rate gauge spikes on hard bumps. |
| **Police Cruiser** | 4,000 pills | Fuel | Low, light and fast. **Nitro:** hold the ability key for a burst of speed that also works in the air. It recharges as you drive. |
| **Fire Engine** | 9,000 pills | Fuel | Long, heavy, three axles, lots of torque. **Water cannon:** hold the ability key to spray. Put out brush fires on the road for bonus pills. |

Upgrades cost a bit more for the police cruiser (×1.2) and the fire engine (×1.4).

## Maps

Each map is one fixed course, the same every run, so you can learn it. Each has its own best distance, marked by a red "BEST" flag, and its own areas that blend into each other as you drive.

| Map | Unlock | Pills | Character |
|---|---|---|---|
| **City General** | Free | ×1 | Hospital District, Countryside, Mountain Pass, Night Highway. The original course. |
| **Desert Canyon** | 2,500 | ×1.25 | Sand dunes with jump ramps, red canyons, a mesa sunset and a starlit desert. Sand has less grip. |
| **Frozen Peaks** | 6,000 | ×1.5 | Steep snowy climbs, falling snow, a slippery ice glacier and an aurora at night. |
| **Volcano Ridge** | 12,000 | ×2 | Jagged rock, glowing lava, embers in the air and lots of fires for the fire engine. |
| **Moon Base** | 20,000 | ×2.5 | Low gravity, craters and huge air time, with Earth in the sky. Supply beams let you grab refills in mid-jump. |

Your starting building changes with your vehicle: the hospital, the police department or the fire station (and a dome base on the Moon).

## How it works

- **Watch your tank.** It drains as you drive. Grab O₂ canisters (ambulance) or fuel cans (police and fire) to refill it. They get farther apart the deeper you go.
- **Pills are coins.** Red pills are worth 5, blue 10 and gold 25, multiplied by the map's pill bonus. You also earn bonus pills for backflips, frontflips, long air time and putting out fires.
- **Don't roll over.** If you land on your roof, the run is over.
- **Dispatch calls:** three missions at a time, such as "Drive 600 m in one run", "Land 3 flips", "Hit 85 km/h" or "Put out 2 fires". Finish one during a run for bonus pills. New calls get harder as you complete them, and you can swap one call after each run.
- **Garage:** the Upgrades, Vehicles, Maps and Calls tabs. Picking a vehicle or map previews it live behind the garage, even before you unlock it. A red dot on a tab means there's something you can afford or a new call.
- **Incident report** after every run: distance, pills, stunts, fires, top speed, completed calls and how far you are from your next unlock.
- **Service record:** lifetime runs, distance, flips, top speed, longest air, fires put out and calls completed.
- **Sound:** every vehicle has its own siren and engine note, and each map plays the music loop in its own key and tempo. Everything is generated live with the Web Audio API, so there are no audio files.

Your pills, unlocks, upgrades, best distances and calls are saved in your browser. Saves from the first version (pills, ambulance upgrades and best distance) carry over automatically.

**Start over:** press **Reset all progress** at the bottom of the garage, under the Drive button. This isn't the same as **Restart run** in the pause menu, which only restarts the current drive. After you confirm, the game goes back to how it was on the very first launch (0 pills, only the ambulance and City General). Your sound and music settings are kept. The save lives in each browser separately, so resetting on one computer doesn't affect another.

## Run it

Everything is in one `index.html` file with no build step. The physics engine ([planck.js](https://github.com/piqnt/planck.js), a JavaScript port of Box2D) and the fonts load from public CDNs, so the game needs an internet connection the first time it loads.

- **Locally:** open `index.html` in a browser.
- **GitHub Pages:** push this folder to a repo, go to **Settings → Pages**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.

Adding `?debug` to the URL exposes the game state as `window.__hcr` in the browser console, for playtesting.
