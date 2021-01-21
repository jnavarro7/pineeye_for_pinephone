# PineEye Thermal imaging solution for the PinePhone
 Thermal imaging board aimed to be used with the PinePhone. It uses the Panasonic AMG8833 sensor.   

![alt tag](/pictures/1.png)

Sensor is attached to the pogo pin expansion port on the back of the PinePhone and to the I2C port exposed here.  It is numbered as i2c-3 in multiple operating systems.
To expose the pogo pins I use my other design which is the flex PCB shown in the pictures.   

<a href="https://github.com/jnavarro7/pinephone_flex_breakout_board" title="PinePhoone flex breakout board">PinePhone flex breakout board</a>

## The address of the AMG8833 can be setup using resistors R1 and R2:
* Pullup   - 0x69
* Pulldown - 0x68

![alt tag](/pictures/2.png)

## Initial tests
For the initial tests we use i2c-tools 
To install in Mobian:

    sudo apt-get update && sudo apt-get install i2c-tools -y

To install in Manjaro:

    sudo pacman -Syu && sudo pacman -S i2c-tools

To check for I2C ports available:

    i2cdetect -l 

To check for devices in an specific port in this case in port i2c-3 which is the one exposed on the back of the Pinephone:

    i2cdetect -y 3

To read a register on the sensor we use i2cget then give the port number "3" then the address of the sensor "0x68" and last the register we want to read in this case "0x80" which gives you a value that represents the temperature read by one of the pixels in the sensor:

    i2cget 3 0x68 0x80

![alt tag](/pictures/3.png)

![alt tag](/pictures/5.png)

![alt tag](/pictures/4.png)


## Drivers

Tests drivers I have been creating to test the system will be located here <a href="https://github.com/jnavarro7/pineeye_pinephone_drivers" title="Drivers repo">Drivers repo</a>


## Design

The design was created using <a href="https://diptrace.com" title="DipTrace">DipTrace</a>

## Try it for yourself
You can get the board from OSH Park using this direct link to order the project. 

<a href="https://oshpark.com/shared_projects/Z65YHSF2"><img src="https://oshpark.com/packs/media/images/badge-5f4e3bf4bf68f72ff88bd92e0089e9cf.png" alt="Order from OSH Park"></img></a>


## License

Released under the Creative Commons Attribution 3.0 License
https://creativecommons.org/licenses/by/3.0/