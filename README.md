## Sequential Circuits:
A sequential circuit is a type of digital logic circuit whose output depends not only on the present input values but also on the history of past inputs and outputs. This is achieved by incorporating memory elements, such as flip-flops or latches, which store information about previous states of the circuit.

## Synchronous Circuits:
A synchronous circuit is a type of digital circuit in which changes in the state of memory elements are coordinated by a common clock signal.
Key Characteristics
•	Clock Synchronization: All state changes happen in sync with the clock signal, ensuring that outputs and internal states change only at specific times.
•	Memory Elements: Synchronous circuits use clocked flip-flops or latches to store information, enabling the circuit to "remember" previous states.
•	Predictability: Because all changes are governed by the clock, the timing and sequence of operations are highly predictable and repeatable

![seq cir](https://www.tutorialspoint.com/digital-electronics/images/synchronous-sequential-circuit.jpg)

# 555 Timer Tutorial:
 
***The 555 Timer is a commonly used IC designed to produce a variety of output waveforms with the addition of an external RC network.***

The basic 555 timer gets its name from the fact that there are three internally connected 5kΩ resistors which it uses to generate the two comparators reference voltages. The 555 timer IC is a very cheap, popular and useful precision timing device which can act as either a simple timer to generate single pulses or long time delays, or as a relaxation oscillator producing a string of stabilised waveforms of varying duty cycles from 50 to 100%.

**The single 555 Timer chip in its basic form is a Bipolar 8-pin mini Dual-in-line Package (DIP) device consisting of some 25 transistors, 2 diodes and about 16 resistors arranged to form two comparators, a flip-flop and a high current output stage as shown below.**

![block](https://th.bing.com/th/id/OIP.O3gVUlSJO00BU3teD1TLDQAAAA?pid=ImgDet&w=500&h=500&c=7)

![di]("555 timer.jpeg")

Pin 1 : It is connected to the ground (0V) supply rail
Pin 2 : The inverting input to comparator 2 is connected to pin 2. A negative impulse on this pin ( voltage less then Vcc/3) makes S go high and hence Q prime goes low. It sets the internal flip-flop causing the output to switch from a “LOW” to a “HIGH” state.</br>
Pin 3: Output, The output pin can drive any TTL circuit and is capable of sourcing or sinking up to 200mA of current at an output voltage equal to approximately Vcc – 1.5V so small speakers, LEDs or motors can be connected directly to the output.</br>
Pin 4: Reset, This pin is used to “reset” the internal Flip-flop controlling the state of the output, pin 3. This is an active-low input( active when input is 0) and is generally connected to a logic “1” level when not used to prevent any unwanted resetting of the output.
Pin 5: Control Voltage, This pin controls the timing of the 555 by overriding the 2/3Vcc level of the voltage divider network. By applying a voltage to this pin the width of the output signal can be varied independently of the RC timing network. When not used it is connected to ground via a 10nF capacitor to eliminate any noise.</br>

Pin 6: Threshold, The positive input to comparator 2. When it exceeds 2/3Vcc, R becomes 1 and hence Q becomes 0. The output switches from “HIGH” to “LOW” state. This pin connects directly to the RC timing circuit.</br>
 Pin 7: Discharge, The discharge pin is connected directly to the Collector of an internal NPN transistor which is used to “discharge” the timing capacitor to ground when the output at pin 3 switches “LOW”.</br>
Pin 8:  Supply +Vcc, This is the power supply pin and for general purpose TTL 555 timers is between 4.5V and 15V.

## Monostable 555 Timer:

![y](https://www.electronics-tutorials.ws/wp-content/uploads/2018/05/waveforms-tim38.gif)

1)	When a negative (<Vcc/3) pulse is applied to the trigger input (pin 2) of the Monostable configured 555 Timer oscillator, the internal comparator, (comparator No1) detects this input(S=1) and “sets” the state of the flip-flop, changing the output from a “LOW” state to a “HIGH” state. (as Qprime is zero)
2)	This action in turn turns “OFF” the discharge transistor connected to pin 7, thereby removing the short circuit across the external timing capacitor, C1.
3)	The output of comparator 2 remains 0 until threshold is less than 2/3Vcc and the high state of the flip-flop is maintained as S also becomes zero after pulse.(R=0,S=0,then output retains previous state)
4)	This action allows the timing capacitor to start to charge up through resistor, R1 until the voltage across the capacitor reaches the threshold (pin 6) voltage of 2/3Vcc set up by the internal voltage divider network.
5)	At this point the comparators output goes “HIGH”(R=1,S=0) and “resets” the flip-flop back to its original state( Q=0) which in turn turns “ON” the transistor and discharges the capacitor to ground through pin 7. 
6)	This causes the output to change its state back to the original stable “LOW” value awaiting another trigger pulse to start the timing process over again(As R=0 and S=0 after capacitor discharges and threshold voltage is again less than 2/3Vcc). Then as before, the Monostable Multivibrator has only “ONE” stable state.

**NOTE: The Monostable 555 Timer circuit triggers on a negative-going pulse applied to pin 2 and this trigger pulse must be much shorter than the output pulse width allowing time for the timing capacitor to charge and then discharge fully. This is because the trigger is only for setting the flip-flop to high state and S=0 condition is necessary for threshold to control the output and work as a monostable timer.**

Once triggered, the 555 Monostable will remain in this “HIGH” unstable output state until the time period set up by the R1 x C1 network has elapsed. The amount of time that the output voltage remains “HIGH” or at a logic “1” level, is given by the following time constant equation.
</br>
![time]( https://www.electronics-tutorials.ws/wp-content/uploads/2018/05/waveforms-tim39.gif)
Where, t is in seconds, R is in Ω and C in Farads.

