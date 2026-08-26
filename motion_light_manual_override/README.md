# Motion-Activated Light with Manual Switch Override

Automation blueprint for Home Assistant that controls lighting based on motion or occupancy sensors while respecting manual switch overrides.

## Features

- **Multi-Sensor Support:** Trigger lights using one or multiple motion or occupancy sensors.
- **Flexible Off Delay:** Adjustable timeout slider ranging from 0 minutes to 8 hours.
- **Manual Override:** Halts automatic light shut-off if a physical switch or manual state change occurs during the wait period.

## Installation

1. Import this blueprint into your Home Assistant instance using the raw URL of `motion_light_manual_override.yaml`.
2. Create a new automation from the imported blueprint.
3. Select your desired motion sensor(s), target light(s), and off-delay duration.
