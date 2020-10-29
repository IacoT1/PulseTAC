![Logo](https://raw.githubusercontent.com/IacoT1/PulseTAC/master/Images/logo.jpg)
# PulseTAC
***Very flexible device to integrate the smart home with water, gas, electricity meters etc. which provide pulse outputs.***
<br><br>
<p align="center">
<img src="Photos/01a.jpg" width="350"> <img src="Photos/01b.jpg" width="350">
<img src="Photos/02a.jpg" width="350"> <img src="Photos/02b.jpg" width="350">
<img src="Photos/03a.jpg" width="350"> <img src="Photos/03b.jpg" width="350">
</p>
<br>
<p align="justify">
<b>PulseTAC</b> is used as a water meter but also as a gas and electricity meter and works with any external meter with pulse output. The acronym PulseTAC stands for <b>"Pulse Transporter And Counter"</b>.<br>
It has three simultaneous channels transmitted over very long distances using a network cable and the RS422/RS485 standards.<br>
It is composed of two very small (approx 4x4.5cm) junction boxes: the sender and the receiver/controller which integrates an ESP8266 connected to the WiFi for IoT applications.<br>
PulseTAC is very flexible and designed both for situations where the WiFi network reaches the meters or not.<br>
If the wifi signal in your home reaches the meters, you can connect the pulse output of the meters to the sender and keep the receiver/controller close with a short patch cable.<br>
If instead the wifi signal cannot reach the meter room, you can use a cable, even very long if necessary, and place the receiver/controller in another room or building where your wifi signal is present.<br>
The sender integrates three separate switch debouncers with ESD protected inputs. The power for the junction boxes can be supplied anywhere along the Ethernet cable or at the ends.<br>
The ESP8266 controller in the receiver/controller junction box can be equipped with Tasmota firmware for pulse counting and MQTT protocol support or with customized firmware. Using the Tasmota firmware (is recommended to use latest version 8.3.1), integration with home automation is very simple thanks to the MQTT protocol.<br>
The Tasmota configuration template for PulseTAC is the following:
</p>

```
{"NAME":"Smart Meters","GPIO":[0,0,0,0,0,0,0,0,43,44,42,0,0],"FLAG":15,"BASE":18}
```

<br><br>
<p align="center">
<img src="Images/wiring.jpg">
</p>
<br>
<b>Sender schematic</b><br>
<p align="center">
<img src="Images/Sender_Schematic.jpg">
</p>
<br>
<p align="center">
<img src="Images/Sender_PCB_top.jpg" width="400"> <img src="Images/Sender_PCB_bottom.jpg" width="400">
</p>
<br>

***Bill of materials of Sender board***

- U1: Maxim MAX6817EUT+T
- U2: Maxim MAX6816EUS+T
- U3, U4, U5: Renesas ISL3295EIHZ-T
- U6: CUI Inc. VXO7803-500-M
- R1, R2, R3: 1K 1/8W SMD 0805
- R4: 68 ohm 1/8W SMD 0805
- C1, C2, C3, C4, C5: Wurth 885012207098 0.1uF MLCC SMD 0805
- C6: Taiyo Yuden UMK316BBJ106KL-T 10uF MLCC SMD 1206
- C7, C8: TDK C2012X5R1A226K125AB 22uF MLCC SMD 0805
- L1: Pulse Electronics PA4321.333NLT
- J1: Cui Devices TB006-508-06BE 6 pin terminal block
- J2: Amphenol RJCSE-5085-01 RJ45 SMD connector
<br>

<b>Receiver/Controller schematic</b><br>
<p align="center">
<img src="Images/Controller_Schematic.jpg">
</p>
<br>
<p align="center">
<img src="Images/Controller_PCB_top.jpg" width="400"> <img src="Images/Controller_PCB_bottom.jpg" width="400">
</p>
<br>

***Bill of materials of Receiver/Controller board***

- U1, U2, U3: Renesas ISL3280EIHZ-T
- U4: ESP-03 1MB flash ESP8266 controller
- U6: CUI Inc. VXO7803-500-M
- R1, R2, R3: 100 ohm 1% 1/8W SMD 0805
- R4: 68 ohm 1/8W SMD 0805
- R5, R6, R7, R9: 10K 1/8W SMD 0805
- R8: 0 ohm solder joint
- R10: 0 ohm solder joint
- C1, C2, C3, C4: Wurth 885012207098 0.1uF MLCC SMD 0805
- C6: Taiyo Yuden UMK316BBJ106KL-T 10uF MLCC SMD 1206
- C7, C8: TDK C2012X5R1A226K125AB 22uF MLCC SMD 0805
- L1: Pulse Electronics PA4321.333NLT
- P1: 6 pins header 2.54mm
- J2: Amphenol RJCSE-5085-01 RJ45 SMD connector

***The 6 pins header P1 is used to connect an external FTDI programmer to flash the ESP8266 firmware. The pinout is:***

- 1: 3.3V
- 2: GPIO0 (connect to pin 3 with a jumper to enter flash mode)
- 3: GND
- 4: TXD
- 5: RXD
- 6: GND

***The GPIO assignment of the ESP8266 is:***

- GPIO14: Pulse Input 1 (counter1)
- GPIO12: Pulse Input 2 (counter2)
- GPIO13: Pulse Input 3 (counter3)

