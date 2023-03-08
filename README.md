# Air Quality Sensor Exercise
Today we will connect an air quality sensor to our Pycom boards and read measurements from it.
A real world use-case for this could be to check the air in a classroom, building or even a city.

The air quality sensor we will use is the [Sensirion SCD30](https://sensirion.com/products/catalog/SCD30/).

The exercise is split into two parts. First we need to connect the sensor to our Pycom board, and second we need to program the Pycom device to talk with the sensor.

## 1. Connect the sensor
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
In general be careful to ensure that you have wired everything correctly. Check the pinout diagram to find the needed pins and ensure the names are the same as the printed names on the board where the wires are plugged in.


## 2. Program the sensor
Now that you have the sensor connected we want to be able to read measurements from it. To do this we need to establish an I2C connection to it. Luckily a MicroPython library exists that does this for us. 

Create a new Pymakr project, and create a `lib` folder in the root of your project.
Download the `scd30.py` file from https://github.com/agners/micropython-scd30 and place it in the `lib` folder.

Then in our `main.py` we need to initialize the I2C connection and with that initialize our sensor.

This is all up for you to figure out. Using the documentation for I2C on Pycoms website (https://docs.pycom.io/tutorials/hardware/i2c/) and the example from the SCD30 library you should write a program that reads from the sensor and prints the CO2 level, temperature and relative humidity to the console.



### Notes
- When you want to run the code, remember to upload all files to the Pycom device, and not just `main.py`. Pressing the button that looks like a cloud with an arrow pointing into it does that.
- if you have problems getting the I2C connection to work, try changing the bus from `0` to `2`. For some reason, bus `0` sometimes doesn't work.

>### Food for thought
>- Is the SCD30 an analog or digital sensor?
>- How do we translate from an analog signal to a digital one? Is there any loss of information?
>- Are the measurements it gives correct? What might influence them?
>- How do we even know if they're correct? Can we take steps to ensure or check for correctness?

# Acknowledgements
This exercise is inspired from exercise 3 from a previous iteration of the IoT Course (https://github.com/ITU-DASYALab/IoT_course/blob/main/assignments/assignment1.md)
and it uses the SCD30 micropython library made by Agners (https://github.com/agners/micropython-scd30)
