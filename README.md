# RFD900x DOCS

This project aims to test configurations for multipoint connections using RFD900x radios. RFD900x radios are communication devices that utilize radio frequency technology for data transmission. Multipoint connection enables multiple devices to communicate in a network, facilitating communication between different points in a distributed system. The [RFD900x Multipoint User Manual](https://files.rfdesign.com.au/Files/documents/RFD900x%20Multipoint%20User%20Manual%20V1.1.pdf) provides detailed information on how to configure and utilize this functionality, offering step-by-step guidance for successful implementation. Hardware information can be found in the [datasheet](https://files.rfdesign.com.au/Files/documents/RFD900x%20DataSheet%20V1.2.pdf).

## Requirements


1. RFD SiK radios need a certain distance from each other to work
2. The Master node in the RFD can also be used as an actuator node.
3. Unlike Sik Radio v1/v2, in the RFD multipoint firmware, the master node is 1 and can be used as an actuating node.
4. According to [logs](https://files.rfdesign.com.au/Files/firmware/RFD%20X%20modems%20SiK%20V2.X%20release%20notes.txt), [datasheet](https://files.rfdesign.com.au/Files/documents/RFD900%20DataSheet.pdf) e FAQ RFDesign, Mav2 (Mavlink 2) protocol compatibility has been added to the RFD900x.
5. Firmware was used ***[RFD900x2-MultipointRelease_V3.00MP.gbl](https://files.rfdesign.com.au/Files/firmware/RFD900x2-MultipointRelease_V3.00MP.gbl)***
6. [RFD Multipoint Manual](https://files.rfdesign.com.au/Files/documents/RFD900x%20Multipoint%20User%20Manual%20V1.1.pdf) multipoint
7. The parameters can be adjusted using [RFD tools](https://files.rfdesign.com.au/tools/) and/or AT commands.

[Modem Support FAQs V1.1 (1).pdf](RFD900x%20radios%2099d54dca739748468d48f41d4b6bb27b/Modem_Support_FAQs_V1.1_(1).pdf)

![PXL_20231230_010125302.NIGHT.jpg](RFD900x%20radios%2099d54dca739748468d48f41d4b6bb27b/PXL_20231230_010125302.NIGHT.jpg)

> Pixhawk with NodeID 3, Rover with NodeID 1(Master)
> 

![PXL_20231230_010136203.NIGHT.jpg](RFD900x%20radios%2099d54dca739748468d48f41d4b6bb27b/PXL_20231230_010136203.NIGHT.jpg)

> GCS with NodeID 2
> 

![PXL_20231230_010350764.jpg](RFD900x%20radios%2099d54dca739748468d48f41d4b6bb27b/PXL_20231230_010350764.jpg)

> Connection of the two Vehicles (Rover and Copter)
> 

## RFD config

| RFD |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Test | Day | frequency | Airspeed | NodeCount |TXPower | Duty Cicle | Serial Speed | Firmware | Status |
| Vôo 1 | 15/10 | 922000 - 928000 | 125 | 4 | 30 | 40:followed(NodeID3) - 40:repeater(NodeID1) - 10:follower(NodeID4) - 10:GS(NodeID2) | 115 | https://files.rfdesign.com.au/Files/firmware/RFD900x2-MultipointRelease_V3.00MP.gbl |  |

## In Mavproxy

![rfdMPMavProxy.png](RFD900x%20radios%2099d54dca739748468d48f41d4b6bb27b/rfdMPMavProxy.png)

## TEST | SYSID_THISMAV=23 RELEVANT PARAMS

| PARAM | TEST - SERIAL1(telem1) | 23 - SERIAL2(telem2) |
| --- | --- | --- |
| SERIAL2_BAUD | 115 | 115 |
| SERIAL2_PROTOCOL | 2 | 1 |

> obs: no divergent parameters relevant for serial communication with the RFD were found
>
