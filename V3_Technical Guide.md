# The Completely Unofficial Eaglemoss Vector 3 3D Printer Firmware Technical Guide

![alt text][logo]

[logo]: https://www.eaglemoss.com/uploads/141647767867724/original.png "Eaglemoss Vector 3 Firmware Technical Guide"

# Version 1.01.x
## V3 Firmware releases
   ### 2016/07/01 Firmware release
   **V3-Sprinter-Melzi_1_00** The original Eaglemoss Vector 3 firmware release.
   ### 2017/02/24 Firmware release
   **V3-Sprinter-Melzi_1_01** User community version. All future enhancements from Eaglemoss will be incorporated into this user community release. New features include an I2C driven LCD, the ability to use a Z height probe, M42 support, a simplified experimental I2C bus (pinched from Marlin) and PC style beep Error codes.
   ### 2017/06/17 Firmware release
   **V3_Sprinter_Melzi_1_00a** The new Eaglemoss Vector 3 firmware release. Fixes the thermistor tables and improved thermistor error detection.

## 2. Main board pin out
   ### 2.a Pin definition for the Vector 3
   ### 2.b Pin assignments on the Vector 3
   
# Section 2 The pin asignments

## 2.a Pin definition for the Vector 3

   ATMEL ATMEGA644/ATMEGA1284 / SANGUINO
  
                          +---\/---+
              (D 0) PB0  1|        |40  PA0 (AI 0 / D31)
              (D 1) PB1  2|        |39  PA1 (AI 1 / D30)
         INT2 (D 2) PB2  3|        |38  PA2 (AI 2 / D29)
          PWM (D 3) PB3  4|        |37  PA3 (AI 3 / D28)
       SS PWM (D 4) PB4  5|        |36  PA4 (AI 4 / D27)
         MOSI (D 5) PB5  6|        |35  PA5 (AI 5 / D26)
         MISO (D 6) PB6  7|        |34  PA6 (AI 6 / D25)
          SCK (D 7) PB7  8|        |33  PA7 (AI 7 / D24)
                    RST  9|        |32  AREF
                    VCC 10|        |31  GND
                    GND 11|        |30  AVCC
                  XTAL2 12|        |29  PC7 (D 23)
                  XTAL1 13|        |28  PC6 (D 22)
         RX0 (D 8)  PD0 14|        |27  PC5 (D 21) TDI
         TX0 (D 9)  PD1 15|        |26  PC4 (D 20) TDO
    INT0 RX1 (D 10) PD2 16|        |25  PC3 (D 19) TMS
    INT1 TX1 (D 11) PD3 17|        |24  PC2 (D 18) TCK
         PWM (D 12) PD4 18|        |23  PC1 (D 17) SDA
         PWM (D 13) PD5 19|        |22  PC0 (D 16) SCL
         PWM (D 14) PD6 20|        |21  PD7 (D 15) PWM
                          +--------+

## 2.b Pin assignmens for the Vector 3

/****************************************************************************************
* Sanguinololu pin assignment
*
****************************************************************************************/
#if MOTHERBOARD == 62  
#define MOTHERBOARD 6  
#define SANGUINOLOLU_V_1_2  
#endif  
#if MOTHERBOARD == 6  
#define KNOWN_BOARD 1  
#ifndef __AVR_ATmega644P__  
#ifndef __AVR_ATmega1284P__  
#error Oops!  Make sure you have the appropriate 'Sanguino' selected from the 'Tools -> Boards' menu.  
#endif  
#endif  

//x axis pins

#define X_STEP_PIN         15  
#define X_DIR_PIN          21  
#define X_MIN_PIN          18  
#define X_MAX_PIN          -2  

//y axis pins  

#define Y_STEP_PIN         22  
#define Y_DIR_PIN          23  
#define Y_MIN_PIN          19  
#define Y_MAX_PIN          -1  

//z axis pins

#define Z_STEP_PIN         3  
#define Z_DIR_PIN          2  
#define Z_MIN_PIN          -1  
#define Z_MAX_PIN          20  

//extruder pins  

#define E_STEP_PIN         1  
#define E_DIR_PIN          0  



#define PROBE_PIN          11     // TX1 on V3  
//#define PROBE_PIN          29    //29 on Melzi1284p A2  


#define LED_PIN            27  

#define FAN_PIN            4  

#define PS_ON_PIN          -1  
#define KILL_PIN           -1  

#define HEATER_0_PIN       13 // (extruder)  

#ifdef SANGUINOLOLU_V_1_2  

#define HEATER_1_PIN       12 // (bed)  
#define X_ENABLE_PIN       14  
#define Y_ENABLE_PIN       14  
#define Z_ENABLE_PIN       26  
#define E_ENABLE_PIN       14  

#else  

#define HEATER_1_PIN       14  // (bed)  
#define X_ENABLE_PIN       -1  
#define Y_ENABLE_PIN       -1  
#define Z_ENABLE_PIN       -1  
#define E_ENABLE_PIN       -1  

#endif  

#define TEMP_0_PIN          7   // MUST USE ANALOG INPUT NUMBERING NOT DIGITAL OUTPUT NUMBERING!!!!!!!!! (pin 33 extruder)  
#define TEMP_1_PIN          6   // MUST USE ANALOG INPUT NUMBERING NOT DIGITAL OUTPUT NUMBERING!!!!!!!!! (pin 34 bed)  
#define SDPOWER          -1  
#define SDSS          31

