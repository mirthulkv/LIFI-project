# Methodology

This document details the full design and build methodology for the Li-Fi based wireless audio transmission system.

## I. System Overview

The project consists of two main units: the **transmitter** and the **receiver**.
- The **transmitter** captures and processes audio signals to modulate a laser beam.
- The **receiver** captures the modulated light signal and reconstructs the original audio.

### 1. Transmitter Section

**Power Supply**
The transmitter circuit is powered using a 9V DC battery. Since components like the microphone module and laser diode operate at 5V, a voltage regulator (LM7805) steps the voltage down from 9V to a stable 5V supply.

**Audio Signal Acquisition**
A microphone module (MAX4466) captures sound from the surroundings and converts it into a corresponding electrical signal.

**Signal Amplification**
The weak microphone output is fed into a pre-amplifier circuit (PAM8403) to boost the signal strength enough to effectively modulate the laser.

**Laser Modulation**
The amplified audio modulates the intensity of a laser diode (HW-493). The current through the laser varies according to the audio signal, causing the light output to carry the audio information as intensity variations.

**Laser Transmission**
The modulated laser beam is directed toward the receiver, with careful alignment to preserve signal integrity over distance.

### 2. Receiver Section

**Light Detection**
A small solar panel acts as a photodetector, receiving the modulated laser beam and converting the varying light intensities into corresponding electrical signals.

**Signal Amplification**
The output from the solar panel is weak and requires amplification. A PAM8403 audio amplifier module boosts the signal to a level suitable for driving a speaker.

**Audio Playback**
The amplified signal drives a small speaker (8Ω, 15W), reproducing the original sound at the receiving end.

### 3. Testing and Calibration

**Alignment & Range Testing**
The laser and solar panel were carefully aligned for maximum signal reception, with tests conducted across different distances and angles.

**Audio Quality Assessment**
Clarity and volume were tested and optimized by adjusting amplifier gains and improving physical alignment.

### 4. Safety Measures

**Laser Safety**
A low-power laser diode is used to avoid potential eye hazards. All precautions were taken to prevent direct exposure to the laser beam.

**Electrical Safety**
All circuit connections were securely insulated and checked for proper operation to prevent short circuits and component damage.
