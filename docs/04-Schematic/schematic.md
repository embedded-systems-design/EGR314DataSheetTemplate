---
title: Schematic
---

## Overview

This schematic is designed to comply with the Spark Guard's product requirements with time constraints, resorces, and my own abilities taken into consideration. Below are the schematics I have created for the purpose of completing the vision of our project. The device is powered from a 120V AC to 12V DC adapter, its internal components operate at 5V which is regulated via a 12VDC to 5VDC voltage regulator.




![schematicv1](MAC-Individual-Subsystem-Complex-Filters.jpg){style width:"350" height:"300;"}
**Figure 1:** Version 1 of my schematic.
In this schematic, I tried to leverage filters to capture a specific amplitude leveraging a Goertzel algorithm as a digital signal processor to measure the strenght of specific frequencies. This would have been excellent to capture high intensity voices such as a close whistle or a scree. Although for testing purposes, I decided to put this idea to the side for now until I understand its application with more detail.



![schematicv2](MAC-Individual-Subsystem-Simple-Test-Bed.jpg){style width:"350" height:"300;"}
**Figure 2:** Simplified schematic.
In this schematic, I utilized the same idea from a previous in class lab to send a clean analog signal from the microphone, after a high pass filter, to our Curiosity Nano PIC. It complies with our project requirement of having voice recognition to trigger a digital signal from my PIC to activate a solenoid and open the protective cover of the Spark Guard. This was mainly picked due to time constraints and to reduce development costs for the test bed product.



## Resouces

The schematic as a PDF download is available [*here*](MAC Individual Subsystems.pdf), and the Zip folder of the project schematics [*here*](MAC Individual Subsystem.zip).
Link to resourses of the DSP [Geoertzel algorithm](http://ww1.microchip.com/downloads/en/devicedoc/70332b.pdf).