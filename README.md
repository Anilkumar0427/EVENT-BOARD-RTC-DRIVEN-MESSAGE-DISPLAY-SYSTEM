# EventBoard – RTC-Driven Message Display System

## Overview

EventBoard is an embedded system project based on the **LPC2148 ARM7 microcontroller** that automatically displays predefined messages on a 16x2 LCD at scheduled times using the built-in **Real Time Clock (RTC)**. The system provides a secure **Admin Mode** for editing time settings and selecting active messages through a keypad with password protection.

The project also monitors room temperature using an **LM35 sensor** and displays real-time information when no scheduled event is active.

## Features

* ⏰ RTC-based automatic message scheduling
* 📟 16x2 LCD message display with scrolling mechanism
* 🔒 Password-protected Admin Mode
* ⌨️ Keypad-based user interaction
* 🌡️ Temperature monitoring using LM35 sensor
* 🟢 Green LED indication for active scheduled messages
* 🔴 Red LED indication for idle mode
* 📅 Support for enabling/disabling scheduled messages
* 🔄 Real-time clock editing functionality

## Hardware Requirements

* LPC2148 Microcontroller
* 16x2 LCD Display
* Matrix Keypad
* LM35 Temperature Sensor
* LEDs (Red & Green)
* Buzzer
* Power Supply

## Software Requirements

* Embedded C
* Keil uVision Compiler
* Flash Magic

## System Workflow

1. The RTC continuously tracks the current time.
2. The controller compares RTC time with stored message schedules.
3. If a scheduled time matches:

   * Corresponding message is displayed on the LCD.
   * Green LED turns ON.
4. If no scheduled message is available:

   * Current RTC time is displayed.
   * Room temperature from LM35 sensor is displayed.
   * Red LED turns ON.
5. Admin can enter secure mode using a switch and password.
6. In Admin Mode:

   * Edit current RTC time.
   * Enable or disable scheduled messages.

## Message Structure

```c
#define TOTAL_MESSAGES 10

typedef struct {
    u8 hour;
    u8 minute;
    char text[80];
    u8 enabled;
} Message;
```

## Sample Scheduled Messages

| Time  | Message                                      |
| ----- | -------------------------------------------- |
| 07:45 | Good Morning! Classes Start Soon             |
| 09:45 | ARM Workshop on External Interrupts          |
| 10:15 | C Module Theory Exam                         |
| 12:45 | Lunch Break                                  |
| 15:15 | Only 15 mins break time for next ARM session |
| 17:45 | End of Day – See You Tomorrow!               |

## Block Diagram

```text
           +----------------+
           |    Keypad      |
           +-------+--------+
                   |
                   v
+--------+   +------------+   +--------+
|  RTC   |-->|  LPC2148   |-->|  LCD   |
+--------+   +------------+   +--------+
                   |
         +---------+---------+
         |                   |
         v                   v
      LM35 Sensor         LEDs
                             
                   |
                   v
                Buzzer
```

## Applications

* College Notice Boards
* Event Information Systems
* Training Centers
* Smart Classrooms
* Industrial Announcements
* Public Information Displays

## Future Enhancements

* GSM-based remote message updates
* Bluetooth/Wi-Fi connectivity
* EEPROM storage for dynamic messages
* Mobile application integration
* Larger graphical display support

## Author

**Anil Kumar**

Embedded Systems Project using **LPC2148 ARM7 Microcontroller**

---

