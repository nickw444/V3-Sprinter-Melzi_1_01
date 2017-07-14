# V3-Sprinter-Melzi_1_01
The original Eaglemoss V3 3D printer firmware cleaned up and modified. 

Nominally called Version 1.01

Tonokip RepRap firmware rewrite based off of Hydra-mmm firmware.

Based on https://github.com/reprappro/Firmware/tree/master/Sprinter_Melzi
V3 parts http://rp3d.com/ 
I2C_lcd  Suusi Malcolm-Brown

Licence: GPL

Arduino 0023 is required for the build and upload.

Almost all V3 specific code and all V3 specific variables have been moved to two new files unsurpringly called V3.cpp and V3.h
added a function to handle the V3 I2C device and the necessay defines 

All instances of V3 specific code on Sprinter_Melzi_Play.pde is now enclosed in #ifdef V3, #else and #endif as required

I2C_LCD needs F Malpartida's NewLiquidCrystal library. Download the repository from https://bitbucket.org/fmalpartida/new-liquidcrystal/downloads and put it in your documents/arduino/libraries folder and restart your ide.

You need to modify libuary file LiquidCrystal_I2C_ByVac.h to get the program to compile in Arduino 0023 

2016/12/19 Added:
I2C_lcd.h to contain the I2C lcd specific declarations.
I2C_lcd.cpp to contain the I2C lcd specific functions etc.
global int btt to store the target heated bed temperature in degrees C.
global int ett to store the extrude traget temprature in degrees C.
global bool bFanOn to store fan status: true = on, false = off.
added a call to SplashScreen() to setup().
added call to StatusScreen() to funtion gcode_M190() to update status screen whist waiting for the bed to get to temperature.
added call to StatusScreen() to funtion wait_for_temp() to update status screen whist waiting for the extruder to get to temperature.

2017/01/22 Added:
enabled the code for G29 / G30 G Code Currently residing in the LCD-modifications branch

2017/02/24 Added:
Added StatusScreen() to setup()
Fixed bug in UUID on the LCD SplashScreen() by changing char uuid[] = "0000..." to char pointer uuid = "0000..."
Merged LCD and master branches

2017/02/25 Added:
fixed bug in M190 so LCD displays increasing temperature
fixed bug in status strings.

2017/02/26 Added: 
Displaying printer state on LCD "Sprinter: Idle", "Sprinter: Heating", "Sprinter: Printing", "Sprinter: Done"

2017/02/27 Added: 
Fixed Bug in displaying printer state on the LCD. 

2017/02/28 Added:
Made the check_PauseID() function in V3.cpp more readable through a series of defines in V3.h
Fixed bug in M109 that was preventing the LCD from displaying the extruder Temperature as it rose from ambient to target temperature.
Changed printer name from "Vector 3 3D printer" to "Vector 3"
fixed centering bug in SplashScreen() 
Displaying printer state on LCD to "Vector 3: Idle", "Vector 3: Heating", "Vector 3: Printing", "Vector 3: Done"

2017/07/14 Added:
Added M42 function works on M42 A1 S1 syntax as per Bill and M42 P30 S1 as per reprap wikki. A V3 melzi specific version of Klimet's code 
