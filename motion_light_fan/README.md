# 🏛️ AlsunniNet | Lights and Fans Control

The ultimate "Universal Pro Suite" blueprint. This automation manages lighting and climate dynamically based on your available sensors, ensuring energy efficiency and comfort.

## 🚀 Key Logic
- **Multi-Motion Trigger:** Supports one or multiple sensors. Lights and fans turn on instantly upon detection.
- **Lux Sensitivity:** Smart lighting logic prevents lights from turning on if the room is already bright enough from natural sunlight.
- **Climate Intelligence:** Fans can trigger automatically if humidity or temperature exceeds your thresholds, even without motion.
- **Dual-Stage Timeout:** After leaving, lights turn off quickly to save power, while the fan continues to run to clear the air.
- **Safety Cutoff:** Features a **Maximum Run Time** (adjustable 1–12h) that force-stops the fan to prevent it from running indefinitely if a sensor gets stuck.

## ⚙️ Requirements
- **Required:** Motion/Occupancy Sensor(s), Light(s).
- **Optional:** Fan(s), Lux Sensor, Humidity Sensor, Temperature Sensor, Door/Window Sensors.

## 🛠️ Configuration Tips
1. **Light Off Delay:** Set this for how long you want the lights to stay on after the last motion is detected.
2. **Fan Extra Run Time:** Set this for how many minutes you want the fan to keep clearing the air *after* the lights go out.
3. **Max Run Time:** Set this as your "safety net." If you set this to 4 hours, the fan will turn off no matter what once that limit is reached (unless motion resets the timer).

---
*Brought to you by AlsunniNet — Quality Automations for a Smarter Future.*
