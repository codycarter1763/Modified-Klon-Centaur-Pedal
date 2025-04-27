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
The input buffer listed here converts the high-impedance signal from your guitar into a low impedance signal for increased signal integrity and less high end tone loss. This buffer has uniatry gain with the main focus being a clear guitar tone even when the pedal is bypassed. As the pedal is not true bypass, when the pedal is turned off the guitar signal runs through the input buffer, into a seperate RC network, and to the output jack. 

### Bypass RC Network
This RC network does not audibly affect te guitar tone. Though, the 4.7uF capacitor blocks the DC offset, 100k resistor bleeds this DC signal to ground to prevent DC from going into the guitar amp, and the 560 ohm resistor prevents popping and noise when bypassed on or off. 
F = 1 / 2pi(4.7uF)(100k) = 0.33Hz
![image](https://github.com/user-attachments/assets/2e7d87c3-aea6-4461-a0e7-b7a75c5b1a72)

### Frequency Cutoff
The 1Meg Resistor and 0.1u capacitor form a high pass filter and can be calcuated with the f = 1 / 2piRC formula.
f = 1 / 2pi(1Meg)(0.1u) = 1.59 Hz

This input buffer having a cutoff frequency of 1.59Hz does not audibly affect the signal and preserves the original guitar signal without attentuation.

### Input Impedance
Due to the JFET network inside the TL072, the input impedance is on the order of 10^12 ohms and will not affect the guitar signal all that much. With 1Meg input impedance and above, you don't have to worry about tone sucking.
Z = 10k + (1Meg // TL072 Z) = 1Meg
![image](https://github.com/user-attachments/assets/d3df56b4-1f56-47c8-8865-bbab273afe42)

## Clipping Stage
The clipping stage is where the distortion is created and frequency response is EQed to the Klon signiture sound. 

### Gain
![image](https://github.com/user-attachments/assets/deb9e58f-ed97-4d40-b9ae-6b544fe40e7d)
![image](https://github.com/user-attachments/assets/d961c995-8917-4ca2-a45d-1c56d5e790d9)

As the gain is turned up, the more the signature 1k mid hump is pronounced. At max gain, the pedal outputs 42dB.
![image](https://github.com/user-attachments/assets/a49108f3-b2b8-4f50-b6f5-fbef79c81e84)

### High Level Overview
The goal of this stage is to create distortion and add clarity through two RC networks that add a clean signal to the distored tone by the OP amp and germanium diodes.

#### Germanium Diode Distortion
As shown below, with the forward voltage of germanium diodes being 0.35 volts, as the gain is tuned up the signal becomes more and more distorted.
![image](https://github.com/user-attachments/assets/468b4fb4-308e-457f-934c-00daa67e7041)

#### RC Network 1
Through this RC network, clean guitar signal is added to the distorted tone after the clipping diodes for more low end. Frequencies over 106Hz are attenuated.

F = 1 / 2pi(1.5k)(1uf) = 106Hz
![image](https://github.com/user-attachments/assets/bc99d3ef-38c6-4b86-983d-9f8adf916ce8)

#### RC Network 2
Through this RC network, clean guitar signal is added to the distorted tone after the clipping diodes. This network is responsible for changing how much bass in inserted into the distorted signal depending on gain. When gain is low, bass is attenuated for a cleaner tighter signal, and as gain is turned up, more bass is added for a fatter tone.
![image](https://github.com/user-attachments/assets/2be31ee1-d6ae-49cd-b31a-d4d714fb3b71)
![image](https://github.com/user-attachments/assets/c07bf9db-326a-4668-a806-83a9e425f649)

## Summing OP Amp
![image](https://github.com/user-attachments/assets/6da31535-aa10-4cf7-9ef7-248d1db0322c)

This stage is where the distorted and both RC network signals are summed together into one signal. This stage boosts the signal even higher from the previous stage and shapes the distorted signal as shows below. Thanks to the MAX1044 voltage converter, this stage has -8.6V and +16.2V power rails for 30V of headroom. This extra headroom keeps the signal cleaner and more dynamic even when the gain turns up.

With the RC network in the feedback loop, the cutoff frequency is 495.13Hz and adds to the signiture mid boost of the Klon.

F = 1 / 2pi(392k)(820pF) = 495.13Hz
![image](https://github.com/user-attachments/assets/8f71fd55-82fb-4837-b739-820a23367f52)

## Tone Control
This stage is responsible for adding or taking away the amount of treble from the guitar signal. As the treble knob is turned up, the more boosted the trebke signal will be. Due to the nature of the wiring, even through the gain is unitary there will still be a noticeable increase in high fequencies because of the adjustable RC high pass filter.
![image](https://github.com/user-attachments/assets/b603652b-4988-4f6e-8efc-c28d4a7e21da)

## Output 
This stage is mainly for the volume control and switch to route the guitar signal through the pedal or buffer bypass to the output jack. No significant signal attenuation is applied to the signal as shown below.

### Max Pot Value Cutoff Frequency
F = 1 / 2pi(560 + 10000)(4.7uF) = 3.21Hz

### Max Pot Value Cutoff Frequency
F = 1 / 2pi(560)(4.7uF) = 60.47Hz

![image](https://github.com/user-attachments/assets/5d2c4245-152e-4fc9-9fca-a628ec1424ed)

## Switchable Diode Mod
To add versitility, the switchable diode mod is one that I came up with to add more high end distortion to the guitar signal. When switched on, siicon switching diodes are added in series to the germanium diodes to raise the forward voltage needed to distort from 0.3V to 1V. This increases headroom, output, and increases high end tone for a less fuzz like tone. 
![image](https://github.com/user-attachments/assets/12dee5a7-917e-42b8-baec-48a709f3679d)

### Gain 
Shown here, with the diode mod engaged, the maximum gain of the pedal increases to about 49dB.
![image](https://github.com/user-attachments/assets/4c1343e0-a7ba-45c1-a682-47d6f0342ab6)

### Diode Clipping
With the added 1N4148 silicon switching diodes to te 1N34A germanium diodes, the forward voltage is increased to 1V. This increases headroom and adds more aggresive high end distortion that makes the Klon truly versitile.
![image](https://github.com/user-attachments/assets/d21fcc5a-1a81-433a-a03c-196ea09cfad3)

# Closing Remarks 
As you can see, the Klon Centaur's cult iconic tone can be created with without paying a huge premium for an original model. There is something truly magical about the history and cult following thats only matched by the incredible sound used by many great guitarists. This has so far been my favorite build and it was very cool seeing all of the circuit techniques to get that tone. As I test and discover new mods, I will update the repository as nessesary.

Special thanks to ElectroSmash for the very in-depth analysis and history of the Klon Centaur. Reading documentation like this has helped a ton in applying knowledge from my electronics classes to real-life applications.

Follow at this link below. 
https://www.electrosmash.com/klon-centaur-analysis




