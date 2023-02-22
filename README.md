# CO^2 Sensor exercise
Today we will connect a CO^2 sensor to our Pycom boards and read sensor-values from it.
This could provide valuable information to check the air quality of a classroom, building or even a city.

The exercise is split into two parts. First we need to connect the sensor to our pycom board, and second we need to program it to talk with the sensor

## Connect the sensor
To connect the sensor to the Pycom device, each pin on the sensor should be wired to the correct pins on the Pycom device. Luckily each Pycom device is connected to an expansion board which allows us to wire without soldering. 
The SCD30 sensor supports the [I2C](https://en.wikipedia.org/wiki/I%C2%B2C) protocol which uses two pins for communication and two for power.

> What are the roles of the communication pins? Why are they named the way they are?


On the sensor each pin are named to denote what they do. The pins we need are:

| Pycom Expansion Board | SCD30 |
|-----------------------|-------|
|3V3                    |VIN/VDD|
|GND                    |GND    |
|SDA                    |RX/SDA |
|SCL                    |TX/SCL |


![pinout](https://docs.pycom.io/gitbook/assets/lopy4-pinout.png)


Using the above pinout and the provided wires, you can connect the sensor to the Pycom device. 
In general be careful to ensure that you have wired everything correctly. 

## Program the sensor
Now that you have the sensor connected we want to be able to read measurements from it. To do this we need to establish an I2C connection to it. Luckily a MicroPython library exists that does this for us. 

Create a new Pymakr project, and create a `lib` folder in the root of your project.
Download the `scd30.py` file from https://github.com/agners/micropython-scd30 and place it in the `lib` folder.

Then in our `main.py` we need to initialize the I2C connection and with that initialize our sensor.

This is all up for you to figure out. Using the documentation for I2C on pycoms website (https://docs.pycom.io/tutorials/hardware/i2c/) and the example from the SCD30 library you should write a program that reads from the sensor and prints the value to the console.


There are samples on both the Pycom web


# Acknowledgements
This exercise is inspired from exercise 3 from a previous iteration of the IoT Course (https://github.com/ITU-DASYALab/IoT_course/blob/main/assignments/assignment1.md)
and it uses the SCD30 micropython library made by Agners (https://github.com/agners/micropython-scd30)