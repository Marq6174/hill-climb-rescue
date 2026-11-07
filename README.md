# Hill Climb Rescue

An emergency-services hill climber. Drive twelve different rescue vehicles over sixteen hilly maps with real physics. Keep your tank from running dry, collect pills, land flips, answer dispatch calls, and spend your pills in the garage on upgrades. Every vehicle and map is open from the start, and stream viewers can change almost everything in the middle of a run.

## Controls

| Action | Keyboard | Touch |
|---|---|---|
| Gas | `D` | **Gas** pedal (bottom right) |
| Brake / reverse | `A` | **Brake** pedal (bottom left) |
| Tilt back | `←` | Round button next to the brake |
| Tilt forward | `→` | Round button next to the gas |
| Nitro / water cannon / thrusters | `W`, `↑` or `Shift` | Blue button above the gas pedal |
| Siren | `H` | Siren button (top right) |
| Pause | `Esc` or `P` | Pause button (top right) |
| Sound / music | `9` / `0` | Buttons in the garage and pause menu |

In the garage, press `D` or `Enter` to start driving.

## Stream keys

| Key | What it does |
|---|---|
| `U` / `B` / `V` | Send up 1,000 / 5,000 / 10,000 m by medical helicopter |
| `J` / `N` / `G` | Send down 1,000 / 5,000 / 10,000 m. The score can go below zero. |
| `C` | Change to a random vehicle |
| `M` | Change to a random map |
| `F` / `T` | Add / take 2% fuel. The tank can overfill up to 1000%. |
| `I` | Jail: a cage freezes the vehicle, score and fuel for 15 s |
| `K` | KABOOM: the vehicle explodes, the score goes to 0 and a different vehicle starts |
| `R` | Reset: a 50-second countdown fills the middle of the screen. At 0 the run restarts from 0. |
| `S` | Save: stops the Reset countdown and the run carries on |
| `L` | Reset Everything: wipes pills, upgrades, best distances, stats and calls, and the vehicle explodes. There is no confirmation. |

Changing the vehicle or map keeps your score, pills and fuel level. Stream tools can use these keys, as long as the game's window is the focused one, or call them from a script:

```js
HillClimbRescue.sendUp(5000);    HillClimbRescue.sendDown(5000);
HillClimbRescue.randomVehicle(); HillClimbRescue.randomMap();
HillClimbRescue.addFuel(200);    HillClimbRescue.removeFuel(200);
HillClimbRescue.jail(15);        HillClimbRescue.kaboom();
HillClimbRescue.reset();         HillClimbRescue.save();
HillClimbRescue.resetEverything();
HillClimbRescue.vehicle("train"); HillClimbRescue.map("moon");
```

`HillClimbRescue.vehicles` and `HillClimbRescue.maps` list the IDs. From an overlay that embeds the game in an iframe, use `frame.contentWindow.postMessage({ type: "hill-climb-rescue", action: "sendUp", amount: 5000 }, "*")`.

## Crashes

Flips are fine as long as you don't land on the driver. A run ends when:

- **The driver's head hits the ground.** If the ground touches the roof right above the driver, at any speed, the run is over. Landing on the wheels, the nose or the tail is survivable.
- **You stay flipped or stuck.** If the vehicle is on its side, or wedged and not moving, a 4-second countdown appears. Tilt to get back on your wheels.
- **The tank stays empty.** At 0% an "OUT OF FUEL" panel starts a 30-second countdown while you coast. Any refill or fuel gift clears it. Press **End run** or `Enter` to stop waiting.

## Vehicles

All vehicles share three upgrades (Engine, Suspension and Tires), with 10 levels each, and every vehicle keeps its own levels. Tank size is fixed for each vehicle and can't be upgraded.

| Vehicle | Class | How it drives |
|---|---|---|
| **Ambulance** | All-rounder | Balanced. Reserve O₂ tank once per run. |
| **90s Ambulance** | Old timer | Slow and floaty, cheap to upgrade, reserve O₂ tank. |
| **Police Cruiser** | Speedster | Fast and bouncy with little grip. Hold the special key for nitro. |
| **Fire Engine** | Heavy hauler | Slow and strong. Hold the special key for the water cannon, and put out fires for pills. |
| **Medical Motorcycle** | Daredevil | Tiny and quick with the best air spin. The rider's head is exposed. |
| **Medical Sports Car** | Supercar | The fastest vehicle, sponsored by Back Pain. Almost no grip and a tiny tank. |
| **Medical Snowmobile** | Snow specialist | Light and nimble. Ice doesn't make it slip. |
| **Medical Train** | Slowest of all | Barely moves, but four driven axles drag it up nearly anything, with the biggest tank. |
| **Medical Supply Truck** | Workhorse | Big wheels, strong pull and a decent top speed. |
| **Senior Shuttle Bus** | Top heavy | Slow, tall and bouncy with a full load of seniors. |
| **Rescue Boat** | Water specialist | A boat on a trailer. Water puddles don't slow it. |
| **Moon Lander** | Hopper | Slow on the road. Hold the special key to fly on thrusters. |

## Maps

Each map is one fixed course with its own best distance. Harder maps pay more pills.

| Map | Pills | Character |
|---|---|---|
| **City Day** | ×1 | Hospital district, countryside and mountain pass in daylight. |
| **City Night** | ×1.1 | The same streets after dark. |
| **Highway** | ×1 | Smooth tarmac and long gentle hills, built for speed. |
| **Forest** | ×1.25 | Fallen logs to bounce over and thick woods that slow you down. |
| **Mountain** | ×1.5 | Long, relentless climbs and big drops. |
| **Four Seasons** | ×1.25 | Spring, summer, autumn, then an icy winter. |
| **Beach** | ×1 | Soft sand, palm trees and a sea view. |
| **Puddle Dunes** | ×1.5 | Sand with water puddles that bog you down. |
| **Desert Canyon** | ×1.25 | Dunes with jump ramps and red canyons. |
| **Mud Bog** | ×1.75 | Slippery ground and sticky mud pits. |
| **Crystal Cave** | ×1.75 | Pitch dark underground, lit by headlights and crystals. |
| **Frozen Peaks** | ×1.5 | Steep snowy climbs and a slippery glacier. |
| **Volcano Ridge** | ×2 | Jagged rock, lava and lots of fires. |
| **Stunt Arena** | ×2 | Packed stands and giant dirt ramps. |
| **Roller Coaster** | ×2.25 | Huge drops along a steel track above the park. |
| **Moon Base** | ×2.5 | Low gravity, craters and huge air time. |

## How it works

- **Watch your tank.** It drains as you drive. Refills get farther apart the further you go.
- **Pills are coins.** Red pills are worth 5, blue 10 and gold 25, multiplied by the map's pill bonus. You also earn bonus pills for flips, long air time and putting out fires.
- **Dispatch calls:** three missions at a time for bonus pills. You can swap one after each run.
- **Garage:** the Upgrades, Vehicles, Maps and Calls tabs. Picking a vehicle or map shows it live behind the garage.

Your pills, upgrades, best distances and calls are saved in your browser. **Reset all progress**, under the Drive button in the garage, starts over after asking you to confirm. Each browser keeps its own save.

## Run it

Everything is in one `index.html` file with no build step. The physics engine ([planck.js](https://github.com/piqnt/planck.js), a JavaScript port of Box2D) and the fonts load from public CDNs, so the game needs an internet connection the first time it loads.

- **Locally:** open `index.html` in a browser.
- **GitHub Pages:** push this folder to a repo, go to **Settings → Pages**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.

Adding `?debug` to the URL exposes the game state as `window.__hcr` in the browser console, for playtesting.
