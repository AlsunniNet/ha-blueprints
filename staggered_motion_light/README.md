# 💡 AlsunniNet - Staggered Motion Light

[![Import Blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FAlsunniNet%2Fha-blueprints%2Fblob%2Fmain%2Fstaggered_motion_light%2Fstaggered_motion_light.yaml)

Automates lighting across single or multiple motion/occupancy sensors with strict range-bound delay controls (0–480 min), protected mode lights, and occupancy flash warnings (1–240 min).

## ⚙️ Inputs

| Input | Requirement | Description |
| :--- | :--- | :--- |
| **Motion / Occupancy Sensors** | Required | One or multiple binary sensors detecting motion/occupancy. |
| **Standard Lights** | Required | Primary lights turned on when motion triggers. |
| **First Light Target to Turn Off** | Required | Target within Standard Lights to turn off after `First Off Delay`. |
| **First Off Delay** | Required | Minutes (**Range: 0–480 min**) to wait before turning off First Light Target. |
| **Second Light Target to Turn Off** | Optional | Target within Standard Lights to turn off after `Second Off Delay`. |
| **Second Off Delay** | Optional | Additional minutes (**Range: 0–480 min**) to wait before turning off Second Light Target. |
| **Mode / Always-On Lights** | Optional | Lights turned on with motion that remain ON when motion clears (protected from turning off). |
| **Occupancy Flash Alert Light** | Optional | Light target to flash when occupancy alert triggers. Leave empty to disable alerts entirely. |
| **Occupancy Warning Interval** | Optional | Minutes of continuous occupancy (**Range: 1–240 min**). **Must be strictly less than First Off Delay.** |

> ⚠️ **Configuration Note:** `Occupancy Warning Interval` must be shorter than `First Off Delay`. If set equal to or longer than `First Off Delay`, the blueprint will log a warning to system logs and bypass flashing.
