# Atmel-Interrupts-Lab-3-
In this lab you will implement interrupts using the Atmel 328P microcontroller.

Part 1 (circuit): Parts needed:
ATmega328P minimal circuit components
10kΩ resistors (2)
220Ω or 330Ω resistors (4)
Connector wires
Switches (2 pushbutton or a row of DIP switches) 
LEDs (4)
Multimeter

Part 2 (schematic): Sketch a schematic of your circuit that includes the LEDs, switch, and ATmega328P (note that you do not need to sketch the minimal circuit of the ATmega328P that includes the oscillator, power, and ground connections). This may be a hand sketch or a drawn sketch similar to those shown in the Lab 1 handout.

Part 3 (code): Your main() function in this lab will be the same as in Lab 2: it will cause the ATmega328P to rotate a single lighted LED through the row of four LEDs and then repeat the pattern indefinitely. In this sequence, any given LED must be on for 1 sec before the next LED is turned on.

In Lab 2, we polled the switch and changed the LED pattern if it was pressed. The polling was only done in the main() function, though, so if the switch were pressed during a delay, the delay needed to be finished before the switch press could take effect. In this lab, we will use interrupts to see immediate effect of the switch press, and we’ll add a second switch that creates an additional effect.
Use the interrupt functions of INT0 and INT1 such that the switches attached to PD2 and PD3 cause the following action when the switches are pressed (capture each switch signal’s falling edge to trigger the interrupt):

- A press of switch 0 (attached to INT0 pin) will cause the LED pattern to change to a count up by 1 in binary, for one complete cycle of the four LEDs, with PC0 being the least significant bit. Start from 00002. In this sequence, any given LED pattern must be on for 250 msec before transitioning to the

Example LED pattern:
Main rotating sequence is running... (1 = LED is off and 0 = LED is on) 1110 (1 sec)
1101 (1 sec)
1011 (part of 1 sec)
INT0 triggered...start LED sequence that is an upward binary count, starting with 00002:
0000 (250 msec) 0001 (250 msec) 0010 (250 msec) 0011 (250 msec) ...
1110 (250 msec)
1111 (250 msec)
Exit the interrupt routine and resume the main rotating sequence by
first finishing the required time for the 1011 pattern and then
continuing as usual: 1011 (remainder 1 sec) 0111 (1 sec)
1110 (1 sec)
...
