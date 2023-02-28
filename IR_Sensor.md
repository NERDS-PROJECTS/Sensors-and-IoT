## N.E.R.D.S ||  Documentation
# Topic: Infrared Sensor                                               
by:- Indrajit Ray.
## 
# Introduction :
**An infrared (IR)** sensor is an electronic device that measures and detects infrared radiation in its surrounding environment.There are two types of infrared sensors: active and passive. Active infrared sensors both emit and detect infrared radiation. Active IR sensors have two parts: a light emitting diode (LED) and a receiver. When an object comes close to the sensor, the infrared light from the LED reflects off of the object and is detected by the receiver. Active IR sensors act as proximity sensors, and they are commonly used in obstacle detection systems (such as in robots).

# LED:
(Light Emitting Diode) An  LED is a type of diode or simple semiconductor. Electric current is allowed to flow in only one direction in diodes. As the current flows, electrons fall from one part of the diode into holes on another part. In order to fall into these holes, the electrons must shed energy in the form of photons, which produce light.

![download](https://user-images.githubusercontent.com/97835920/221942877-da896472-7ac8-46b8-a240-b4a01aa2597b.jpg)


# THEORY:
**Infrared light (IR)** is based on the principles of optics. An IR proximity sensor works by applying a voltage to a pair of IR light-emitting diodes (LEDs) which in turn, emit infrared light. This light propagates through the air and once it hits an object it is reflected towards the sensor.

# Working of IR:
An IR sensor consists of two parts, the emitter circuit, and the receiver circuit. This is collectively known as a photo-coupler or an optocoupler.
The emitter is an IR LED and the detector is an IR photodiode. The IR photodiode is sensitive to the IR light emitted by an IR LED

![image](https://user-images.githubusercontent.com/97835920/221944398-9620bea3-135b-479a-bfd1-7f173233ffb9.png)



# Components of IR Sensors:
1. IR Emitter LED
2. IR Receiver
3. Distance Adjust(Trim-pot adjust)
4. Power LED
5. Obstacle LED
6. Comparator OP-Amp

 ![image](https://user-images.githubusercontent.com/97835920/221944748-c17380bc-12f4-4a62-a5eb-a2a62009b381.png)
 



                                        Figure: IR Sensor Diagram


# Types of IR:
There are several types of IR sensors, each with different characteristics and applications. Some common types include:

**Passive Infrared (PIR) Sensor:** PIR sensors are used to detect motion by sensing changes in infrared radiation. They are commonly used in security systems, lighting control, and automatic doors.

**Reflective IR Sensor:** Reflective IR sensors use infrared LED to emit infrared light and a phototransistor to detect the reflected light from an object. They are used to measure distance and detect proximity.

**Transmissive IR Sensor:** Transmissive IR sensors use infrared LED to emit infrared light and a phototransistor to detect the light that passes through an object. They are used to measure distance and detect proximity.

**IR proximity Sensor:** IR proximity sensors are used to detect the presence of an object without making physical contact. They are commonly used in mobile devices, robotics, and automation systems.

**IR temperature Sensor:** These can measure the temperature of an object by detecting the infrared radiation emitted by it. They are used in industrial, HVAC, and medical applications.

**IR spectroscopy Sensor:** These can use infrared radiation to analyze the properties of a substance. They are used in chemical analysis, medical diagnosis, and environmental monitoring.

**IR Imaging sensor:** These sensors use infrared radiation to create images, they are used in thermal imaging, night vision, and surveillance cameras

# Projects that can be made from IR Sensor:
1. Line Follower Robot.
2. Burglar Alarm.
3. IR music transmitter and emitter.
4. Wireless security system using PIR.

 ##  Arduino code for interfacing IR Sensor
/*** Arduino with IR Sensor ***/

int SensorPin = 2;

int OutputPin = 13;

void setup() {

  pinMode(OutputPin, OUTPUT);
  
  pinMode(SensorPin, INPUT);
  
  Serial.begin(9600);
}

void loop() {

  int SensorValue = digitalRead(SensorPin);
  
  Serial.print("SensorPin Value: ");
  
  Serial.println(SensorValue);
  
  delay(1000);
  
   if (SensorValue==LOW){
   
 // LOW MEANS Object Detected
 
    digitalWrite(OutputPin, HIGH);
  }
  
  else
  
  {
  
    digitalWrite(OutputPin, LOW); 
    
  }
  
}

![image](https://user-images.githubusercontent.com/97835920/221945180-148aee87-407b-4aa4-8970-e409fee38d78.png)

RESULT: You should see your LED turn ON, when an object comes in the range of the IR Sensor. If you cannot see the desired output, ensure the circuit has been properly assembled, and verified and uploaded the code to your board.

## Disadvantages of infrared sensor:

1. Limited range, support a shorter range.
2. Get blocked by common objects.
3. Can be affected by environmental conditions such as rain, fog, dust, pollution, sunlight, smoke, etc.
4. Infrared waves at high power can damage eyes.
