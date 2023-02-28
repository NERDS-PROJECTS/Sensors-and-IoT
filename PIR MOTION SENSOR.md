
**Ujjwal Saxena**
(2115063)

***PIR Motion Sensor***

**CONTENT FLOW**

- Overview
- Objectives
- Working Principles
- What does a PIR Sensor detects
- Working
- Pin Configuration
- Connecting and Testing
- Practical applications
- Advantage and Disadvantages
- Conclusion

**OVERVIEW**

PIR sensor is a small low-priced Passive infrared motion detector sensor. As the name suggests it doesn’t emit radiation (unlike an Infrared (IR) Sensor which emits infrared radiation) but it detects the changes in infrared radiation of the source. It's very facile to use and hence used in diverse applications.

![Aspose Words be0a63b0-3c52-4f3d-a4cf-5d66785e66b2 002](https://user-images.githubusercontent.com/86782553/221925466-81e50ed4-7b34-44a2-bbdb-548842f7b7f2.jpeg)




**OBJECTIVES**
1. To study about the PIR Sensor.
1. To understand the working of PIR Sensor.
1. To understand practical applications of PIR Sensor.

**WORKING PRINCIPLE**

The PIR Sensor, detects the change of Infrared radiation/ Heat energy in the surrounding, caused due to motion of an heat emitting body (as, every body emits some radiation/ heat ), and gives an digital output as an response.

**WHAT DOES A PIR SENSOR DETECTS**

Generally, PIR sensors can detect animal/human movement in a requirement range. PIR is made of a pyroelectric sensor, which is able to detect different levels of infrared radiation. The detector itself does not emit any energy but passively receives it

It detects infrared radiation from the environment. Once there is infrared radiation from the human body particle with temperature, focusing on the optical system causes the pyroelectric device to generate a sudden electrical signal.

![Aspose Words be0a63b0-3c52-4f3d-a4cf-5d66785e66b2 003](https://user-images.githubusercontent.com/86782553/221925595-98e7d85b-21be-4eff-8295-d1fed329f3db.png)


**WORKING**

The PIR sensor has two slots in it, each slot is made of a special material that is sensitive to IR. The lens used here is not really doing much and so we see that the two slots can 'see' out past some distance (basically the sensitivity of the sensor). When the sensor is idle, both slots detect the same amount of IR, the ambient amount radiated from the room or walls or outdoors. When a warm body like a human or animal passes by, it first intercepts one half of the PIR sensor, which causes a positive differentialchange between the two halves. When the warm body leaves the sensing area, the reverse happens, whereby the sensor generates a negative differential change. These change pulses are what is detected.

![Aspose Words be0a63b0-3c52-4f3d-a4cf-5d66785e66b2 004](https://user-images.githubusercontent.com/86782553/221926365-71ee1958-c688-4148-bb56-c577fbf146f3.jpeg)


**PIN CONFIGURATION**

A PIR Sensor consists of 3 basic pins.

The below image shows a typical pin configuration of the PIR sensor, which is quite simple to understand the pinouts.

![Aspose Words be0a63b0-3c52-4f3d-a4cf-5d66785e66b2 005](https://user-images.githubusercontent.com/86782553/221925873-e2ee4ce2-217b-4b83-9d17-167c9b9344b3.jpeg)

1. **Pin1 (3-5 V DC POWER)** :-corresponds to the drain terminalof the device, which is connected to the positive supply 5V DC.
1. **Pin2 (Digital OUT)** :-corresponds to the source terminalof the device, which connects to the ground terminal via a 100K or 47K resistor. The Pin2 is the output pin of the sensor. The pin 2 of the sensor carries the detected IR signal to an amplifier from the
1. **Pin3 (GROUND)** :-of the sensor connected to the ground.


**CONNECTION WITH ARDUINO**

Here, we will learn about connecting our PIR Motion Sensor to Arduino Uno

Arduino Uno :An Arduino is an open hardware development board that can be used by tinkerers, hobbyists, and makers to design and build devices that interact with the real world.Arduino Uno

is a microcontroller board based on the ATmega328. It has 20 digital input/output pins (of which 6 can be used as PWM outputs and 6 can be used as analog inputs).

Now we can start working on the circuit :

PIR connections - Connect the Gnd pin of sensor to the ground of Arduino. Vcc pin of the sensor to 5V of Arduino. And signal / output pin to digital pin 5 of Arduino board.

![Aspose Words be0a63b0-3c52-4f3d-a4cf-5d66785e66b2 006](https://user-images.githubusercontent.com/86782553/221926001-58f0e1fe-58d5-4ace-a01c-fb495031a7e7.jpeg)

Led connections - Positive terminal of the led to digital pin 9 of Arduino. Negative terminal should be connected to any one leg of the resistor. Another leg of the resistor should be connected to the Gnd of the Arduino.

![Aspose Words be0a63b0-3c52-4f3d-a4cf-5d66785e66b2 007](https://user-images.githubusercontent.com/86782553/221926302-43c5fc0b-f1c6-432c-93bc-698d7557559e.png)


**CODE**

const int led = 9; // Led positive terminal to the digital pin 9.

const int sensor = 5; //signal pin of sensor to digital pin 5.

const int state = LOW;

const int val = 0;

void setup() { // Void setup is ran only once after each powerup or reset of the Arduino board.

pinMode(led, OUTPUT); // Led is determined as an output here.

pinMode(sensor, INPUT); // PIR motion sensor is determined is an input here.

Serial.begin(9600); }

void loop(){ // Void loop is ran over and over and consists of the main program.

val = digitalRead(sensor);

if (val == HIGH) {

digitalWrite(led, HIGH);

delay(500); // Delay of led is 500

if (state == LOW) {

Serial.println(" Motion detected");

state = HIGH;

} }

else {

digitalWrite(led, LOW);

delay(500);

if (state == HIGH){

Serial.println("The action/ motion has stopped");

state = LOW;

}

}

}


**PRACTICAL APPLICATIONS**

Here are some of the popular applications of PIR sensors.

1. Lighting Control
1. Smart Home and IoT Applications
1. Motion Detection Using PIR Sensor
1. Automatic Door Opening System
1. Security Alarm System Based on PIR Sensor
1. Human Detection Robot Using PIR Sensor
1. PIR Sensor Based on Stepper Motor Control
1. Multi-Function Printers
1. Video-Conference Systems
1. Digital Signage

**ADVANTAGES AND DISADVANTAGES Advantages:-**

1. Detects motion reliably indoors as well as in day or dark.
1. It consumes less energy (0.8W to 1.0W) compared to a microwave sensor.
1. They are cheaper compared to microwave sensors.
1. Due to its small size, they are good for electrical applications used in smaller and compact premises.

**Disadvantages:-**

1. They have lower sensitivity and less coverage compared to microwave sensors.
1. It does not operate above some specific temperature.
1. It works effectively in LOS (Line of Sight) and will have problems in the corner regions.
1. It is insensitive to the very slow motion of the objects.
1. Since PIR sensors sense heat signatures in a room, they are not very sensitive if the room itself is warm. Hence PIR sensors are not able to detect human beings in the summer.
1. Snoozing is another problem with PIR sensors. PIR sensors may turn off even if there is very little movement in occupied floors.
1. Thieves may find it easy to fool PIR detection range as they have a slotted detection zone and not continuous one like a microwave sensor.


**CONCLUSION**

In this article, we have learned the PIR sensor is a highly versatile and reliable device that is perfect for motion detection applications. With its simple working principle and easy-to-use interface, it can detect motion and presence with great accuracy. Whether you want to detect intruders, automate lighting, or trigger alarms, a PIR sensor is a must-have in your toolkit.
