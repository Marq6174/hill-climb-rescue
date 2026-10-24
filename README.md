# Hill Climb Rescue

A medical take on Hill Climb Racing. You drive an ambulance over endless hills with real physics, keep the oxygen tank from running dry, collect pills, land flips, and upgrade your rig in the garage between runs.

## Controls

| Action | Keyboard | Touch |
|---|---|---|
| Gas | `D` | **Gas** pedal (bottom right) |
| Brake / reverse | `A` | **Brake** pedal (bottom left) |
| Tilt back | `←` | Round button next to the brake |
| Tilt forward | `→` | Round button next to the gas |
| Siren | `H` | Siren button (top right) |
| Pause | `Esc` or `P` | Pause button (top right) |
| Sound / music | `M` / `N` | Buttons in the garage and pause menu |

In the garage, press `D` or `Enter` to start driving.

## How it works

- **Oxygen is your fuel.** The O₂ tank drains as you drive. Grab green O₂ canisters to refill it. They get farther apart the deeper you go.
- **Pills are coins.** Red pills are worth 5, blue 10 and gold 25. You also earn bonus pills for backflips, frontflips and long air time.
- **Don't roll over.** If the ambulance lands on its roof, the run is over.
- **Garage upgrades:**
  - **Engine:** more top speed and power
  - **Suspension:** softer landings
  - **Tires:** more grip on steep slopes
  - **O₂ Tank:** oxygen lasts longer
- **Four areas** blend into each other as you drive: Hospital District, Countryside (450 m), Mountain Pass (1,200 m) and Night Highway (2,200 m).
- **One fixed course**, the same every run, so you can learn it. A red "BEST" flag marks your record distance.
- **Bedside details:** a speedometer and a patient heart-rate gauge that spikes on hard bumps, plus an incident report at the end of every run.
- **Sound:** engine noise follows your throttle, plus a two-tone siren, pickup and stunt sounds, crash sounds and a music loop. Everything is generated live with the Web Audio API, so there are no audio files.

Your pills, upgrades and best distance are saved in your browser.

## Run it

Everything is in one `index.html` file with no build step. The physics engine ([planck.js](https://github.com/piqnt/planck.js), a JavaScript port of Box2D) and the fonts load from public CDNs, so the game needs an internet connection the first time it loads.

- **Locally:** open `index.html` in a browser.
- **GitHub Pages:** push this folder to a repo, go to **Settings → Pages**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.
