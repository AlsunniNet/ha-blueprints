# AlsunniNet | Smart Water Heater Control

## Description
This automation turns your water heater on/off based on a flexible schedule (fixed time window or calendar events), a minimum outdoor temperature, and optional water temperature readings. It also enforces a maximum daily runtime to save energy.

## Features
- Supports **any water heater entity** – switch, climate, water_heater, or any other device that can be turned on/off.
- **Two scheduling modes**:
  - Fixed daily time window (e.g., 06:00 – 20:00)
  - Calendar‑based (the automation runs when a calendar event is active)
- **Outdoor temperature lockout** – heater only runs when outside temperature is above a user‑defined threshold.
- **Water temperature control (optional)** – turns on when water drops below a minimum, turns off when it reaches a maximum.
- **Run time management** – configurable desired run time per cycle.
- **Maximum daily runtime limit** – prevents excessive energy use.
- **Boost mode** – a helper switch that forces one heating cycle ignoring schedule & weather.

## Requirements
- Home Assistant **2023.8 or later** (blueprint YAML format)
- An entity that controls your water heater (e.g., `switch.boiler_relay`, `climate.boiler`, `water_heater.hot_water`)
- (Optional) A temperature sensor for outdoor temperature (e.g., `sensor.weather_temperature`)
- (Optional) A temperature sensor for water temperature (e.g., `sensor.water_heater_temperature`)
- (Optional) An `input_boolean` helper for boost mode
- (Optional) An `input_number` helper for tracking daily runtime (if you want daily limits)

## Installation
1. Go to **Settings → Automations & Scenes → Blueprints**.
2. Click **Import Blueprint**.
3. Paste the raw URL of the blueprint YAML file:  
   `https://raw.githubusercontent.com/AlsunniNet/ha-blueprints/main/water_heater_scheduler/water_heater_scheduler.yaml`
4. Click **Preview** and then **Import**.
5. Create a new automation from this blueprint.

## Configuration Example
- **Water Heater Entity**: `switch.boiler`
- **Outdoor Sensor**: `sensor.outdoor_temperature`
- **Minimum Outdoor Temp**: `5` °C
- **Schedule Type**: `Fixed Time Schedule`
- **Start Time**: `06:00:00`
- **End Time**: `21:00:00`
- **Desired Run Time**: `60` minutes
- **Maximum Daily Runtime**: `120` minutes

## Boost Mode Setup
1. Create a **Toggle** helper (`Settings → Devices & Services → Helpers → + Add Helper → Toggle`). Name it, e.g., `Water Heater Boost`.
2. In the blueprint, enable **Enable Boost Button** and select that toggle.
3. Turning the toggle ON will force the heater to run for one full cycle (respecting the desired run time and water temperature limits, but ignoring schedule and outdoor temperature). The toggle will automatically turn OFF after the cycle finishes.

## Troubleshooting
| Symptom | Likely fix |
|---------|-------------|
| Heater never turns on | Check outdoor temperature vs. min threshold; verify schedule window; ensure water temperature (if used) is below the minimum. |
| Daily counter not resetting | Confirm the reset time is set correctly and the `input_number` helper is selected. |
| Boost mode doesn't work | The `input_boolean` must be selected in the blueprint and the boost toggle must be turned ON. |
| Water temperature control not working | The sensor must be numeric and report in °C; re‑save the automation after adding the sensor. |

## Version History
- **1.0.0** – Initial release (2025‑04‑27)

## Support
Open an issue at [https://github.com/AlsunniNet/ha-blueprints/issues](https://github.com/AlsunniNet/ha-blueprints/issues)
