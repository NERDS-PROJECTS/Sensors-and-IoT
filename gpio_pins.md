# GPIO Pins			   

**By : Sanidhya Kumar Patra**

## INTRODUCTION
GPIO stands for General-Purpose Input/Output. These pins are a physical interface between the Raspberry Pi and the outside world. At the simplest level, you can think of them as switches that you can turn on or off (input) or that the Pi can turn on or off (output). The GPIO pins allow the Raspberry Pi to control and monitor the outside world by being connected to electronic circuits. The Pi is able to control LEDs, turning them on or off, run motors, and many other things. It’s also able to detect whether a switch has been pressed, *the temperature, and light. We refer to this as physical computing.

![download](https://user-images.githubusercontent.com/69229860/221931236-26d98bd7-d3d5-4eb4-88e1-1168ceff439d.png)

Figure : Pins on Raspberry Pi

There are 40 pins on the Raspberry Pi (26 pins on early models), and they provide various different functions. If you have a RasPiO pin label, it can help to identify what each pin is used for. Make sure your pin label is placed with the keyring hole facing the USB ports, pointed outwards.

If you don’t have a pin label, then this guide can help you to identify the pin numbers:

![cc911ae9-fd0c-4f36-8abd-4a63f7050685](https://user-images.githubusercontent.com/69229860/221933296-0d46f940-6cd5-4f03-924e-d1cb20378059.jpg)

Figure : Pin Guide
If you're coming to the Raspberry Pi as an Arduino user, you're probably used to referencing pins with a single, unique number. Programming the Pi's hardware works much the same, each pin has its own number.
There are (at least) two, different numbering schemes you may encounter when referencing Pi pin numbers: (1) Broadcom chip-specific pin numbers and (2) P1 physical pin numbers. You're usually free to use either number-system, but many programs require that you declare which scheme you're using at the very beginning of your program. The Broadcom pin numbers relate to Pi Model 2 and later only.


Voltages
From the above diagram, we can see that there are two 5V pins and two 3V3 pins on the board. It also has several ground pins (0V). All these pins are unconfigurable.
Outputs
A GPIO pin can be designated as an output pin. The pin set as output pin can be set to 3V3(high) or 0V(low).
Inputs
A GPIO pin can be designated as an input pin. The pin set as input pin can be read as 3V3(high) or 0V(low). You can use internal pull-up or pull-down resistors.
You can see in the above diagram, GPIO2 and GPIO3 pins have fixed pull-up resistors but for the other pins, you can configure it in software.

Alternative Functions
GPIO pins can be used with a variety of alternative functions. Among them, some are available on all pins and others on specific pins.
PWM: Pulse-width modulation
Pulse width modulation (PWM) is a modulation technique that generates variable-width pulses to represent the amplitude of an analog input signal. The output switching transistor is on more of the time for a high-amplitude signal and off more of the time for a low-amplitude signal.
Software PWM are available on all the pins whereas Hardware PWM are available on GPIO12, GPIO13, GPIO18, and GPIO19.

SPI: Serial Peripheral Interface
The Serial Peripheral Interface (SPI) is a communication protocol used to transfer data between micro-computers like the Raspberry Pi and peripheral devices. These peripheral devices may be either sensors or actuators. In this example, we will be learning to use an Analog to Digital Converter (ADC) sensor. An analog to digital sensor takes an analog voltage and converts it into a digital number that can be understood by the Raspberry Pi.
The SPI are available on the following −
i. SPI0: MOSI (GPIO10); MISO (GPIO9); SCLK (GPIO11); CE0 (GPIO8), CE1 (GPIO7)
ii. SPI1: MOSI (GPIO20); MISO (GPIO19); SCLK (GPIO21); CE0 (GPIO18); CE1 (GPIO17);         CE2 (GPIO16)

I2C: Inter-integrated Circuit
Inter-integrated circuit (I2C) is a system for serial data exchange between the microcontrollers and specialized integrated circuits of a new generation. It is used when the distance between them is short (receiver and transmitter are usually on the same printed board). Connection is established via two conductors. One is used for data transfer and the other is used for synchronization (clock signal).
The I2C are available on the following −
i. Data: (GPIO2); Clock (GPIO3)
ii. EEPROM Data: (GPIO0); EEPROM Clock (GPIO1)
Here's an example C code to establish I2C communication with a device on a Raspberry Pi using the ‘wiringPi’ library:
![7b457855-d19c-4dc5-8d09-9023de0d9184](https://user-images.githubusercontent.com/69229860/221933458-323241a2-222d-4af4-9125-8a62125bb0b2.jpg)



In the example above, we're using the ‘wiringPiI2C’ library to open the I2C bus, write a byte to a register, and read a byte from a register on the device. Note that the ‘wiringPiI2CSetup’ function returns a file descriptor for the I2C bus, which we use in the ‘wiringPiI2CWriteReg8’ and ‘wiringPiI2CReadReg8’ functions to communicate with the device.
Make sure to compile the program with the ‘-lwiringPi’ option to link against the ‘wiringPi’ library. You can do this with the following command (assuming your file is named program.c) :

gcc -o program program.c -lwiringPi



Serial Communication (With UART)
Serial communication is simply a way to transfer data. The data will be sent sequentially, one bit at a time (1 byte = 8 bits), contrary to parallel communication, where many bits are sent at the same time. 
UART protocol
More specifically, when you use Serial with Arduino and Raspberry Pi, you’re using the UART protocol. UART means “Universal Asynchronous Reception and Transmission”.
Basically it’s an asynchronous multi-master protocol based on the Serial communication, which will allow you to communicate between the 2 boards. Be reassured, there are libraries that will handle all the low layers for you.
The Arduino Uno board has one UART that you can use either with a USB cable or from the RX/TX pins (don’t use it with both at the same time). Some boards have more available UARTs. For example the Arduino Mega has different Serials (Serial, Serial1, Serial2, Serial3) and the Arduino Zero has a native USB port only (use SerialUSB instead of Serial).
On the Raspberry Pi, you can connect many Serial devices on the USB ports. Each will have a different device name (we’ll see how to find them later in this tutorial). You can also use the GPIOs (RX0/TX0) for an additional UART.
Serial via GPIOs
To make a Serial connection you can also use plain wires between the Raspberry Pi GPIOs and the Arduino pins.

![91e43f85-9bbd-49ae-90d8-04a383a8f654](https://user-images.githubusercontent.com/69229860/221933548-30b516b5-65a8-4fd2-aa5d-98ed36018b48.jpg)

Figure : Serial connection between Raspberry Pi GPIOs and the Arduino pins
Depending on your Arduino board you might need to use a voltage level-shifter. The Raspberry Pi is operating at 3.3V. For Arduino boards like Due, 101, it will be fine because they also use 3.3V.
But, for many Arduino, such as Uno, Mega, Leonardo, Nano, and many more, the board is operating at 5V. Thus, you need a 3.3V/5V level-shifter to protect the Raspberry Pi when connecting RX and TX.
I2S Protocol
I2S, or Inter-IC Sound, is a serial communication protocol that is commonly used for digital audio transmission. It is widely used in audio applications, including digital signal processors, digital-to-analog converters, and other audio equipment. In the Raspberry Pi, I2S is a standard way of transmitting audio data between different devices.
The Raspberry Pi has several pins that can be used for I2S communication. These include GPIO pins 18, 19, 20, 21, and 28, which are the clock, data in, data out, word select, and channel select pins, respectively. These pins are connected to the I2S bus, which is used to transfer audio data.
To use I2S on the Raspberry Pi, you need to enable it by editing the configuration file. This can be done by opening the terminal and typing:
sudo nano /boot/config.txt
This will open the configuration file in the nano text editor. To enable I2S, you need to uncomment the following line:
dtparam=i2s=on

![b9ef9252-bb3c-4793-af07-52e76098f257](https://user-images.githubusercontent.com/69229860/221933641-a70758e9-1a3d-48f6-9863-3635aa3e1c2c.jpg)

Figure : I2S output on Pi Zero Model
Once this line is uncommented, you can save and close the file by pressing Ctrl+X, then Y, then Enter.
After enabling I2S, you can connect your Raspberry Pi to an I2S device, such as a digital-to-analog converter or an audio amplifier. The connections should be made as follows:
Clock pin: This pin should be connected to the clock pin of the I2S device.
Data in pin: This pin should be connected to the data in pin of the I2S device.
Data out pin: This pin should be connected to the data out pin of the I2S device.
Word select pin: This pin should be connected to the word select pin of the I2S device.
Channel select pin: This pin should be connected to the channel select pin of the I2S device.
Once the connections are made, you can play audio through the I2S device using a program like VLC media player or the Raspberry Pi's built-in audio player, ‘aplay’.
