# **HydroSmart**

## A Smart Water Management & Automated Distribution System
An intelligent water management platform that automates tank filling, overflow prevention, water quality monitoring, automatic water renewal, and safe contactless dispensing; built for Nigerian households, schools, and businesses.




**Team HydroTitans**
- Emmanuel Onakoya: Hardware Systems Engineer
- Glory Akanbi: Embedded Systems Engineer
- Adenike Adewumi: Product Design & Research Engineer

---

## Project Overview

Millions of Nigerian households struggle daily with water: tanks overflow unnoticed, pumps run dry or flood tanks after power returns, stored water quality goes unmonitored, and manual taps waste thousands of litres a year. HydroSmart is a portable, external add-on that fits onto existing household water tanks — no structural modifications required and automates the full water management cycle using embedded sensing and intelligent control.

## Problem Statement

Most households still rely on manual monitoring of overhead tanks. This leads to:

- Tank overflow when pumps are left running
- Unexpected water shortages with no real-time level visibility
- Unknown water quality — sediment and contamination go undetected
- Water and electricity wastage from poor pump control
- Frequent pump damage from dry-running
- No remote monitoring or notifications

Existing solutions only address part of the problem. Float switch systems automate pump on/off but offer no quality monitoring, no contamination alerts, and no notifications. Manual monitoring has zero upfront cost but is unreliable, not scalable, and provides no quality checks at all. The market needs one integrated, intelligent platform — that's HydroSmart.

## Objectives

- Prevent water overflow 
- Monitor water quality in real time
- Automate water renewal when stored water becomes stagnant or contaminated
- Reduce water and electricity wastage
- Enable safe, contactless water dispensing
- Improve user convenience through smart notifications
- Extend pump lifespan
- Provide an easy, non-invasive installation path for existing tanks

## Key Features

- Automatic pump control — fills tank automatically, stops at capacity
- Water quality monitoring via turbidity sensors
- Automatic water renewal when contamination/staleness threshold is exceeded
- Contactless dispensing with 5-second verification delay to prevent accidental activation
- LED status indication
- Expandable IoT architecture for future cloud/mobile integration

## Competitive Comparison

| Feature | Float Switch | Manual | HydroSmart |
|---|---|---|---|
| Automatic Pumping | ✓ | ✗ | ✓ |
| Water Quality Monitoring | ✗ | ✗ | ✓ |
| Auto Water Renewal | ✗ | ✗ | ✓ |
| Contactless Dispensing | ✗ | ✗ | ✓ |
| Smart Notifications | ✗ | ✗ | ✓ |
| Easy Installation | ✓ | ✓ | ✓ |
| Low Maintenance | ✓ | ✓ | ✓ |

## System Architecture

```
                    Water Tank (External Mount)
                              │
              ┌───────────────┴───────────────┐
              │                                │
     Ultrasonic Level Sensor           Turbidity Sensor
              │                                │
              └───────────────┬────────────────┘
                              │
                      Arduino Control Box
                              │
                    Decision Algorithm
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                      │
   Relay → Pump      Contactless Dispenser      LED Alerts
                              

Future expansion:  Arduino → ESP32 → WiFi → Cloud Database → Mobile App
```

### Key Engineering Decisions

- **External calibration mechanism** — measures water level from outside the tank, no drilling required
- **Dedicated control box** — all electronics enclosed for protection and easy maintenance
- **Sensor-based automation** — decisions driven by live sensor data, not timers or manual input
- **Contactless tap delay** — 5-second verification before release reduces accidental activation

## Hardware Components

| Component | Purpose |
|---|---|
| Arduino Uno | Main controller |
| Water Sensor | Water level detection |
| Turbidity Sensor | Water quality / contamination monitoring |
| Relay Module | Pump switching |
| Water Pump | Tank filling and water renewal |
| LEDs | System status and alerts |
| Power Supply | System power |
| Ultrasonic Sensor | Human Prescence detection |

## Software Stack

- Arduino IDE
- Embedded C/C++
- Git / GitHub

**Planned for future iterations:**
- ESP32 (WiFi-enabled controller)
- MQTT
- Firebase / cloud database
- Mobile app (Blynk or custom)

## Working Principle

1. Measure tank water level (water sensor)
2. Detect water quality (turbidity sensor)
3. Determine tank status (empty / filling / full)
4. Activate relay to run pump as needed
5. Pump fills tank or triggers water renewal if water is stagnant/contaminated
6. Pump stops automatically at full level
7. Contactless dispenser releases water after 5-second verification
8. LEDs/buzzer indicate current status; notifications sent to user

### Flowchart

```
Start
  ↓
Initialize Sensors
  ↓
Read Water Level + Water Quality
  ↓
Tank Full? ──No──→ Pump ON
  │
 Yes
  ↓
Pump OFF
  ↓
Water Stagnant/Contaminated? ──Yes──→ Trigger Auto Renewal/Drain contaminated water out
  ↓
Display Status
  ↓
Repeat
```

## Prototype Status — Tested & Validated

**What we proved:**
- Automatic pump control — fully operational
- Sensor integration (level + quality) — functioning
- Contactless dispensing (trigger + delay) — working
- End-to-end automation — system ran without manual input

## Folder Structure

```
HydroSmart/
│
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── .gitignore
│
├── Arduino_Code/
│   ├── main.ino
│   ├── sensors.cpp
│   ├── relays.cpp
│   ├── dispenser.cpp
│   └── config.h
│
├── Circuit_Diagrams/
├── CAD/
├── PCB_Design/
├── Images/
├── Videos/
├── Results/
├── Test_Reports/
├── Documentation/
├── Presentation/
├── Datasheets/
└── Bill_of_Materials/
```

## Installation

### Hardware Setup
Connect the Arduino, relay module, ultrasonic sensor, turbidity sensor, pump, water sensor, and LEDs according to the wiring diagram in `Circuit_Diagrams/`. Mount the control box externally on the tank — no structural modification needed.

### Software Setup
```bash
git clone https://github.com/yourusername/HydroSmart.git
```
Open `Arduino_Code/main.ino` in the Arduino IDE and upload it to the Arduino Uno.

### Pin Configuration

| Component | Arduino Pin |
|---|---|
| Ultrasonic Trigger | D4 |
| Ultrasonic Echo | D5 |
| Turbidity Sensor | A0 |
| Pump Relay | D8 |
| Dispenser Relay | D7 |
| Green LED | D9 |
| Yellow LED | D10 |
| Red LED | D11 |
| Buzzer | D12 |


## Test Cases

| Test | Expected Result |
|---|---|
| Empty Tank | Pump starts |
| Tank Full | Pump stops |
| Water Overflow Attempt | Pump OFF, alert raised |
| Dry Tank | Dry-run protection enabled |
| Contaminated/Stagnant Water | Auto-renewal triggered, alert generated |
| Dispenser Touch | 5-second delay before release |

## Scalability

HydroSmart is designed for affordable, wide-scale deployment:

- 200M+ Nigerians potentially affected
- Zero tank modifications needed
- Fits any existing household tank
- Simple external installation by a technician
- Low maintenance — sealed control box, minimal moving parts
- Affordable relative to replacing entire water systems

**Target segments:** Residential homes, schools & hostels, small businesses, estate facilities.

## Alignment with Global Sustainable Development Goals

- **SDG 6** — Clean Water & Sanitation: safer water storage, automated quality control, reduced wastage
- **SDG 3** — Good Health & Well-being: prevents exposure to contaminated or stagnant water
- **SDG 11** — Sustainable Cities & Communities: builds resilient, efficient household water infrastructure
- **SDG 12** — Responsible Consumption & Production: reduces water and energy waste through smart automation

## Future Improvements

- Mobile application
- WiFi monitoring via ESP32
- GSM notifications
- Solar-powered operation
- AI-based water usage prediction
- Leak detection
- Predictive maintenance
- Smart billing
- Cloud dashboard

## Results

*(Add photographs/GIFs showing: prototype, circuit, water level tests, pump operation, overflow prevention, water quality monitoring, contactless dispensing in action.)*

## Contributors

| Name | Role |
|---|---|
| Emmanuel Onakoya | Hardware Systems Engineer |
| Glory Akanbi | Embedded Systems Engineer |
| Adenike Adewumi | Product Design & Research Engineer |

## License

Choose an appropriate license such as the MIT License if you want others to use and build upon this work.
