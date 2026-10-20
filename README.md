# Newb Aurora Storm

A mobile-friendly shader for **Minecraft Bedrock** (via **MB Loader**), with a vivid northern-lights sky, living storms, per-biome ambience and extra atmosphere for the Nether and the End.

Based on **Newb X Legacy 0.16.56** by devendrn and the Newb Shader contributors (MIT License).
Modified by **Mist TvT**.

> Status: all changes beyond Newb X Legacy are **new and experimental**. Please report anything that looks wrong.

---

## Features

### Sky
- **Richer northern lights**: two drifting curtains, a green > violet > teal palette with a crimson-pink fringe, slow pulsing and moving ray shimmer
- **Aurora ground glow**: at night the aurora colours softly light the world
- **Sun and moon sway** slightly so the sky feels alive
- Soft clouds by default (cheap and pretty)

### Weather
- **Gloomy rain**: outdoor scenes darken while it rains so the rain stands out
- **Clearer rain streaks** and a **bright splash** where rain meets the ground
- **Snowflakes dissolve** softly just above the ground
- **Storm wind**: plants, leaves and lanterns sway harder as rain increases
- **Storm waves**: water gets rougher during rain

### Quality of life
- **Twilight mist**: a soft golden mist at sunrise and sunset
- Slightly more vivid colours by default (`NL_SATURATION`)

### Light
- **Warm glow around torches and other light sources**, plus a soft warm haze in the fog around them

### Biome ambience (experimental)
| Biome | Effect |
|---|---|
| Desert | Warm orange/yellow tint with sandy dust in the air |
| Swamp / Mangrove swamp | Thick greenish mist |
| Birch forest | Extremely sunny: brighter, warmer light and clearer air |
| Pale garden | White-out fog; glowing mob eyes stay visible in it |
| Deep dark | Darker, colder fog and lighting |
| Snowy biomes | Cold, crisp bluish air |
| Jungle / bamboo jungle | Humid green haze |
| Badlands (mesa) | Red dust and warm light |
| Cherry grove | Dreamy pink haze |
| Mushroom fields | Purple spore haze |

### Other dimensions
- **Nether**: warm ember haze in the fog
- **The End**: deeper purple void haze

### Performance
- Lighter defaults: shorter wave range, and the extra cloud layer is off
- **Lite subpack** for low-end phones: turns off waves, shimmer, rainbow, shooting stars, cloud shadow, extra fog effects, rain splash, snow dissolve, torch haze and more
- Biome detection uses a cheap colour comparison (no square roots)

---

## Install (Android)

1. Install **MB Loader** (Minecraft Bedrock Loader) and open Minecraft **through MB Loader**.
2. Open the `.mcpack` file to import it.
3. Go to **Settings > Global Resources** and activate **Newb Aurora Storm**.
4. Open the pack's settings to choose a subpack:
   - **Default**: full effects
   - **Lite**: best for low-end phones
   - **Biome Debug**: tints blocks per detected biome (see Troubleshooting)

Requires Minecraft Bedrock **1.26.50 or newer**.

---

## Settings

All options are in `src/newb/config.h`. Each line has a comment with its range. Useful ones:

| Setting | What it does |
|---|---|
| `NL_AURORA`, `NL_AURORA_COL1/2/3/4`, `NL_AURORA_SHIMMER`, `NL_AURORA_LAYER2`, `NL_AURORA_GLOW` | Northern lights brightness, palette, shimmer, second curtain, ground glow |
| `NL_TWILIGHT_MIST`, `NL_SATURATION` | Sunrise/sunset mist, colour vividness |
| `NL_RAIN_GLOOM`, `NL_RAIN_CLARITY`, `NL_RAIN_SPLASH` | Rain look |
| `NL_SNOW_DISSOLVE`, `NL_SNOW_DISSOLVE_HEIGHT` | Snow fade near the ground |
| `NL_STORM_WIND`, `NL_STORM_WATER_BUMP` | Storm strength |
| `NL_TORCH_GLOW`, `NL_TORCH_HAZE` | Light source warmth |
| `NL_CELESTIAL_WOBBLE` | Sun/moon sway in degrees |
| `NL_DESERT_HAZE`, `NL_SWAMP_MIST`, `NL_BIRCH_SUN`, `NL_PALE_FOG`, `NL_DEEPDARK_DARKEN`, `NL_SNOW_BIOME`, `NL_JUNGLE_HUMID`, `NL_BADLANDS_DUST`, `NL_CHERRY_DREAM`, `NL_MUSHROOM_SPORE` | Biome strength (0.0 turns one off) |
| `NL_NETHER_EMBER`, `NL_END_VOID` | Nether and End haze |

Comment out a line with `//` to turn an effect off. To save performance, turn off the effects you don't need.

---

## Build from source (GitHub, no PC needed)

1. Fork this repository on GitHub.
2. Edit `src/newb/config.h` (or upload changed files).
3. Open **Actions > build > Run workflow**, choose **Android**, run, and download the artifact.
4. Zip the downloaded pack folder (if needed), rename it to `.mcpack`, and import it with MB Loader.

On a PC you can instead run:

```
./build.sh setup
./build.sh pack -p android -v 1
```

(Requires Python 3 and `pip install -r requirements.txt`.)

---

## Troubleshooting

- **Biome effects don't show.** Biomes are detected from custom fog colours set in `assets/biomes_client.json` and `assets/fogs/`. If Minecraft ignores them, the effects stay off. Pick the **Biome Debug** subpack and walk through the biomes: red = desert, green = swamp, yellow = birch, white = pale garden, blue = deep dark, cyan = snowy, orange = jungle, dark red = badlands, magenta = cherry grove, purple = mushroom fields. If nothing tints, the detection is not working on your Minecraft version, please report it.
- **Pale garden eyes don't glow.** This assumes the Creaking's eyes use Minecraft's emissive material. If they don't, only the white fog applies.
- **Lag.** Use the **Lite** subpack, lower `NL_WAVE_RANGE`, comment out `NL_AURORA_LAYER2`, or comment out `NL_AURORA`.
- **Odd fog colours without the shader.** The pack changes some biome fog colours so the shader can detect biomes. Load the pack only together with MB Loader.
- **Black or pink blocks.** Your Minecraft version may be unsupported or a shader failed to compile. Send a screenshot and your device model.

---

## License and credits

- Shader source is under the **MIT License** (see `LICENSE`), originally by **devendrn** and **Newb Shader contributors**: https://github.com/devendrn/newb-x-mcbe
- Modifications by **Mist TvT**.
- This pack is not affiliated with Mojang or Microsoft.
