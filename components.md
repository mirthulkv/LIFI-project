# Components

Detailed notes on every component used in the build.

## 1. MAX4466 Microphone Amplifier Module (×1)
An electret microphone module with a built-in low-noise preamplifier. Designed to capture ambient audio and convert sound waves into corresponding electrical signals. Features an adjustable gain trimmer, making it suitable for capturing voice and ambient sounds with clarity.

## 2. PAM8403 Audio Amplifier Module with Potentiometer (×2)
A Class-D stereo audio amplifier delivering up to 3W per channel into 4Ω speakers with high efficiency and low distortion. Operates at 5V DC, ideal for low-power, battery-operated applications. Built-in potentiometer (knob) acts as a volume control device. One unit is used in the transmitter (to drive the laser) and one in the receiver (to drive the speaker).

## 3. HW-493 Laser Diode Module (×1)
A laser transmitter module that emits a focused beam of light, modulated by varying its input voltage. In this project, it acts as the medium carrying the audio signal via intensity modulation.

## 4. Solar Panel — Photovoltaic Sensor (×1)
A small solar panel, made up of a few solar cells, used to detect the incoming laser beam. The laser's intensity variations are converted into corresponding electrical signals — acting as the light receiver and signal demodulator.

## 5. 8Ω, 15W Speaker (×1)
Converts the electrical audio signal (amplified from the solar panel output) back into sound waves, completing the wireless audio transmission chain.

## 6. 9V Battery (×2)
Primary power source for both the transmitter and receiver circuits, providing portability and sufficient power via the voltage regulator.

## 7. LM7805 Voltage Regulator (×2)
A linear voltage regulator taking a 9V input and providing a stable 5V output. Used in both the transmitter and receiver circuits to keep modules operating safely within their voltage ratings.

## 8. 100kΩ Potentiometer (×1)
A three-terminal variable resistor used to adjust voltage levels within a circuit. In the receiver section, it controls output volume by adjusting the signal level fed into the audio amplifier.

## Supporting hardware
- Breadboards (×2, one per section)
- Jumper wires / connecting cables
- Crocodile clips (for solar panel leads)

See [`../hardware/bill-of-materials.csv`](../hardware/bill-of-materials.csv) for a spreadsheet-friendly version of this list.
