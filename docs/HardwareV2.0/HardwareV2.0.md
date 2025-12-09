---
title: Hardware V2.0
tags:
- Myles White
- tag2
---

## Overview

If I were to create a version 2.0 of the speaker subsystem, several improvements would increase reliability and ease of debugging with added performancee. 

I would first improve the the power regulation stage because it was causing the most issues during testing due to heat build up, soldering sensitivity and difficukty verifying correct voltages on the PCB. In V2.0 I would switch to a 5V switching regulator because they run cooler, can handle higher heat from soldering and handing input voltage variation better. 
I would then add proper test points and debugging pads. Due to testing and troubleshooting it required external jumpers and quick modifications. Including more labeled test points on the schematic for: 

- 5V Output
- Groung
- Patner subsystem input (RB0) 
- Manual test button input (RB2)

I would then fix the routing around the manua test button due to the input behaing unexpectly and casued a short like behavior on the power supply. So a V2.0 would include a larger pull down resistor closer to RB2, wider spacing between the button pads and nearby traces, and a dedicates ground test point close to the switch to prevent current spikes that was seen during testing. 

Version 2.0 would also have wider power traces for better manufacturability because the inital PCB failed DFM checks because the annular rings were below the manufacturing limits. 

The connector alignement for the curiosity nano could be improved because the original header layout initially caused a unrealiable detection of the board. In V.2.0 I would use a single keyed connector or a alignment silkscreen 

With this improvements to manufacurability, debugging, and power delivery and stability. These changes directly address the issues encountered in testing and make the subsystem more robust and professional for the full system.
