---
title: Individual -- Component Selection
---

## Major component selection

> Below are examples of what subcomponent options could fullfil the roles of the following components. 

*Table 1: Individual component selection (prox sensor)*

**A-Proximity Sensor**
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
    | Built-in amp/comparator                                           | Gives digital output, no analog output |

    1. Analog Distance Sensor Sharp/Socle (GP2Y0A41SK0F)

    ![](LHI968.jpg)

    * $6/each LHI968
    * [Link to LHI968](https://www.digikey.com/en/products/detail/excelitas-technologies/LHI-968-3866/5885894)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | Good range for hand detection (4-30cm)                            | Most expensive option      |
    | Analog voltage readout                                            | Distance < 4 cm will provide throw away readings and will need to be addressed in design |
    |High resolution measurements|

**Choice:** Option 1: TCRT5000 element

**Rationale:** Analog current/voltage proportional to reflected light and pairs well with a custom MCP6002 gain + active low-pass filter stage to satisfy project requirements. The cost also makes this a viable option.

*Table 2: Individual component selection (Op-Amp)*
**B-Signal Conditioning Op-Amp**
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