## SamotPi2040 Board



Schematic:

![images/schematic.png](images/schematic.png)

PCB:

![images/pcb.png](images/pcb.png)

Image of PCB:

![3d_pcb](images\3d_pcb.png)

Rendered Image of PCB

![rendered_PCB.png](images/rendered_PCB.png)



### BOM

*or you can import [fastOrder_BOM.csv](fastOrder_BOM.csv**[)* file to [TME.eu](https://tme.eu)  

| Qty  | Value                       | Reference                                          | Footprint                                                  | Where(link)                                                  | Cost (USD)    |
| ---- | --------------------------- | -------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------ | ------------- |
| 2    | 1uF                         | C1, C10                                            | Capacitor_SMD:C_0402_1005Metric_Pad0.74x0.62mm_HandSolder  | [TME link](https://www.tme.eu/cz/details/grm155r61e105ma12d/kondenzatory-mlcc-smd/murata/) | 0.095         |
| 12   | 0.1uF                       | C2, C3, C4, C5, C6, C7, C8, C9, C11, C12, C17, C18 | Capacitor_SMD:C_0402_1005Metric_Pad0.74x0.62mm_HandSolder  | [TME link](https://www.tme.eu/cz/details/grm155r71c104ka88d/kondenzatory-mlcc-smd/murata/) | 0.17          |
| 2    | 10uF                        | C13, C14                                           | Capacitor_SMD:C_0603_1608Metric_Pad1.08x0.95mm_HandSolder  | [TME Link](https://www.tme.eu/cz/details/lmk107bj106maltd/kondenzatory-mlcc-smd/taiyo-yuden/lmk107-bj106maltd/) | 0.30          |
| 2    | 27pF                        | C15, C16                                           | Capacitor_SMD:C_0603_1608Metric_Pad1.08x0.95mm_HandSolder  | [TME link](https://www.tme.eu/cz/details/cc0603jrnpo9270/kondenzatory-mlcc-smd/yageo/cc0603jrnpo9bn270/) | 0.043 USD     |
| 1    | USB_C_Receptacle_USB2.0_16P | J1                                                 | Connector_USB:USB_C_Receptacle_GCT_USB4085                 | [Tme Link](https://www.tme.eu/cz/details/usb4085-gf-a/konektory-usb-a-ieee1394/gct/) | 1.05 USD      |
| 2    | Conn_01x20                  | J2, J3                                             | Connector_PinHeader_2.54mm:PinHeader_1x20_P2.54mm_Vertical | I have them                                                  | 0             |
| 1    | Conn_01x03                  | J4                                                 | Connector_PinHeader_2.54mm:PinHeader_1x03_P2.54mm_Vertical | I have it                                                    | 0             |
| 2    | 5.1K                        | R1, R2                                             | Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder   | [TME link](https://www.tme.eu/cz/details/wr06x5101ftl/rezistory-smd/walsin/) | 0.18 USD      |
| 2    | 27                          | R3, R4                                             | Resistor_SMD:R_0402_1005Metric_Pad0.72x0.64mm_HandSolder   | [TME Link](https://www.tme.eu/cz/details/erj2rkf27r0x/rezistory-smd/panasonic/) | 0.25          |
| 2    | 1k                          | R5, R6                                             | Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder   | [TME link](https://www.tme.eu/cz/details/crcw06031k00fkea/rezistory-smd/vishay/) | 0.015 USD     |
| 2    | 10k                         | R7, R9                                             | Resistor_SMD:R_0603_1608Metric_Pad0.98x0.95mm_HandSolder   | [TME Link](https://www.tme.eu/cz/details/rc0603jr-0710k/rezistory-smd/yageo/rc0603jr-0710kl/) | 0.085 USD     |
| 2    | SW_Push                     | SW1, SW2                                           | Button_Switch_SMD:SW_SPST_B3U-1000P-B                      | [TME Link](https://www.tme.eu/cz/details/b3u-1000pb/mikrospinace-tact/omron-electronic-components/b3u-1000p-b/) | 1.95 USD      |
| 1    | RP2040                      | U1                                                 | Package_DFN_QFN:QFN-56-1EP_7x7mm_P0.4mm_EP3.2x3.2mm        | [TME Link](https://www.tme.eu/cz/details/sc0914-7/raspberry-pi-vestavene-systemy/raspberry-pi/ic-rp2040-rp2b2-t-r-500-7-reel/) | 1.02 USD      |
| 1    | MCP1700x-330xxTT            | U2                                                 | Package_TO_SOT_SMD:SOT-23                                  | [TME link](https://www.tme.eu/cz/details/mcp1700t-3302e_tt/stabilizatory-napeti-neregulovane-ldo/microchip-technology/) | 0.65 USD      |
| 1    | MX25L6433FM2I-08G           | U3                                                 | Package_SO:SOIC-8_5.3x5.3mm_P1.27mm                        | [TME link](https://www.tme.eu/cz/details/mx25l6433fm2i-08g/pameti-flash-seriove/macronix-international/mx25l6433fm2i-08g-tube/) | 2.4 USD       |
| 1    | 12 MHz                      | Y1                                                 | Crystal:Crystal_SMD_3225-4Pin_3.2x2.5mm_HandSoldering      | [TME link](https://www.tme.eu/cz/details/abm8g-12.000mhz-18/resonators-and-generators/abracon/abm8g-12-000mhz-18-d2y-t/) | 0.39 USD      |
| 1    | PCB + CUSTOMS               | PCB + CUSTOMS                                      |                                                            | JLCPCB                                                       | 13.45         |
|      |                             |                                                    |                                                            | Shipping                                                     | 8.21 USD      |
|      |                             |                                                    |                                                            | **<u>TOTAL</u>**                                             | **16.81 USD** |



JLCPCB cart:

![jlcPcbcart.png](images/jlcPcbcart.png)

![jlcPcbcart2.png](images/jlcPcbcart2.png)