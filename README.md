# Spring-Reverb-Driver-with-external-Feedback
A spring reverb circuit with external feedback capabilites designed to drive an Accutronics AMC2BF3.

## Overview
Initially, I planned to add a PT2399 delay into the feedback path to create a unique effect. However, I soon realized that allowing more experimentation with different effects in the feedback path could be interesting for sound design as well.  
This circuit was therefore designed as a spring reverb driver with a modular feedback path, enabling the user to freely choose which effect to insert, how much of it to apply, and so on. If no effect is desired, the feedback output can simply be patched directly into the feedback input.

## Features

### Controls
 - **Dwell** - Adjusts how hard the reverb tank is driven. Higher settings may cause some distortion, as the OPA1679 can only supply up to 50 mA. In practice, this is rarely an issue, since any distortion is largely masked by the reverb itself. 
 - **Mix** – Sets the balance between the dry and wet signals. 
 - **Output** – Controls the overall output volume. The output signal is phase-inverted relative to the input, which in most use cases is not an issue. If a non-inverted output is required, the feedback output can be used instead. Using the standard output in the feedback path may produce different tonal results due to phase cancellation with the input signal.  
 - **Feedback** Adjusts the output level of the feedback signal. Due to the Big Muff–style filter, this output is approximately -6 dB in the passband compared to the normal output.  
 - **Tone** Implements a Big Muff–style tone control. With the chosen component values, setting the knob to the middle position produces roughly +3 dB at 3 kHz, emphasizing the characteristic “drippy” quality of the reverb.

### Noise Considerations
To achieve high input impedance and sufficient current-drive capability for the tank, the standard approach would be to use a TL072 at the input and an NE5532 for the amplification stage. However, the TL072 has relatively high noise (around 37 nV/√Hz at 1 kHz), which becomes noticeable given the high gain required in the recovery stage.  
To address this, I chose the OPA1679, which offers high input impedance, low noise, and current-drive performance comparable to the NE5532  
(OPA1679: 4.5 nV/√Hz, 50 mA Isc; NE5532: 5 nV/√Hz, 60 mA Isc).

## Schematic
![Spring Reverb with Feedback — Schematic](docs/springreverb_.jpg)
