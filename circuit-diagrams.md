# Circuit Diagrams & Wiring Notes

Vector recreations of the original schematics are in [`../images/`](../images):
- `transmitter-circuit.svg`
- `receiver-circuit.svg`

## Power Section (used identically on both Tx and Rx boards)

```
9V Battery (+) ── VIN   LM7805   VOUT ── +5V rail
9V Battery (-) ── GND ──┴──────── GND ── GND rail
```

The LM7805 steps the 9V battery voltage down to a stable, regulated 5V used by all downstream modules.

## Transmitter Section

```
+5V ── MAX4466 (VCC)
GND ── MAX4466 (GND)
MAX4466 (OUT) ── PAM8403 (IN.L / IN.COM)
+5V ── PAM8403 (+5V)
GND ── PAM8403 (GND)
PAM8403 (OUT.L+ / OUT.L-) ── HW-493 Laser Module (signal input, in place of a speaker)
+5V ── HW-493 Laser Module (VCC)
```

The laser module's brightness is driven directly by the amplified microphone signal instead of a speaker coil — this is what encodes the audio as intensity variations in the light.

## Receiver Section

```
Solar Panel (+/-) ── PAM8403 (IN.L / IN.COM), via 100kΩ potentiometer wiper
+5V ── 100kΩ Potentiometer (top terminal)
GND ── 100kΩ Potentiometer (bottom terminal) / Solar Panel reference
+5V ── PAM8403 (+5V)
GND ── PAM8403 (GND)
PAM8403 (OUT.L+ / OUT.L-) ── 8Ω Speaker
```

The potentiometer is wired as a variable voltage divider between the solar panel output and the amplifier input, allowing manual volume control before amplification.

## Alignment Notes
- Keep the laser diode and solar panel at the same height and pointed directly at each other.
- Minimize ambient light interference (test in a dimmer room for best signal-to-noise ratio).
- The solar panel's relatively large surface area makes exact alignment less critical than it would be with a photodiode, but a stable mount/tripod is still recommended.
