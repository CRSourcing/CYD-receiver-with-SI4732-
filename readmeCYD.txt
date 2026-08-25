
This receiver and the modifications to the CYD are ONLY tested with the ESP32-2432S028 CYD with ILI9341 display.
Other displays or display sizes will not work.


The SI4732 chip glues nicely to the backside of the CYD. The CYD has not enough GPIO's available and additional GPIO's need to be freed.
This radio uses the on board audio amplifier. Connect headphones or a speaker to the audio output pins. 
A volume potentiometer is recommended, see below.


Board modifications:
1. Make GPIO21 available: Connect drain of Q2 (backlight mosfet) to ground. Cut trace to gate of Q2 before R10.
2. Make GPIO 4, 16, 17 available: Remove RGB status LED.
3. Connect GPIO 35 to pin5 of the audio amp (SC8002) (for FFT and decoders).
4. Optional: Remove serial connector and replace with antenna connector (sma)

Encoder:
This radio can be tuned without encoder, but it's preferable to use one. Connections:
Connect GPIO 16 to encoder pin A.
Connect GPIO 4 to encoder pin B.
Connect GPIO 27 to encoder pushbutton.
Connect encoder center pin and the other pushbutton pin to ground.

SI 4732 pins:
16: via 2.2uF + 2.2K in serie to pin 4 of the CYD audio amp. The resistor will determine the volume of the SI4732 audio
15: ground
14: + 3.3V and 1uF cap to ground (short connections)
13: Crystal 32768Hz and 22pF to ground
12: GPIO 21
11: GPIO22
10: Either +3.3V or ground
9:  GPIO17
8:  via 220pF to antenna connector
7:  ground, short connection
6:  via 6.8pF to antenna connector
5: NC
4: NC
3: NC
2: Crystal (other side) 32768Hz and 22pF to ground
1: NC




Volume control potentiometer:
Volume of the radio can be set with the volume slider, but if the volume is too high or too low, waterfall and decoders will not work.
It is therefore recommended to add an external volume potentiometer. Easiest is a 100 Ohm pot (0.5W) between audio out and headphone/speaker.



Limitations:
SD card does not work reliably.
Pulsing/knocking noise in KiwiSDR SSB mode.
Scratching noise with some internet radio stations.
Battery voltage indicator not available.
