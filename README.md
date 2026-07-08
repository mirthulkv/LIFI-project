# 📡 Wireless Audio Transmission Using Li-Fi Technology

> A low-cost, laser-based optical wireless communication system that transmits live audio using **Light Fidelity (Li-Fi)** principles — modulating a laser beam with sound and demodulating it at the receiver using a solar panel.


---

## 📖 Table of Contents

- [Overview](#-overview)
- [Demo](#-demo)
- [How It Works](#-how-it-works)
- [System Architecture](#-system-architecture)
- [Components (Bill of Materials)](#-components-bill-of-materials)
- [Circuit Diagrams](#-circuit-diagrams)
- [Repository Structure](#-repository-structure)
- [Build Instructions](#-build-instructions)
- [Testing & Calibration](#-testing--calibration)
- [Results](#-results)
- [Li-Fi vs Wi-Fi](#-li-fi-vs-wi-fi)
- [Advantages & Disadvantages](#-advantages--disadvantages)
- [Applications](#-applications)
- [Future Scope](#-future-scope)
- [Safety Notes](#-safety-notes)
- [Team](#-team)
- [References](#-references)


---

## 🔍 Overview

This project demonstrates a simplified **Li-Fi (Light Fidelity)**–based audio transmission system built using a **laser diode** and a **solar panel**, developed as part of the *BECE304L – Analog Communication Systems* course (Winter Semester 2024–25) at **Vellore Institute of Technology (VIT)**.

Live audio is captured by a microphone, amplified, and used to modulate the **intensity of a laser beam**. This modulated light travels through free space to a receiver, where a small **solar panel** acts as an unconventional photodetector, converting the light intensity variations back into an electrical audio signal — which is then amplified and played through a speaker.

The project validates that **inexpensive, readily available components** can be used to build a working optical wireless communication link, and specifically highlights the **viability of a solar panel as a Li-Fi receiver**, as an alternative to a traditional photodiode.

---

## 🎥 Demo

A working demonstration of the system (transmitter → laser link → receiver → speaker) is available here:

🔗 **[Watch the working demo](https://drive.google.com/file/d/1GRu8-7CUCw4oxxqnaBfl8eLSfCSe_MrF/view?usp=drivesdk)**

> Add your own demo photos/videos to the [`images/`](images) folder and link them here for a self-contained repository.

---

## ⚙️ How It Works

1. **Sound → Electrical Signal**: A microphone module captures ambient audio and converts it into a small analog electrical signal.
2. **Amplification**: The weak mic signal is boosted by a Class-D audio amplifier so it's strong enough to drive the laser modulation stage.
3. **Intensity Modulation**: The amplified audio signal varies the drive current of a laser diode — the *brightness* of the laser beam fluctuates in step with the sound wave (this is **analog intensity modulation**, the optical equivalent of AM).
4. **Free-Space Optical Transmission**: The modulated laser beam travels through the air to the receiver. A clear line-of-sight is required.
5. **Light → Electrical Signal**: A small solar panel at the receiver acts as a photodetector — it generates a varying voltage proportional to the incoming light intensity, effectively demodulating the optical signal back into an audio-frequency electrical signal.
6. **Amplification & Playback**: This recovered signal is amplified again and played back through a speaker, reproducing the original sound.

```
🎤 Mic  →  🔊 Pre-Amp  →  📈 Laser Intensity Modulation  →  🔦 Laser Beam (free space)
                                                                     │
                                                                     ▼
🔈 Speaker  ←  🔊 Amp  ←  🎚️ Volume Pot  ←  ☀️ Solar Panel (Photodetector / Demodulator)
```

---

## 🏗 System Architecture

The system is split into two independent units, each with its own regulated power supply:

### Transmitter Section
| Stage | Component | Function |
|---|---|---|
| Power | 9V battery + LM7805 | Regulates 9V → stable 5V |
| Audio capture | MAX4466 mic module | Converts sound → electrical signal |
| Amplification | PAM8403 amplifier | Boosts signal for laser modulation |
| Optical output | HW-493 laser diode module | Intensity-modulates the laser beam with audio |

### Receiver Section
| Stage | Component | Function |
|---|---|---|
| Power | 9V battery + LM7805 | Regulates 9V → stable 5V |
| Light detection | Solar panel (photovoltaic sensor) | Converts light intensity variation → electrical signal |
| Volume control | 100kΩ potentiometer | Adjusts signal level into the amplifier |
| Amplification | PAM8403 amplifier | Boosts recovered signal |
| Playback | 8Ω, 15W speaker | Converts electrical signal → sound |

---

## 🧰 Components (Bill of Materials)

| # | Component | Qty | Role |
|---|---|---|---|
| 1 | MAX4466 Electret Microphone Amplifier Module | 1 | Captures ambient audio, low-noise adjustable-gain preamp |
| 2 | PAM8403 Class-D Audio Amplifier Module (w/ potentiometer) | 2 | Amplifies mic signal (Tx) and recovered signal (Rx) |
| 3 | HW-493 Laser Diode Module | 1 | Emits laser beam, intensity-modulated by audio |
| 4 | Small Solar Panel (Photovoltaic Sensor) | 1 | Acts as the optical receiver / demodulator |
| 5 | 8Ω, 15W Speaker | 1 | Converts recovered electrical signal to sound |
| 6 | 9V Battery | 2 | Primary power source (1 per section) |
| 7 | LM7805 Voltage Regulator | 2 | Steps down 9V → regulated 5V (1 per section) |
| 8 | 100kΩ Potentiometer | 1 | Manual volume/gain control on the receiver |
| — | Breadboard, jumper wires, connectors | — | Prototyping hardware |

> 💡 See [`docs/components.md`](docs/components.md) for detailed datasheunderstanding notes on each part.

---

## 🔌 Circuit Diagrams

Recreated schematic-level diagrams are provided as vector images in [`images/`](images):

- [`images/transmitter-circuit.svg`](images/transmitter-circuit.svg) — Power supply + Transmitter section (Mic → Amp → Laser)
- [`images/receiver-circuit.svg`](images/receiver-circuit.svg) — Power supply + Receiver section (Solar Panel → Pot → Amp → Speaker)

See [`docs/circuit-diagrams.md`](docs/circuit-diagrams.md) for pin-level wiring notes.

---

## 📁 Repository Structure

```
LiFi-Audio-Transmission/
├── README.md                     ← You are here
├── LICENSE
├── .gitignore
├── docs/
│   ├── methodology.md            ← Full build methodology (Tx/Rx design, testing, safety)
│   ├── components.md             ← Detailed component notes / datasheet summaries
│   ├── circuit-diagrams.md       ← Wiring/pinout explanation for the diagrams
│   └── results.md                ← Results, discussion, Li-Fi vs Wi-Fi comparison
├── hardware/
│   └── bill-of-materials.csv     ← BOM in spreadsheet-friendly format
└── images/
    ├── transmitter-circuit.svg   ← Recreated Fig 1 (Transmitter circuit diagram)
    ├── receiver-circuit.svg      ← Recreated Fig 2 (Receiver circuit diagram)
    ├── transmitter-photo.jpg     ← 📷 Add your own hardware photo here
    └── receiver-photo.jpg        ← 📷 Add your own hardware photo here
```

---

## 🛠 Build Instructions

1. **Assemble the power section** on both breadboards: 9V battery → LM7805 → filter capacitors → regulated 5V rail + GND.
2. **Transmitter**: Wire the MAX4466 mic module's `OUT` pin to the `IN.L`/`IN.COM` of the PAM8403 amplifier. Connect the amplifier's output (`OUT.L+ / OUT.L-`) to the laser diode module's signal input instead of a speaker, so the laser intensity is driven by the audio waveform.
3. **Receiver**: Connect the solar panel's leads to the `IN.L`/`IN.COM` of a second PAM8403 amplifier through the 100kΩ potentiometer (wired as a variable voltage divider for volume control). Connect the amplifier output to the 8Ω speaker.
4. **Align** the laser diode and solar panel so the beam falls directly on the solar cell — this is the most sensitive step; even small misalignment attenuates the signal significantly.
5. **Power on** both sections and speak/play sound near the microphone — audio should be audible from the receiver speaker.

> ⚠️ See [Safety Notes](#-safety-notes) before powering on the laser.

---

## 🧪 Testing & Calibration

- **Alignment & Range Testing**: The laser and solar panel were tested at multiple distances and angles to determine the working range and tolerance for misalignment.
- **Audio Quality Assessment**: Amplifier gain and physical alignment were iteratively adjusted to optimize clarity and volume at the receiver.

Full details: [`docs/methodology.md`](docs/methodology.md)

---

## 📊 Results

The system was successfully assembled and tested, demonstrating real-time wireless audio transmission over a modulated laser beam with a solar panel as receiver.

- A **solar panel was chosen over a photodiode** as the receiver due to its larger surface area and higher sensitivity to low-intensity light, making alignment far more forgiving — at the cost of the faster response time a photodiode would offer for high-speed digital communication.
- Audio was successfully reproduced at the receiver with acceptable clarity within line-of-sight range.

Full discussion: [`docs/results.md`](docs/results.md)

---

## ⚖️ Li-Fi vs Wi-Fi

| Parameter | Wi-Fi | Li-Fi |
|---|---|---|
| Spectrum | Radio Frequency | Visible Light |
| Range of Spectrum | 5 GHz | ~400 THz |
| Electromagnetic Interference | Yes | No |
| Coverage | Based on intensity of signal | Maximum 150 meters |
| Standard | IEEE 802.12 | IEEE 802.15 |
| Rate of Data Transfer | 10 Mbps | > 1 Gbps |
| Security | Limited | High |
| Power Consumption | High | Low |
| System Complexity | High | Low |
| Cost | High | Low |

*Adapted from Saranya et al. (2021), ICICT — see [References](#-references) [4].*

---

## ✅ Advantages & ❌ Disadvantages

**Advantages**
- High-speed data transfer potential, exceeding traditional Wi-Fi
- Enhanced security — light doesn't pass through walls
- No radio-frequency interference
- Lower latency for real-time applications
- Energy-efficient, can piggyback on existing LED lighting

**Disadvantages**
- Requires direct line-of-sight between transmitter and receiver
- Shorter operational range than Wi-Fi
- Best suited for indoor use
- Sensitive to obstructions in the light path
- Higher initial infrastructure/setup cost

---

## 🌐 Applications

- High-speed indoor wireless communication (homes, offices, schools)
- Secure communication in sensitive environments (hospitals, military, aerospace)
- Connectivity in RF-restricted areas (airplanes, underwater vehicles, industrial plants)
- Smart city & IoT integration via public lighting infrastructure
- Augmented reality & indoor location-based services (museums, malls, airports)

---

## 🚀 Future Scope

1. **Digital Data Transmission** — modulate text/images/files onto the laser using PWM or ASK for a full digital Li-Fi link.
2. **Improved Optical Receivers** — replace the solar panel with high-speed photodiodes or avalanche photodetectors for higher bandwidth.
3. **Noise Reduction & Filtering** — add electronic filtering to reduce ambient light interference.
4. **Longer Range & Beam Stability** — add focusing lenses, tracking, or adaptive beam alignment.
5. **IoT/Smart System Integration** — combine with microcontrollers for remote monitoring and automation triggers.

---

## ⚠️ Safety Notes

- A **low-power laser diode** is used specifically to minimize eye-hazard risk. Never look directly into the laser beam or point it at another person's eyes.
- All circuit connections should be properly insulated and checked before powering on, to avoid short circuits or component damage.
- This project is intended for **educational/demonstration purposes** under supervision.

---



## 📚 References

1. Othman, R. A. A., ap Sagaran, D., Mokayef, M., binti Wan, W. I. I. R., & Nasir, M. (2018). Effective LiFi communication for IoT applications. *2018 IEEE 4th International Symposium in Robotics and Manufacturing Automation (ROMA)*, 1–4.
2. Ali, S. H., Shivakumar, P., & Manikandan, J. (2018). Design and Evaluation of LiFi Module for Audio Applications. *2018 15th IEEE India Council International Conference (INDICON)*, 1–5.
3. Madhuri, G., Anjali, K., & Prabha, R. S. (2020). Transmission of data, audio and text signal using Li-Fi technology. *IOP Conference Series: Materials Science and Engineering*, 872(1), 012010.
4. Saranya, S., Ragavi, B., Pavithra, L., Susheel, S., Srivarsha, M., & Vishal, V. (2021). Audio transmission using visible light communication and Li-Fi technology. *2021 6th International Conference on Inventive Computation Technologies (ICICT)*, 19–24.
5. Asmathunnisa, Z., Manavalan, S., & Kumar, N. (2019). Visible Light Communication for Data and Audio Transmission using Light-Fidelity (Li-Fi). *International Journal of Scientific Research in Computer Science Engineering and Information Technology*, 534–539.

---
