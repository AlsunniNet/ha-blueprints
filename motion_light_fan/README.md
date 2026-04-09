# 💡 AlsunniNet: Motion Light & Delayed Fan Off

A smart occupancy automation designed for bathrooms and utility rooms where you want light immediately, but ventilation to persist after you leave.

## ✨ Key Features
* **Area-Based Control:** Automatically targets all lights and fans within a chosen Home Assistant Area.
* **Dual-Stage Timeout:** The light turns off first to save energy, while the fan continues to run for a custom duration (default 30 min) to clear humidity.
* **Smart Scheduling:** Built-in time and weekday filters to ensure the automation only runs when needed.
* **Restart Logic:** If motion is re-detected while the fan is in its "extra run time" phase, the light turns back on and the timers reset.

## 🛠️ Configuration
1. **Motion Sensor:** Select your binary sensor (e.g., `binary_sensor.bathroom_motion`).
2. **Target Area:** Select the area (e.g., `Women's Bathroom`).
3. **Light Off Delay:** How long after the sensor goes "Clear" should the light turn off?
4. **Fan Extra Run Time:** How many minutes *after* the light turns off should the fan stay on?

---
*Part of the AlsunniNet Home Assistant Suite.*
