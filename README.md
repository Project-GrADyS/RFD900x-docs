# RFD900x radios?

Status: Testing
Assign: Johan Marcos
Team: Field & testbed tasks

## Obs:

1. os RFD SiK radios precisam de uma certa distancia um do outro para poderem funcionar
2. O node Master no RFD pode ser usado também como node atuador.
3. Diferente do Sik Radio v1/v2, no firmware multipoint do RFD, o node master é o 1.
4. Segundo [logs](https://files.rfdesign.com.au/Files/firmware/RFD%20X%20modems%20SiK%20V2.X%20release%20notes.txt), [datasheet](https://files.rfdesign.com.au/Files/documents/RFD900%20DataSheet.pdf) e FAQ RFDesign, foi adicionada compatibilidade ao protocolo Mav2(Mavlink 2) ao RFD900x.
5. foi utilizado o firmware ***[RFD900x2-MultipointRelease_V3.00MP.gbl](https://files.rfdesign.com.au/Files/firmware/RFD900x2-MultipointRelease_V3.00MP.gbl)***
6. [Manual do RFD](https://files.rfdesign.com.au/Files/documents/RFD900x%20Multipoint%20User%20Manual%20V1.1.pdf) multipoint

[Modem Support FAQs V1.1 (1).pdf](RFD900x%20radios%2099d54dca739748468d48f41d4b6bb27b/Modem_Support_FAQs_V1.1_(1).pdf)

![PXL_20231230_010125302.NIGHT.jpg](RFD900x%20radios%2099d54dca739748468d48f41d4b6bb27b/PXL_20231230_010125302.NIGHT.jpg)

> Pixhawk com o NodeID 3, Rover com o NodeID 1(Master)
> 

![PXL_20231230_010136203.NIGHT.jpg](RFD900x%20radios%2099d54dca739748468d48f41d4b6bb27b/PXL_20231230_010136203.NIGHT.jpg)

> GCS com o NodeID 2
> 

![PXL_20231230_010350764.jpg](RFD900x%20radios%2099d54dca739748468d48f41d4b6bb27b/PXL_20231230_010350764.jpg)

> Conexão dos dois Veículos (Rover e Copter)
> 

## RFD config

| RFD |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Teste | Dia | Frequência | Airspeed | NodeCount | https://ardupilot.org/copter/docs/common-configuring-a-telemetry-radio-using-mission-planner.html | Duty Cicle | Serial Speed | Firmware | Situação |
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