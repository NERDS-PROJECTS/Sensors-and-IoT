# ROBOTICS CLUB || NIT SILCHAR

# MOTOR DRIVERS

#### (contributed by:- SIDHANT MISHRA )

#### All of us are quite familiar with motors and we can easily witness the use of motors in any electrical equipment.But we have never teased our brain to think how our motors actually work or what DRIVES it using some adjustments.Have we??

![page1](https://user-images.githubusercontent.com/100593956/221625006-f5687cb6-61d4-446b-9261-39784e22c098.jpeg)


![page2](https://user-images.githubusercontent.com/100593956/221625908-76617187-cfc3-44e7-854c-86ee51956012.jpeg)

#### [L 293 D MOTOR DRIVER]

#### Motor drivers basically are interface between motors and microcontrollers. Most microprocessors operate at LOW voltages and require a small amount of current to operate while the motors require a relatively higher voltages and current.Therefore,Motor driver is an interface connecting both the motor and microcontroller and fulfilling their demands.

## TYPES OF MOTOR DRIVERS

L293D IC-->Controls two DC motors simontaneously  

<img width="127" alt="Screenshot 2023-02-27 at 10 53 27 PM" src="https://user-images.githubusercontent.com/100593956/221635656-200c0d4b-a49d-45bc-bdf5-f3519d93d51b.png">

**TB6612FNG motor driver board**--> Can control 2 DC motors at 1. 2 A constantly

<img width="122" alt="Screenshot 2023-02-27 at 10 55 36 PM" src="https://user-images.githubusercontent.com/100593956/221636591-7f386c1c-68be-4f76-8c89-e4fc33035f8d.png">

**TB6560 motor driver board**--> Used for axis control and with input signal high-speed optocoupler isolation,the large heat sink to ensure good heat dissipation.

<img width="119" alt="Screenshot 2023-02-27 at 10 57 10 PM" src="https://user-images.githubusercontent.com/100593956/221637251-632b9c10-f9d5-4a44-84e7-eab81a589d93.png">

**BTS 7960 B motor driver board**--> Controls the **SPEED** and **DIRECTION** of the dc motor based on PWM.

<img width="125" alt="Screenshot 2023-02-27 at 10 58 24 PM" src="https://user-images.githubusercontent.com/100593956/221637767-dcbcf6d8-4c94-48a5-8cde-22d351e29b5c.png">

**PCA968516 channel servo motor driver**-->Drivers upto 16 servos over 12 IC with only two pins.

<img width="130" alt="Screenshot 2023-02-27 at 11 00 07 PM" src="https://user-images.githubusercontent.com/100593956/221638576-3f7565eb-698f-48d4-8d5d-e1415f6c5504.png">

**MACH 3 interface board CNC 5 Axis** --> ● Maximum support 5 - Axis Stepper motor driver controllers
                                          ● Compatible with MACH 3 ,Linux,etc.
                                          ● USB power supply are seperate for security

<img width="127" alt="Screenshot 2023-02-27 at 11 04 32 PM" src="https://user-images.githubusercontent.com/100593956/221639907-05c3f030-963a-4532-a335-51fecdd26e36.png">

## WORKING OF A MOTOR DRIVER
![page3](https://user-images.githubusercontent.com/100593956/221626974-4a0e3caa-2c3f-481c-805a-4d5c497d08b1.png)

This is the most important section of the whole document about how
motor driver really operates.
The microcontroller that we generally use(Aurdino,rasberry pi) firstly
sends signals to the motor driver.The motor driver then interprets the
signals and steps them up with the reference voltage.The two voltage pins
on the motor turns on and o by giving **V=ref** voltage and **V= 0**
respectively.
In case our microprocessor transmitts a **HIGH** input to the motor
driver,the driver will rotate the motor in one direction keeping pins **HIGH**
and **LOW.**
If our microprocessor transmitts a **LOW** input to the motor driver,the
driver will rotate the motor in other direction keeping pins **LOW** and
**HIGH**.
For bidirectional motor driving, **”H-BRIDGE”** drivers are used.
Working and construction of “ **H-BRIDGE** ” is explained below in detail.
xtremity, the inverse happens, and the other combine of transistors turn on. To beginnal
at that point finds its way to the ground. This substitute stream of current shapes an


## THE H-BRIDGE CIRCUIT

![page4](https://user-images.githubusercontent.com/100593956/221629602-e039e168-e984-4bc5-ab4c-714054e90c12.png)
![page5](https://user-images.githubusercontent.com/100593956/221629841-8141a862-c7ec-4673-a790-387bbbfdb3da.png)

Connecting two pairs of transistors in a circuit forms an **" H-shaped "**
circuit which we call an H-bridge.


Place two sets of transistors - one that receives input voltage and the
other pair that remains grounded.
Amid a positive extremity, switch one match of transistors at a time.
Presently, current streams from the source voltage to the positive
terminal.
Another, the current from the **+VE** terminal streams to the **- VE** terminal,
which at long last streams to the ground. However, amid a negative
extremity, the inverse happens, and the other match of transistors turn
on.
To begin with, the current will stream straight to the **negative** terminal
from the source voltage. At that point, the current from the **negative**
terminal streams straight to the positive terminal at that point finds its
way to the ground.
**This interchange stream of current shapes an H-bridge circuit.**

## CONSTRUCTION OF A MOTOR DRIVER CIRCUIT
<img width="178" alt="Screenshot 2023-02-27 at 10 38 10 PM" src="https://user-images.githubusercontent.com/100593956/221631628-f3378f7a-9c8d-4ae8-b788-6e4e635bdbac.png">

**STEP 1 :- To build a motor driver Circuit,we need the following
components,**


● An Arduino

● A breadboard

● A 220 ohm resistor

● A 2 N 2222 transistor

● A IN 4001 diode

● A 0. 1 microfarad ceramic capacitor

● A DC motor

● A 9 V battery

● Some jumper or hookup wires

**STEP 2 :- WIRING**

Connect all the components as shown in the figure

<img width="284" alt="Screenshot 2023-02-27 at 10 39 49 PM" src="https://user-images.githubusercontent.com/100593956/221631935-76e926d9-c564-4f9c-ae03-100a6900aff6.png">

**STEP 3 :- THE CODE**


### Upload the following code to arduino.

**int MotorPin = 10;**

**void setup()**

**{**

**pinMode(MotorPin, OUTPUT);**

**}**

**void loop()**

**{**

**analogWrite(MotorPin, 200 ); //Any value between 0 to 255**

**delay ( 10000 ); //Wait for 10 secs**

**analogWrite(MotorPin, 100 ); //Any value between 0 to 255**

**delay ( 10000 ); //Wait for 10 secs**

**}**


##### STEP 4 :- DONE

Now Power the arduino and see your motor spinning with varying speeds.

### CONCLUSION:-

In this document,we learned about the basics of motor drivers and how can we put them into use.
