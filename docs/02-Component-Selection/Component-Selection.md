---
title: Individual -- Component Selection
---

## Major component selection

> Below are examples of what subcomponent options could fullfil the roles of the following components. 

*Table 1: Individual component selection (prox sensor)*

**Proximity Sensor**
> It needs to detect a nearby hand/body; analog output; works at 5 V; supports custom active conditioning.
1. TCRT5000 element (IR LED + phototransistor)

    ![](TCRT5000.jpg)

    * $1-2/each TCRT5000
    * [Link to PDV-P8103](https://www.digikey.com/en/products/detail/advanced-photonix/PDV-P8103/480610)

    | Pros                                      | Cons                                                             |
    | ----------------------------------------- | ---------------------------------------------------------------- |
    | True analog output                               | Needs mechanical aiming |
    | Easy to bias                      | Ambient light can effect performance                                        |
    | Inexpensive |

1. LDR (photoresistor PDV-P8103) + LED

    ![](PDV-8103.jpg)  ![](greenled.jpg)

    * $1/each PDV-P8103 [Link to PDV-P8103](https://www.digikey.com/en/products/detail/advanced-photonix/PDV-P8103/480610)
    * $0.08/ each for LED [Link to Green LED](https://www.digikey.com/en/products/detail/lumimax-optoelectronic-technology/LEDDC-5GRE/26680606) 

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | Robust people detection                                           | Slower     |
    | Stable over operating temperature                                 | Temperature/ambient drift |
    | Direct interface with PSoC (no external circuitry required) range | Requires more assembly

1. PIR Motion Sensor (LHI968)

    ![](LHI968.jpg)

    * $6/each LHI968
    * [Link to LHI968](https://www.digikey.com/en/products/detail/excelitas-technologies/LHI-968-3866/5885894)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | Outputs a square wave                                             | More expensive      |
    | Built-in amp/comparator                               | Gives digital output, no analog output |

**Choice:** Option 1: TCRT5000 element

**Rationale:** Analog current/voltage proportional to reflected light and pairs well with a custom MCP6002 gain + active low-pass filter stage to satisfy project requirements. The cost also makes this a viable option.

*Table 2: Individual component selection (Op-Amp)*
**Signal Conditioning Op-Amp**
> It needs a 5 V single supply, rail-to-rail I/O, low power, enough bandwidth for ~10–50 Hz.
1. MCP6002 (dual, 1 MHz GBW)

    ![](MCP6002.jpg)

    * $0.44/each
    * [Link to MCP6002](https://www.digikey.com/en/products/detail/microchip-technology/MCP6002-I-P/500875)

    | Pros                                        |     Cons                                                             |
    | ----------------------------------------- | ---------------------------------------------------------------- |
    | RRIO at 1.8–5.5 V                               | Not great for precision |
    | Ultra-low supply current                        | Low kHZ support                                           |
    | Good for low-frequency gain + Sallen-Key LPF    |

1. MCP6022 (dual, 10 MHz)

    ![](MCP6002.jpg)

    * $1.86/each
    * [Link to MCP6022](https://www.digikey.com/en/products/detail/microchip-technology/MCP6022-I-P/417828)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | More bandwidth                                                    | More expensive      |
    | 5 V single-supply                                                 | Higher current draw |
    |  |
    
1. TLV2462 (dual, ~6.4 MHz)

    ![](MCP6002.jpg)

    * $1.86/each
    * [Link to MCP6022](https://www.digikey.com/en/products/detail/microchip-technology/MCP6002-I-P/500875)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | RRIO                                                              | More expensive than MCP6002      |
    | 2.7–6 V supply                                                    | Higher current draw |
    |  |

**Choice:** Option 1: MCP6002

**Rationale:** Meets performance with minimal power and gives two amps for gain + active LPF, it is also the least expensive option.

### Style 2

> Also acceptable, more markdown friendly

**Low-Pass Filter**

1. 1st-order RC

    ![](image1.png)

    * $1/each
    * [link to product](http://www.digikey.com/product-detail/en/ECS-40.3-S-5PX-TR/XC1259TR-ND/827366)

    | Pros                                      | Cons                                                             |
    | ----------------------------------------- | ---------------------------------------------------------------- |
    | Minimal parts                               | Limited attenuation |
    | Easy to setup                               | More ripple vs. 2nd-order                                        |
    | Meets surface mount constraint of project |

1. 2nd-order Sallen–Key

    ![](image3.png)

    * $1/each
    * [Link to product](http://www.digikey.com/product-detail/en/636L3I001M84320/CTX936TR-ND/2292940)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | 40 dB/dec roll-off                                            | One more op-amp section      |
    | very smooth ADC input                                 | More components needed |
    |  |

1. Multiple-pole

    ![](image3.png)

    * $1/each
    * [Link to product](http://www.digikey.com/product-detail/en/636L3I001M84320/CTX936TR-ND/2292940)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | No extra op-amp needed                                             | Impedance rises      |
    | Stable over operating temperature                                 | ADC acquisition time needs care |
    |  |

**Choice:** Option 2: CTX936TR-ND surface mount oscillator

**Rationale:** A clock oscillator is easier to work with because it requires no external circuitry in order to interface with the PSoC. This is particularly important because we are not sure of the electrical characteristics of the PCB, which could affect the oscillation of a crystal. While the shipping speed is slow, according to the website if we order this week it will arrive within 3 weeks.
