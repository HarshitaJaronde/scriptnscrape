# ESI (Electronic System Integration)

Also previously known as HV/LV.
This subsystem deals with Low Voltage and High Voltage Circuitry to not just create a successfully running car but also an electrically rule compliant car. 
The task is to ensure the safety of the driver as well as the car. As a member of this subsystem your task would be to design, test, and ensure all the PCBs not only function well on their own but also when integrated with the whole system of our car.

## Terms :
1.	*Wire Harness*:
Wire harness assembly is the process of organizing and bundling individual electrical wires or cables into a single unit.
This unified structure, known as a wire harness or wiring assembly, serves as the central nervous system for various electrical devices and systems. By consolidating multiple wires into a single harness, manufacturers can streamline installation, improve organization, and enhance the overall reliability of electrical systems.

3.*Cable Routing*:
Cable routing refers to the structured method of protecting, organizing, and directing electrical cables within a defined pathway. 

# EV 1 Definitions:

## 1. Tractive System(TS) –
 High voltage sytem that is responsible for delivering electrical energy from the accumulator to the motors which convert to into motion of our car. It includes every component electrically connected to the high-voltage battery that is involved in generating and transmitting drive power to the wheels.<br/>
As per rulebook, 
Tractive System (TS)– every part that is electrically connected to the motors and TS accumulators. The LVS may be supplied by the TS if a galvanic isolation between both systems is ensured.
TS enclosures– every housing or enclosure that contains parts of the TS.

## 2. Galvanic Isolation – 
It means that two circuits would be electrically disconnected and that no current flows from one to another even in extreme conditions ( like a very high potential drop).
As per rulebook,
two electric circuits are defined as galvanically isolated if all of the following conditions are true:
1.	**The resistance between both circuits is >=500ohm/volt.**
( The unit ohm/volt tells that for every 1 volt of electromotive force in a circuit, there exists a resistance of 1 ohm)
The rule is related to maximum TS voltage meaning that if the TS voltage is say 250 V then the required insulation resistance must be 500*250 = 125000 ohm = 125kohms.<br/>
Also, the testing voltage must be either the max TS voltage of 250 V, whichever may be higher.
2.	Isolation test voltage is a high AC voltage applied between two isolated circuits to test their insulation barrier.
This rule states that the isolation test voltage should be the RMS value of an AC source and it is applied for 1 minute. It should be three times the maximum TS voltage or 750V, whichever is higher. <br/>
If the max TS voltage is 750 V (say) then the testing voltage would be 750 V RMS AC.
The 1 minute time period is enough to tell if there is a problem in the insulation and also short enough to not cause a serious damage to the circuits.
3.	**Working voltage is defined as the highest voltage that can be continuously present across a component, insulation barrier, or circuit during normal operation without causing damage or dielectric breakdown.**
As per rulebook,
The working voltage of the isolation barrier, if specified in the datasheet, is higher than the maximum TS voltage.
(It should be higher than three times maximum TS voltage actually)

3)	Also, it is mentioned that 
Capacitors that bridge galvanic isolation must be class-Y capacitors.
Y- class capacitors are used so the Electromagnetic Interference, Radio-Frequency Interference bypass sensitive circuit elements and flow to the ground.
Here , they are used as we are dealing with very high voltage across the insulation barrier and these have the mechanism at extremely high voltages to become open-circuits. This ensures that the ground is not flooded with shock and user is safe. These are line to ground capacitors.

4)	**High Current Path– any path of a circuitry that, during normal operation, carries more than 1A.**
  
## EV 6.3 Insulation Monitoring Device:
1.	Every vehicle must have an IMD installed in the TS system. IMD (Insulation Monitoring Device) continuously measures the resistance between the LV and HV paths. If the resistance falls below a certain threshold, the SDC(Shutdown Circuit) is opened.
2.	The IMD must be a Bender A-ISOMETER® iso-F1 IR155-3203,-3204,-4203, or-4204, or a Bender ISOMETER® iso165C-1, iso175, or equivalent IMD approved for automotive use.
An IMD may be considered equivalent on the basis of:
•	**Robustness to vibration** – our car in motion would lead to vibrations of the IMD and it should function properly amidst these vibrations.
•	**Operating temperature range** – it should operate properly even in heated conditions of the car.
•	**IP rating** (stands for "Ingress Protection" rating, a standardized code defined by the International Electrotechnical Commission (IEC) to indicate how well an electrical or electronic enclosure is protected against the intrusion of solid objects (like dust) and liquids (like water))
•	**Availability of a direct output** – a dedicated hardware signal—typically a relay contact or a digital output—that can be directly connected to other vehicle safety circuits or warning systems.<br/>
 This output provides a clear indication of the IMD's status (such as insulation fault detected, device error, or normal operation) without requiring additional processing or interpretation of communication protocols.
•	**a self-test facility**- The IMD should be able to moniter int’s internal system at regular intervals to prevent false signals from it.
•	It must not be powered by the system that is monitored.
 Prevents a situation where a power loss or fault in the monitored system also disables the IMD, which would leave insulation faults undetected. 

3.	The response value of the IMD must be set to ≥500Ω/V, related to the maximum TS voltage.
If the maximum TS voltage is say 250 V, then the minimum insulation resistance would be 500*250 ohms = 125kohms, below which the IMD must trigger an error.<br/>
Response Value: The preset resistance value at which the IMD will react. If the measured insulation resistance drops below this value, the IMD will signal a fault (often by opening the shutdown circuit).

4.	The response value must not be changed after electrical inspection.
5.	The IMD must be connected on the vehicle side of the AIRs.
The Accumulator Isolation Relays are connected between the accumulator and the rest of the tractive system (the vehicle side including motor controllers , motors, wiring); an IMD error may open the AIRs to isolate the HV source from the other components of our car.<br/>
It must connected on the vehicle side because if the IMD were placed on the accumulator side, it might only monitor the battery, missing insulation faults elsewhere in the tractive system.

6.	One IMD chassis ground measurement line must be connected to the grounded TSAC or the respective grounded TS enclosure of the IMD. The other chassis ground measurement line must be connected to the main hoop. Each connection must use a separate conductor, rated for at least maximum TS voltage. An open circuit in any of these ground measurement connections must result in an opened SDC
7.	In case of an insulation failure or an IMD failure, the IMD must open the SDC.
8.	 This must be done without the influence of any programmable logic. Also, If the SDC is opened by the AMS or the IMD, it has to be latched open by a non programmable logic that can only be manually reset by a person at the vehicle who is not the driver.<br/>
Programmable devices can fail, crash, or be inadvertently reprogrammed, which could prevent the SDC from opening in a dangerous situation. The rules require that:<br/>
The IMD (Insulation Monitoring Device) and AMS (Accumulator Management System) must be able to open the SDC directly, using only hardwired, non-programmable circuits.<br/>
The latching mechanism that keeps the SDC open after a fault must also be implemented with non-programmable logic (e.g., relays, latching circuits) and not rely on software or microcontrollers.
10.	A red indicator light in the cockpit that is easily visible from inside and outside the cockpit even in bright sunlight and clearly marked with the lettering “IMD” must light up if and only if the IMD opens the SDC. It must stay illuminated until the error state has been manually reset, . Signals controlling this indicator are SCS(System critical signals) see T11.9.




## Shut Down Circuit:

### The circuit that drives the CON+ and the CON- contactors, the pre-charge and the discharge relay is the shutdown circuit.

Here is introduction to some elements of the SDC:
1.	LVMS : It is the very first element of the shutdown circuit which powers the SDC and activates all the LV circuitry on the car. As per T 11.3, the LVMS must completely disable power to the LVS. It must be marked with ‘LV’ and a symbol showing a red spark in a white edged blue triangle.
2.	 Shutdown Buttons: These are mechanical push-pull or push-rotate buttons mounted on either side of the car and on the driver’s cockpit. These allow the driver or any authorised person present outside the car to open the shutdown circuit. <br/>
The international electrical symbol consisting of a red spark on a white-edged blue triangle must be affixed in close proximity to each shutdown button. Shutdown buttons must be red.
3.	IMD: It opens the SDC in case of insulation faults
4.	AMS: The Accumulator Management System monitors the cell voltages, temperatures and currents, and opens the SDC, if any of these parameters go out of bound over a range of time.
5.	Inertia Switch: It is a crash-sensing switch that opens the shutdown circuit when the car experiences a heavy jerk.
6.	BOTS (Break Overtravel Switch): BOTS or Brake Over-Travel Switch is useful to detect any abnormalities with the brake pedal. This switch is kept behind the brake pedal, which is usually not in reach even during maximum pedal travel.<br/>
 However, in case the brakes don't work properly, say in case of leakage of brake fluids, the brake pedal can travel even further due to the loss of pressure. Thus, the switch gets pressed and the SDC is opened. ‘
Repeated actuation of the switch must not close the SDC, and it must be designed so that the driver cannot reset it.
7.	Interlocks: An interlock connector or switch is designed so that when you disconnect a high-voltage (HV) connector, it simultaneously interrupts a separate, low-voltage (LV) signal circuit. An Interlock is defined as a connector/switch that is capable of mechanically disconnecting two independent circuits at the same time, usually HV and LV circuits. <br/>
We implement HVD and other interlocks to ensure that breaking of any HV connections is detected as a critical failure of the system, and correspondingly, the SDC is opened.
8.	High Voltage Disconnect: HVD or High-Voltage Disconnect is a rotate-pull switch that is an interlock.
It must be possible to disconnect at least one pole of the TS accumulator by quickly removing an unobstructed and directly accessible element, fuse, or connector. It must be possible to remove the HVD without removing any bodywork. ( EV 4.8 )
9.	TSMS: TSMS or Tractive System Master Switch is, similar to LVMS, is a tagout-lockout switch, that when SDC is complete, powers the coils of precharge, discharge relays and that of AIRs. It is the last element of the shutdown circuit.<br/>
(A tag-out/lock-out switch is used in EVs to prevent accidental starting of the TS during maintenance work. Lock-out means you place a padlock through the breaker’s lock-out provision so it cannot be turned back on. Tag-out means you attach a tag to the lock, stating your name, the date, and the reason for the lock-out.)


## OptoCouplers :

**An Optocoupler, is an electronic component that interconnects two separate electrical circuits by means of a light sensitive optical interface.**

It can be used in many different applications as an interface between low voltage digital or control circuits and large power electronic devices.


Assume a photo-transistor device as shown. Current from the source signal passes through the input LED which emits an infra-red light whose intensity is proportional to the electrical signal.

![A phototransistor](https://i0.wp.com/www.electricalandcontrol.com/wp-content/uploads/2021/04/Optoisolator.png?resize=207%2C132&ssl=1)

This emitted light falls upon the base of the photo-transistor, causing it to switch-ON and conduct in a similar way to a normal bipolar transistor.
The spectral response of the LED and the photo-sensitive device are closely matched being separated by a transparent medium such as glass, plastic or air. Since there is no direct electrical connection between the input and output of an optocoupler, electrical isolation up to 10kV is achieved.
<br/>

<br/>
If we want the output current to depend on the input current through the LED, then we must operate the phototransistor in its active region. This means that Vce>Vce(saturation).

![Figure 1](https://i0.wp.com/electronicsbeliever.com/wp-content/uploads/2015/04/Figure-17.png?resize=346%2C242&ssl=1)