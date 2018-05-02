# Connected-Home-Environment
#This Project is about the Monitoring indoor air quality of the Home. 
#In this repository we detected CO2(Carbon Dioxide), CO(Carbon Monoxide), LPG(Liquid Petroleum Gas), SMOKE and also 
#Temperature and Humidity using "Raspberry Pi" and some 
#sensors like MQ-2, MQ-135, DS18B20 and DHT22 etc.

#To start this project you have to do the thing step by step using saperate sensor

$1. DS18B20 Sensor
#This sensor is for monitoring Temperature in Celsius and Fahrenheit.
ABOUT THE DS18B20
The DS18B20 communicates with the “One-Wire” communication protocol, 
a proprietary serial communication protocol that uses only one wire to transmit the temperature readings to the microcontroller.

The DS18B20 can be operated in what is known as parasite power mode.
Normally the DS18B20 needs three wires for operation: the Vcc, ground, and data wires. 
In parasite mode, only the ground and data lines are used, and power is supplied through the data line.

The DS18B20 also has an alarm function that can be configured to output a signal 
when the temperature crosses a high or low threshold that’s set by the user.

A 64 bit ROM stores the device’s unique serial code. 
This 64 bit address allows a microcontroller to receive temperature data from a virtually unlimited number of sensors at the same pin.
The address tells the microcontroller which sensor a particular temperature value is coming from.

TECHNICAL SPECIFICATIONS
1. -55°C to 125°C range
2. 3.0V to 5.0V operating voltage
3. 750 ms sampling
4. 0.5°C (9 bit); 0.25°C (10 bit); 0.125°C (11 bit); 0.0625°C (12 bit) resolution
5. 64 bit unique address
6. One-Wire communication protocol

ENABLE THE ONE-WIRE INTERFACE
We’ll need to enable the One-Wire interface before the Pi can receive data from the sensor. Once you’ve connected the DS18B20, power up your Pi and log in, then follow these steps to enable the One-Wire interface:

1. At the command prompt, enter: sudo nano /boot/config.txt, then add this to the bottom of the file:

dtoverlay=w1–gpio

2. Exit Nano, and reboot the Pi (sudo reboot)

3. Log in to the Pi again, and at the command prompt enter sudo modprobe w1–gpio

4. Then enter sudo modprobe w1-therm

5. Change directories to the /sys/bus/w1/devices directory by entering: cd /sys/bus/w1/devices

6. Now enter ls to list the devices:
28-000006637696 w1_bus_master1 is displayed in my case.

7. Now enter cd 28-XXXXXXXXXXXX (change the X’s to your own address)

For example, in my case I would enter: cd 28-000006637696

8. Enter cat w1_slave which will show the raw temperature reading output by the sensor:
Here the temperature reading is t=28625, which means a temperature of 28.625 degrees Celsius.

9. Enter cd to return to the root directory
NO GO TO RASPBERRY PI Command prompt and type 

$ python Tempcelfah.py  Enter
