# Modified Klon Centaur Pedal
<p align="center">
  <img src="https://github.com/user-attachments/assets/20f22a20-4202-4e25-baa3-c42ed1a60125" width=40% height=40%>
</p>

# About
<h6> 
   &emsp; The Klon Centaur overdrive pedal is one of the most legendary guitar pedals in history and cultured a huge cult following. This pedal was designed by Bill Finnegan and an electrical engineer in 1994 with a common goal of creating an overdrive that preserves the character of the guitar and amp while adding grit and boost. This pedal caught the eye of legendary guitarists such as Jeff Beck, John Mayer, Joe Bonamassa, and so many more that used this pedal for their signiture sound. As demand grew, so did production stresses that made it really hard to meet the demand of the consumer. As a result, only 8000 units were made and the value skyrocketed to over six thousand dollars for a unit on the used market. The circuit itself was a mystery because the board was covered with epoxy to prevent copies. That did not stop the tone chasers as once the epoxy was removed, countless companies started producing clones to achieve the legendary tone.
<br/> 
</h6>

<p align="center">
  <img src="https://github.com/user-attachments/assets/7f13a982-5c99-4e95-bfc1-aec66c4b55a0" width=70% height=70%>
</p>

# Parts List
- 2x 0.1u Capacitor
- 2x 1.5k Resistor
- 1x 1.8k Resistor
- 4x 100k Resistor
- 1x 100k Dual Gang Potentiometer
- 2x 10k Potentiometer
- 2x 10k Resistor
- 1x 12k Resistor
- 2x 15k Resistor
- 1x 1Meg Resistor
- 2x 1N34A Germanium Diodes
- 2x 1N4001 Silicon Diode
- 2x 1N4148 Fast Switching Diodes (for switchable diode mod)
- 1x Double Pole DPDT Switch (for switchable diode mod)
- 1N5818 Schottky Diode
- 2x 1k Resistor
- 4x 1u Polarized Electrolytic Capacitor
- 3x 1u Bipolar Electrolytic Capacitor
- 1x 2.2n Capacitor
- 1x 22k Resistor
- 3x 27k Resistor
- 1x 27n Capacitor
- 1x 2k Resistor
- 1x 3.9n Capacitor
- 1x 390n Capacitor
- 1x 390p Capacitor
- 1x 392k Resistor
- 1x 4.7k Resistor
- 2x 4.7u Capacitor
- 1x 422k Resistor
- 1x 47k Resistor
- 2x 47u Capacitor
- 1x 5.1k Resistor
- 2x 560 Resistor
- 2x 68k Resistor
- 2x 68n Capacitor
- 1x 820p Capacitor
- 1x 82n Capacitor
- 2x TL072 OP Amp
- 1x MAX1044 Voltage Converter

# Schematic and Analysis
## Original Circuit Diagram
![Klon Centaur Original (1)](https://github.com/user-attachments/assets/4ae05caf-6b1b-4a4b-afdf-e33d96f9290f)

## Power Supply
Using a MAX1044 voltage converter IC, the circuit creates various voltages for use with the TL072 OP amps. The power supply uses the simple negative converter for -8.6V, positive multiplier for +16.2V, and voltage divider for +4.5V. The voltage converter ensures a clean signal for a low noise floor with the pedal. 
![image](https://github.com/user-attachments/assets/0b16ffa6-e71e-41d9-870d-61bf35e72e69)

## Input Buffer
The input buffer listed here converts the high-impedance signal from your guitar into a low impedance signal for increased signal integrity and less high end tone loss. This buffer has uniatry gain with the main focus being a clear guitar tone even when the pedal is bypassed.

### Frequency Cutoff
The 1Meg Resistor and 0.1u capacitor form a high pass filter and can be calcuated with the f = 1 / 2piRC formula.
f = 1 / 2pi(1Meg)(0.1u) = 1.59 Hz

This input buffer having a cutoff frequency of 1.59Hz does not audibly affect the signal and preserves the original guitar signal without attentuation.

### Input Impedance
Due to the JFET network inside the TL072, the input impedance is on the order of 10^12 ohms and will not affect the guitar signal all that much. With 1Meg input impedance and above, you don't have to worry about tone sucking.
Z = 10k + (1Meg // TL072 Z) = 1Meg
![image](https://github.com/user-attachments/assets/d3df56b4-1f56-47c8-8865-bbab273afe42)

## Clipping Stage
![image](https://github.com/user-attachments/assets/deb9e58f-ed97-4d40-b9ae-6b544fe40e7d)
![image](https://github.com/user-attachments/assets/d961c995-8917-4ca2-a45d-1c56d5e790d9)

## Switchable Diode Mod
To add versitility, the switchable diode mod is one that I came up with to add more high end distortion to the guitar signal. When switched on, siicon switching diodes are added in series to the germanium diodes to raise the forward voltage needed to distort from 0.3V to 1V. This increases headroom, output, and increases high end tone for a less fuzz like tone. 
![image](https://github.com/user-attachments/assets/12dee5a7-917e-42b8-baec-48a709f3679d)




