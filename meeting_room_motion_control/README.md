# Meeting Room Motion Control Blueprint

A comprehensive Home Assistant blueprint for meeting rooms that turns lights (and optionally air conditioning) on/off based on motion, with special care for long static meetings, door/window sensors, media player states, and mood lighting to avoid complete darkness.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint url](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/AlsunniNet/ha-blueprints/blob/main/blueprints/meeting_room_motion_control/meeting_room_motion_control.yaml)

## Features

- **Motion‑based control** – turns on main lights when motion is detected.
- **Long, configurable timeout** – prevents lights turning off while people are seated and talking (default 1 hour).
- **Manual override switch** – a helper that, when ON, completely disables auto‑off (useful for very long meetings).
- **Ambient brightness threshold** – only turn on lights if the room is actually dark (optional).
- **Air conditioning integration** – turns AC to cool mode when temperature rises above a threshold, and off after no motion.
- **Media player awareness**:
  - Option to prevent turning on lights while a media player is playing (e.g., during a presentation).
  - Option to prevent auto‑off unless the media player has been off for a specified time.
- **Door/window sensor support**:
  - Treat door open as motion (turn on lights immediately).
  - Prevent auto‑off while the door is closed (keeps the room alive when people are inside but motionless).
- **Mood lighting** – a separate set of lights that stay on at low brightness whenever the main lights are off, so the room is never pitch dark.

## Requirements

- Home Assistant **2024.6** or later (uses blueprint features like `enabled` on triggers and conditions).
- Motion sensor entity (`binary_sensor` with device class `motion`).
- Lights (any `light` entities).
- (Optional) Climate device, temperature sensor, media player, contact sensor, illuminance sensor, input_boolean.

## Installation

1. Click the **"Import Blueprint"** badge above, or manually go to **Settings → Automations & Scenes → Blueprints → Import Blueprint** and paste the raw URL of the YAML file.
2. After import, create a new automation from this blueprint.
3. Fill in the required inputs (motion sensor and main lights). All others are optional.

## Inputs

| Input | Required | Description |
|-------|----------|-------------|
| `motion_sensor` | ✅ | Binary sensor that detects motion. |
| `light_target` | ✅ | Main lights that turn on/off fully. |
| `delay_off` | ❌ | How long to keep lights/AC on after last motion (default 1 hour). |
| `manual_override` | ❌ | Input boolean that, when `on`, prevents auto‑off. |
| `brightness_sensor` | ❌ | Illuminance sensor to check ambient light. |
| `brightness_threshold` | ❌ | Lux threshold – lights only turn on if below this (default 50). |
| `climate_entity` | ❌ | Climate device (AC/thermostat). |
| `temperature_sensor` | ❌ | Temperature sensor – if not set, uses climate entity’s current temperature. |
| `ac_threshold` | ❌ | Temperature above which AC turns on (default 24°C). |
| `ac_target_temp` | ❌ | Target temperature for AC (default 22°C). |
| `media_player` | ❌ | Media player entity to check. |
| `media_player_off_state` | ❌ | State considered “off” (default `off`). |
| `media_player_auto_off` | ❌ | If true, auto‑off only happens after media player has been off for the specified delay. |
| `media_player_off_delay` | ❌ | How long media player must stay off before auto‑off is allowed. |
| `contact_sensor` | ❌ | Door/window binary sensor. |
| `contact_triggers_motion` | ❌ | If true, opening the contact acts as motion (turns on lights). |
| `contact_prevents_auto_off` | ❌ | If true, auto‑off is blocked while contact is closed (door shut). |
| `mood_lights` | ❌ | Lights that stay on at low brightness when main lights are off. |
| `mood_brightness` | ❌ | Brightness percentage (1-100) for mood lights (default 10%). |
| `mood_turn_off_during_meeting` | ❌ | If true (default), mood lights turn off when motion is detected. |

## How it works

1. **When motion is detected** (or contact opens if enabled):
   - Main lights turn on.
   - Mood lights turn off (if configured).
   - If temperature > threshold, AC turns on (cool mode, target temperature).
   - The manual override boolean is turned off automatically (if it was on) so the room can later auto‑off.

2. **When no motion is detected for the configured delay** (and none of the overrides block it):
   - Main lights turn off.
   - AC turns off.
   - Mood lights turn on at the configured low brightness.

The following **block auto‑off** (in order of evaluation):
- Manual override switch is `on`.
- Contact sensor prevents auto‑off (if enabled) and contact is closed.
- Media player auto‑off condition (if enabled) – the player hasn’t been off long enough.

## Example use cases

- **Long meeting with static participants** – set `delay_off` to 90 minutes, or use a manual override switch.
- **Prevent lights turning on during a video presentation** – set `media_player` to the presentation device, `media_player_off_state` to `off`; lights will only turn on when the player is off.
- **Keep room alive while door is closed** – enable `contact_prevents_auto_off` and use a door sensor. As long as the door remains shut, lights stay on even if motion stops.
- **Never walk into a dark room** – configure `mood_lights` to a dim strip. The room will always have a gentle glow when empty.

## Troubleshooting

- **Lights turn off too quickly** – increase `delay_off` or use a manual override.
- **Lights don’t turn on when motion is detected** – check brightness threshold (maybe the room is too bright), or media player condition (player may be on).
- **AC doesn’t turn on** – verify temperature sensor or climate entity is working, and that the threshold is set correctly.
- **Mood lights stay on during meeting** – set `mood_turn_off_during_meeting` to `true`.

## Contributing

Feel free to open issues or pull requests on the [GitHub repository](https://github.com/AlsunniNet/ha-blueprints).

## License

[MIT License](LICENSE)