---
title: Microcontroller Code
---

## Overview

This page documents the firmware used for the Speaker subsystem in the smart irrigation system project.
The microcontroller recieves a digital trigger signal from the Control subsystem and generates an audible beep through a Digital output that drives the speaker amplifier circuit 

## System Function 

- Input: Digital Trigger from partner board(RB0)
- Output: Digital tone on RC0 to speaker circuit
- Indicator: On board LED for Debugging
- Purpose: Provide audible feedback when system state changes. 

## Final Working Code 

#include "mcc_generated_files/system/system.h"
#include "stdio.h"

// 1 kHz beep
#define BEEP_CYCLES   200      // ~200 ms beep

static void beep_once(void)
{
    // Turn LED on while beeping
    IO_RF3_SetHigh();

    for (uint16_t i = 0; i < BEEP_CYCLES; i++)
    {
        IO_RC0_SetHigh();      // drive speaker circuit high
        __delay_us(500);       // 0.5 ms

        IO_RC0_SetLow();       // drive speaker circuit low
        __delay_us(500);       // 0.5 ms
    }

    // Turn LED off after beep
    IO_RF3_SetLow();
}

int main(void)
{
    SYSTEM_Initialize();

    // Make sure speaker output and LED start off
    IO_RC0_SetLow();
    IO_RF3_SetLow();

    // RB2 = your manual test button (active-low)
    // RB0 = digital signal from partner board (Speaker_Out)
    uint8_t last_btn_state     = IO_RB2_GetValue();  
    uint8_t last_partner_state = IO_RB0_GetValue();  

    while (1)
    {
        
        uint8_t btn_state     = IO_RB2_GetValue();   // manual test button
        uint8_t partner_state = IO_RB0_GetValue();   // from Raj

        //Local button: beep on press (1 -> 0, active-low)
        if ((last_btn_state == 1) && (btn_state == 0))
        {
            // button transitioned from released to pressed
            beep_once();
        }

        // Partner signal: beep on press event (1 -> 0) 
        if ((last_partner_state == 1) && (partner_state == 0))
        {
            // Speaker_Out line on Raj's side went from high to low
            // (BTN press or pot event, depending on his code)
            beep_once();
        }

        
        last_btn_state     = btn_state;
        last_partner_state = partner_state;
    }
}

The Code as a zip file is available [*here*](Microcontroller_code.zip)
