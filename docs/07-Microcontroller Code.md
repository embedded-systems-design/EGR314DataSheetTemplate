---
title: Microcontroller Code
tags:
- tag1
- tag2
---
Below is my final tested code that was used on my prototype of my audio sensor circuit. You may also download ithe MPLab code via the link [here](Audio_Sensor_203_MAC.X.zip)

~~~
#include "mcc_generated_files/system/system.h"
#include "mcc_generated_files/system/pins.h"
#include <stdio.h>
#include "mcc_generated_files/adc/adc.h"     // For ADC functions
#include "mcc_generated_files/dac/dac1.h"    // For DAC1 output control

// ============================
// Pin Logic Macros
// ============================

#define PTT_BUTTON      PORTBbits.RB7     // Active-LOW PTT button
#define VOICE_THRESHOLD 1800              // Mic sensitivity

int main(void)
{
    adc_result_t analog_in = 0;   // 10-bit ADC value (0?1023)
    uint8_t analog_out = 0;       // DAC output (0?31)

    SYSTEM_Initialize();
    UART1_Initialize();
    ADC_Initialize();

    // Force RB pins into correct modes
    TRISBbits.TRISB2 = 0;   // LED PTT (output)
    TRISBbits.TRISB3 = 0;   // LED voice detect (output)
    TRISBbits.TRISB4 = 0;   // Voice_OUT digital output
    TRISBbits.TRISB7 = 1;   // Button input

    ANSELBbits.ANSELB7 = 0; // RB7 digital-only

    // Start with LEDs off
    IO_RB2_SetLow();
    IO_RB3_SetLow();
    IO_RB4_SetLow();

    printf("System Initialized (No Interrupts)\r\n");

    // ============================
    // Main polling loop
    // ============================
    while (1)
    {
        printf("System Start");
        // ----- Read microphone ADC on RA0 -----
        ADC_ChannelSelect(ADC_CHANNEL_ANA0);
        ADC_ConversionStart();
        while (!ADC_IsConversionDone());
        analog_in = ADC_ConversionResultGet();
        
//    
        // ----- Scale for DAC output -----
        analog_out = (analog_in >> 4);        // 10-bit ? 5-bit conversion
        DAC1_SetOutput(analog_out);

        // ----- Read PTT button -----
        uint8_t button_state = PTT_BUTTON;    // 1 = pressed, 0 = not pressed

        // Print status for debugging
        printf("ADC=%u  Button=%u\r\n", analog_in, button_state);

        // ----- Button logic -----
        if (button_state == 1)  // pressed (active-high)
        {
            IO_RB2_SetHigh();   // PTT LED ON

            // Check voice threshold
            if (analog_in > VOICE_THRESHOLD)
            {
                IO_RB3_SetHigh();   // Voice LED ON
                IO_RB4_SetHigh();   // Voice OUT HIGH
            }
            else
            {
                IO_RB3_SetLow();  //PTT LED OFF
                IO_RB4_SetLow();  //Voice OUT OFF
            }
        }
        else
        {
            // Button not pressed ? everything off
            IO_RB2_SetLow();
            IO_RB3_SetLow();
            IO_RB4_SetLow();
        }

        __delay_ms(100);
    }

    return 0;
}

~~~