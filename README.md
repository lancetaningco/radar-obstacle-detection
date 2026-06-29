# Radar-Sweep Obstacle Detection System

> A mechanically-scanned ultrasonic sensing system with real-time OpenCV radar visualization, built on an embedded Arduino platform.

<!-- Replace with your demo GIF once the radar display works. Lead with the visual — most people will look at this and never open the source. -->
![Radar visualization demo](media/radar-demo.gif)

---

## Overview

A servo sweeps an ultrasonic distance sensor across a 180° arc. The Arduino streams angle–distance pairs over serial to a Python application that renders a live polar "radar" map with range rings, threat-tier color coding, and persistence trails. The architecture mirrors the core principles behind mechanically-scanned radar and UAV proximity sensing.

<!-- TODO: tighten this to 2–3 sentences in your own words once it's built. -->

## Hardware

| Component | Role |
|-----------|------|
| Arduino UNO | Firmware host, sensor control, serial telemetry |
| HC-SR04 ultrasonic sensor | Distance ranging (digital trigger/echo timing) |
| Servo motor | Mechanical sweep actuation (PWM controlled) |

### Wiring

<!-- Add a photo of your actual rig — it's proof the system physically exists. -->
![Wiring setup](media/wiring.jpg)

| Signal | Arduino Pin |
|--------|-------------|
| Servo signal | _TODO_ |
| HC-SR04 trigger | _TODO_ |
| HC-SR04 echo | _TODO_ |

## How It Works

1. **Sweep & range** — the servo steps across the arc; at each angle the HC-SR04 measures distance via pulse timing.
2. **Telemetry** — the Arduino prints each reading as `angle,distance` over serial.
3. **Visualization** — Python parses the stream and renders the live radar display in OpenCV.

<!-- TODO: expand once each stage is working. -->

## Tech Stack

- **Firmware:** Arduino (C++), PWM servo control, HC-SR04 pulse timing
- **Host:** Python — pyserial, OpenCV, NumPy
- **Visualization:** OpenCV (`cv2.circle`, `cv2.line`, `cv2.putText`, alpha-blended persistence trails)

## Repository Structure

```
.
├── firmware/   # Arduino sketch
├── python/     # Serial reader + OpenCV radar display
├── media/      # Demo GIF, wiring photos
└── README.md
```

## Running It

### Firmware
1. Open the sketch in `firmware/` with the Arduino IDE.
2. Select the Arduino UNO board and the correct port, then upload.

### Python
```bash
cd python
pip install -r requirements.txt
python radar.py
```

## Challenges & Lessons Learned

<!-- Fill this in as you go — this section signals engineering maturity more than the code does. -->
- _TODO: e.g. stabilizing the sensor mount to reduce angular noise_
- _TODO: e.g. tuning serial read timing so the display stays in sync_

## Future Work

- _TODO: e.g. object classification, recording/export pipeline (`cv2.VideoWriter`)_