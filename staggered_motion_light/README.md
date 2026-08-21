# 💡 Staggered Motion Light with Mode Lights

[![Import Blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FAlsunniNet%2Fha-blueprints%2Fblob%2Fmain%2Fstaggered_motion_light%2Fstaggered_motion_light.yaml)

Turns on primary lights and optional mode lights upon motion or occupancy detection. When motion stops, it turns off two target light sets on separate timers while maintaining state for always-on mode lights.

## ⚙️ Inputs

| Input | Type | Description |
| :--- | :--- | :--- |
| **Motion / Occupancy Sensor** | Entity | Binary sensor detecting motion or occupancy. |
| **Standard Lights** | Target | Primary lights turned on when motion is triggered. |
| **First Light Target to Turn Off** | Target | Light(s) to turn off after `First Off Delay`. |
| **First Off Delay** | Seconds | Delay before turning off the first light set. |
| **Second Light Target to Turn Off** | Target | Light(s) to turn off after `Second Off Delay`. |
| **Second Off Delay** | Seconds | Additional delay before turning off the second light set. |
| **Mode / Always-On Lights** | Target | Optional lights triggered on motion that stay ON indefinitely. |
