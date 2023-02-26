# ULTRASONIC SENSORS

_HC-SR04 Ultrasonic sensor for Arduino_

![us sensor](RackMultipart20230226-1-ltas8_html_dfcbfd7c660cebd1.jpg)

**N.E.R.D.S**

By Soham Mandal

22.02.2023

# INTRODUCTION

The HC-SR04 ultrasonic sensor uses SONAR technology to determine the distance of an object just like the bats do. Although it is subject to errors in reading, the HC-SR04 is one of the quite reliable sensors you can use on your Arduino board project to this day.

The operation is not affected by sunlight or black material, although soft materials like cloth can be difficult to detect acoustically. It comes complete with an ultrasonic transmitter and receiver module.

# TECHNICAL SPECIFICATIONS

- Power Supply − +5V DC
- Quiescent Current − \<2mA
- Working Current − 15mA
- Effectual Angle − \<15°
- Ranging Distance − 2cm – 400 cm/1″ – 13ft
- Resolution − 0.3 cm
- Measuring Angle − 30-degree
- Trigger Input Pulse width: 10uS TTL pulse
- Echo Output Signal: TTL pulse proportional to the distance range
- Dimension: 45mm x 20mm x 15mm

# COMPONENTS REQUIRED

1. 1x breadboard
2. Arduino UNO R3
3. 1x Ultrasonic sensor HC-SR04

# WORKING

It emits ultrasound at 40 000 Hz which travels through the air and if there is an object or obstacle in its path It will bounce back to the module. Considering the travel time and the speed of the sound you can calculate the distance.

In order to generate the ultrasound we need to set the Trig pin on a High State for 10 µs. That will send out an 8-cycle ultrasonic burst which will travel at the [speed of sound](https://en.wikipedia.org/wiki/Speed_of_sound). The Echo pin goes high right away after that 8-cycle ultrasonic burst is sent, and it starts listening or waiting for that wave to be reflected from an object.

If there is no object or reflected pulse, the Echo pin will time out after 38ms and get back to a low state.

If we receive a reflected pulse, the Echo pin will go down sooner than those 38ms. According to the amount of time, the Echo pin was HIGH, we can determine the distance the sound wave travelled, thus the distance from the sensor to the object.

For that purpose we are using the following basic formula for calculating distance:

Distance = Speed x Time

We actually know both the speed and the time values. The time is the amount of time the Echo pin was HIGH, and the speed is the speed of sound which is 340m/s. There's one additional step we need to do, and that is, to divide the end result by 2. and that's because we are measuring the duration the sound wave needs to travel to the object and bounce back.

Let's say the Echo pin was HIGH for 2ms. If we want the get the distance result in cm, we can convert the speed of sound value from 340m/s to 34cm/ms.

Distance = (Speed x Time) / 2 = (34cm/ms x 1.5ms) / 2 = 25.5cm.

So, if the Echo pin was HIGH for 2ms (which we measure using the pulseIn() function), the distance from the sensor to the object is 34cm.

# PROCEDURE

Follow the circuit diagram and make the connections as shown in the image below.

The Ultrasonic sensor has four terminals - +5V, Trigger, Echo, and GND connected as follows −

- Connect the +5V pin to the +5v on your Arduino board.
- Connect the Trigger to digital pin 7 on your Arduino board.
- Connect Echo to digital pin 6 on your Arduino board.
- Connect GND with GND on Arduino.

![ggg](RackMultipart20230226-1-ltas8_html_23602946521f2995.png)

# SKETCH

Open the Arduino IDE software on your computer. Coding in the Arduino language will control your circuit. Open a new sketch File by clicking New.

# ARDUINO CODE

const int pingPin = 7; // Trigger Pin of Ultrasonic Sensor

const int echoPin = 6; // Echo Pin of Ultrasonic Sensor

long duration, inches, cm;

void setup() {

Serial.begin(9600); // Starting Serial Terminal

pinMode(pingPin, OUTPUT);

pinMode(echoPin, INPUT);

}

void loop() {

digitalWrite(pingPin, LOW);

delayMicroseconds(2);

digitalWrite(pingPin, HIGH);

delayMicroseconds(10);

digitalWrite(pingPin, LOW);

duration = pulseIn(echoPin, HIGH);

inches = microsecondsToInches(duration);

cm = microsecondsToCentimeters(duration);

Serial.print(inches);

Serial.print("in, ");

Serial.print(cm);

Serial.print("cm");

Serial.println();

delay(100);

}

long microsecondsToInches(long microseconds) {

return microseconds / 74 / 2; //div by 74 same as multp by 0.0135

}

long microsecondsToCentimeters(long microseconds) {

return microseconds / 29 / 2; //div by 29 same as multp by 0.034

}

You will see the distance measured by the sensor in inches and cm on Arduino serial monitor.

# DRAWBACKS

Being a physical device, it certainly has some drawbacks. One of the most frequently occurring errors in the sensor is a wrong data output. This can be due to the shear reason that the sonic waves got deflected in some other direction other than towards the receiver. Other factors may include physical conditions that affect the circuitry, damaging it.

# CONCLUSION

So, we have covered pretty much everything that we need to know about using the HC-SR04 Ultrasonic sensor with Arduino. It's a great sensor for many DIY electronics projects where we need non-contact distance measuring, detection of presence or objects, level or position something etc.

Here are some projects using the HC-SR04 sensor and Arduino:

- [Touchless Automatic Motion Sensor Trash Can](https://create.arduino.cc/projecthub/will-su/touchless-automatic-motion-sensor-trash-can-bbeed1?ref=user&ref_id=222561&offset=0)
- [Hand Gesture Smart Light Control](https://hackaday.io/project/19241-mapping-a-room-with-ultrasonic-distance-sensors)
- [Mini Acoustic Levitation](https://create.arduino.cc/projecthub/millerman4487/mini-acoustic-levitation-30177e?ref=tag&ref_id=ultrasonic&offset=24)
- [Obstacle Avoiding Robot](https://create.arduino.cc/projecthub/maverick/pathfinder-229d5d?ref=search&ref_id=Obstacle%20Avoiding%20Robot&offset=23)

####
