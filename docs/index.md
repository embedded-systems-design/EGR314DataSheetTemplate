---
title: Welcome
tags:
- 
- 
---
<center>
<font size= "6">(Myles White) Datasheet</font><br>
as part of<br>
<font size= "8"> Smart Sprinkler System</font><br>
for<br>
<font size= "5"> Team 101 </font><br>

**Submission: 10, 31, 2025**
</center>

## Introduction

The purpose of this datasheet is to document the design process of my subsystem within the main project's system. My subsystem focus on the audio feedback module, which will provide a audio noice whenever the system detects a change in state, such as user input through the control hub. This documentation outlines the schematic design and ensures reliable intregration within the teams overall automated sprinkler system. 

### Project Summary

The Smart Sprinkler system is designed to automate water usage based off of real time soil moisture data. The System uses a Sensor Module, Control Hub, and a Audio output module. My subsystem connects to the control hub via a digital signal to the Hub microcontroller. When the poteniometer changes state or a button is press a PWM signal is sent to my board where its filtered and amplified through a Op amp and transistors This will drive a small buzzer to provide clear and immediate audio responses for user notifications.[team report.](https://egr304-2025-f-101.github.io/team101.github.io/)


### My Contribution

I independently built the speaker subsystem for team 101. My responsiblities were to develop the full KiCad Schematic integrating the micro controller, an voltage regulator, transistors, and a speaker. Adding Test points and fuse protection for troubleshooting. Ensuring compatibility between my module and the Hub. Creating a Powerr budget using a custom 5V regulator souced from a 9V 3A adapter. With this work I created a low power audio feedback solution that makes the entire System more interactive and easier to troubleshoot during operation. 

To review the details listed of the material used to construct the subsection, you can review it in the ["BOM"](https://mcwhit14.github.io/EGR304DataSheetTemplate/03-BOM/BOM/) section of the datasheet.

For all the sections
## Component Selection (Audio Subsystem)
- [Speaker & Voltage Regulator Options](https://mcwhit14.github.io/EGR304DataSheetTemplate/02-Component-Selection/Component-Selection/)

## Block Diagram (Audio Subsystem)
- [Block Diagram](https://mcwhit14.github.io/EGR304DataSheetTemplate/01-Block-Diagram/Block-Diagram/)

## Power Budget (Audio Subsystem)
- [Power Budget](https://mcwhit14.github.io/EGR304DataSheetTemplate/05-Power-Budget/Power-Budget/)

  ## Schematic (Audio Subsystem)
- [Schematic](https://mcwhit14.github.io/EGR304DataSheetTemplate/04-Schematic/schematic/)
