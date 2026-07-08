# Results & Discussion

The laser-based wireless audio transmission system was successfully designed, assembled, and tested. The project effectively demonstrated the capability to transmit audio signals from a transmitter to a receiver using a modulated laser beam and a photovoltaic sensor (solar panel).

## Transmitter Behavior
The transmitter begins by capturing audio using the MAX4466 microphone module, which converts sound into an analog electrical signal. This signal is amplified and used to modulate the intensity of a laser diode, encoding the audio onto the light beam. The modulated laser beam is then projected through free space toward the receiver, enabling wireless audio transmission with low power consumption and minimal interference.

## Receiver Behavior
The receiver uses a mini solar panel to detect the incoming laser beam and convert its intensity variations back into corresponding electrical signals. These signals are amplified using a PAM8403 audio amplifier and played through a speaker. A potentiometer allows manual volume adjustment, while a 9V battery with a 7805 voltage regulator supplies a stable 5V to power the entire circuit.

## Design Choice: Solar Panel vs. Photodiode
A key design choice in this project was the use of a **solar panel** as the optical receiver instead of a **photodiode**. This was driven by the solar panel's larger surface area and higher sensitivity to low-intensity light, which made laser alignment easier and more forgiving — especially for beginners.

While photodiodes are ideal for high-speed communication due to their fast response times, they require precise alignment and additional amplification circuitry. In contrast, the solar panel can directly generate sufficient voltage from modulated laser light, simplifying the receiver design and reducing component complexity — making it ideal for a straightforward analog demonstration of laser-based audio transmission.

## Li-Fi vs. Wi-Fi Comparison

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

*Adapted from Saranya, S., Ragavi, B., Pavithra, L., Susheel, S., Srivarsha, M., & Vishal, V. (2021). Audio transmission using visible light communication and Li-Fi technology. In 2021 6th International Conference on Inventive Computation Technologies (ICICT) (pp. 19–24). IEEE.*

## Key Takeaway
This project validates that inexpensive, readily available components can implement a functional optical wireless communication link, and specifically highlights the solar panel's viability as an unconventional but effective Li-Fi receiver for analog audio applications.
