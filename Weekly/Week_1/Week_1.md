# Week 1

## Week 1 Plan

- <u>[Setup Stage](#setup-stage)</u> ✔️
- Setting-up Raspberry Pi ✔️
- Setting-up SSH connections ✔️
- **Extra**: Port forwarding for SSH connection ✔️
- Hardware integrations ✔️

<br>

- <u>[Research Stage](#research-stage)</u>
- Researching keywords
- Researching hardware and utilities
- Researching implementations


> [!NOTE]
> I was going to start the `Setup Stage` in Week 2 but because I've already know how to setup raspberry and SSH connections, I just did it in `Research Stage` to reduce workload for Week 2.

## Setup Stage

Notes:

- I used **32-bit Raspberry pi for the OS** on my raspberry.
- I've added **custom host-name** to my computer hosts file so I don't have to remember IP address for next time.
- I've set **SSH port forwarding to my router** so I can use SSH connection over the Internet.
- Finished up hardware integrations using [docs](https://docs.sixfab.com/docs/raspberry-pi-4g-lte-cellular-modem-kit-getting-started).
- ***Extra:***
  - I've also installed and configured git, vim, and ohmyposh to set up my workspace

## Source

- Videos that I watched for setting-up raspberry:
    - [How to Enable SSH on a Raspberry Pi (and connect via IP)](https://www.youtube.com/watch?v=63yw7b0NuWc&t=319s&ab_channel=TonyTeachesTech)
    - [How to Access your Raspberry Pi via SSH over the Internet (port forwarding)](https://www.youtube.com/watch?v=ZKfnGqMrnug&ab_channel=TonyTeachesTech)
    - [How to Edit the Hosts File on Windows 10](https://www.youtube.com/watch?v=Htn3WojEdMI&t=158s&ab_channel=TonyTeachesTech)

<br><hr>

## Research Stage

### Keywords

- [AT commands](#at-commands) ✔️
- [LTE](#lte) ✔️
- [PCIe LTE Module](#pcie-lte-module) ✔️
- [Cellular Connectivity](#cellular-connectivity) ✔️
- [Baud](#baud) ✔️
- [Parity](#parity) ✔️
- [RAT Type](#rat-type) ✔️
- [APN](#apn) ✔️

### Topics

- [AT commands](#at-commands) ✔️
- Python - Modem communication (libraries etc.)
- Port forwarding
- What's Webhook
- What's MQTT broker
- What's hivemq and hivemq topics
- Protocols
  - PPP Protocol
  - QMI/RMNET protocol
  - ECM protocol
- Roaming on network
- Python `Serial` module

<br><hr>

## AT Commands

AT is the abbreviation for **Attention** and they are used to control MODEMs. The dial up and wireless MODEMs need AT commands to interact with a computer.

The Hayes subset commands are called the basic commands and the **commands specific to a GSM network are called extended AT commands**.

#### Types of AT Commands:
  - **Test**: Check whether a command is supported or not by the MODEM.
  - **Read**: Get mobile phone or MODEM settings for an operation.
  - **Set**: Modify mobile phone or MODEM settings for an operation.
  - **Execution**: Carry out an operation.

> [!TIP]
> AT command syntax: AT`<COMMAND>`+`<SUFFIX>`+`<DATA>` \
> *Suffixes*:
> - Test : `=?`
> - Read : `?`
> - Set : `=`
> - Execute : `None`

<br>

#### Common commands:
  - **AT**: Check communication between the module and the computer.
    - Returns "OK" or "ERROR"
  - **+CMGF**: Set the SMS mode. Either text or PDU mode can be selected by assigning 1 or 0 in the command.
    - AT+CMGF=`<mode>` (0: PDU mode, 1: text mode)
    - PDU: Protocol Data Unit
    - **PDU is more complex but allows more features**
  - **+CMGW**: Store message in the SIM.
    - AT+CMGW=”Phone number”> *Message to be stored* *(Ctrl+z)*
  - **+CMGS**: Send a SMS message to a number.
    - AT+CMGS= *serial number of message to be send.*
  - **ATD** : Dial or call a number.
    - ATD<`Phone number`>;*(Enter)*
  - **ATA**: Answer a call.
    - An incoming call is indicated by a message ‘RING’ which is repeated for every ring of the call.
    - When the call ends ‘NO CARRIER’ is displayed on the screen.
  -  **ATH**: Disconnect remote user link with the GSM module.

<br>

> [!NOTE]
> More detailed info can be found [here](https://www.engineersgarage.com/at-commands-gsm-at-command-set).

##### Sources
- [AT Commands, GSM AT command set](https://www.engineersgarage.com/at-commands-gsm-at-command-set/)
- [What are AT Commands?](https://www.cavliwireless.com/blog/nerdiest-of-things/an-introduction-to-cellular-at-commands.html)
- [Hayes AT command set](https://en.wikipedia.org/wiki/Hayes_AT_command_set)
- [Introduction to AT Commands](https://www.youtube.com/watch?v=g1nxe_J3DVI&t=765s&ab_channel=emnify)

<br><hr>

## LTE

- LTE stands for **“Long Term Evolution”**.
- High-speed **wireless data transmission standard** based on GSM/EDGE and UMTS/HSPA network technologies
- It improves on those standards' capacity and speed by using a **different radio interface and core network improvements**.

##### Sources

- [What is LTE: How It Works and Why It Matters](https://www.digi.com/blog/post/what-is-lte)
- [LTE (telecommunication)](https://en.wikipedia.org/wiki/LTE_(telecommunication))
- [LTE (Long-Term Evolution)](https://www.techtarget.com/searchmobilecomputing/definition/Long-Term-Evolution-LTE)
- [What is LTE, this Tutorial Explains LTE](https://www.youtube.com/watch?v=lNQcSgKVhSk&ab_channel=VoIPtutorial)

<br><hr>

## PCIe LTE Module

- The PCIe interface is a high-speed serial computer expansion **bus standard** that is used to connect various hardware devices, such as network cards, graphics cards, and storage controllers, to a computer's motherboard.
- PCIe LTE modules are typically **used to add cellular connectivity** to devices like laptops, desktop computers, and other embedded systems.

<br><hr>

## Cellular Connectivity

- Cellular connectivity refers to the **ability of a device to connect to a mobile network and communicate with other devices or services over that network**.
- It relies on cellular technology, such as GSM (Global System for Mobile Communications), CDMA (Code Division Multiple Access), or LTE (Long-Term Evolution), to establish a wireless connection between devices and a cellular network infrastructure.

**Key Components:**
- Mobile Networks
- SIM Cards
- Frequency Bands
- Protocols and Standarts
- Data Plans

<br><hr>

## Baud

- In telecommunication and electronics, baud (symbol: Bd) is a common unit of measurement of symbol rate, which is one of the components that determine the speed of communication over a data channel.
- *Symbols per second* or *pulses per second*

> [!IMPORTANT]
> Definition:
> - T<sub>s</sub> = 1 / f<sub>s</sub>
> - *Example*: **Communication at the baud rate 1000 Bd means** communication by means of sending 1000 symbols per second. In the case of a modem, this corresponds to 1000 tones per second. The symbol duration time is 1/1000 second (that is, 1 millisecond).

- You configure BaudRate as bits per second. The transferred bits include the **start bit**, **the data bits**, **the parity bit (if used)**, **and the stop bits**. However, only the data bits are stored.

> [!WARNING]
> Both the computer and the peripheral device must be configured to the same baud rate before you can successfully read or write data.


##### Sources

- [Baud (Wikipedia)](https://en.wikipedia.org/wiki/Baud)
- [BaudRate](http://www.ece.northwestern.edu/local-apps/matlabhelp/techdoc/matlab_external/baudrate.html)

<br><hr>

## Parity

- In computers, parity (from the Latin paritas, meaning equal or equivalent) **is a technique that checks whether data has been lost or written over when it is moved from one place in storage to another** or when it is transmitted between computers.
-  A parity bit adds **checksums** into data that enable the target device to determine whether the data was received correctly.

> [!TIP]
> You can configure Parity to be `none`, `odd`, `even`, `mark`, or `space`.


##### Sources

- [Parity (TechTarget)](https://www.techtarget.com/searchstorage/definition/parity)
- [Parity (northwestern.edu)](http://www.ece.northwestern.edu/local-apps/matlabhelp/techdoc/matlab_external/parity.html)

<br><hr>

## RAT Type

- The RAT (Radio Access Technology) type **represents the radio technology used by the mobile device**. This can be useful in determining what services or content can be sent to a specific mobile device.
- Many modern mobile phones support several RATs in one device such as **Bluetooth**, **Wi-Fi**, and **GSM**, **UMTS**, **LTE** or **5G NR**.

##### Sources

- [Radio Access Technology (Wikipedia)](https://en.wikipedia.org/wiki/Radio_access_technology)
- [Radio Access Technology (RAT) type](https://docs.fortinet.com/document/fortigate/7.4.1/fortios-carrier/265246/radio-access-technology-rat-type)

<br><hr>

## APN

- An Access Point Name (APN) is the **name of a [gateway](https://en.wikipedia.org/wiki/Gateway_(telecommunications)) between a mobile network (GSM, GPRS, 3G, 4G and 5G) and another computer network**, frequently the public Internet.
- APN identifies the [packet data network (PDN)](https://en.wikipedia.org/wiki/Packet_switching) that a mobile data user wants to communicate with.

##### Sources

- [Access Point Name (Wikipedia)](https://en.wikipedia.org/wiki/Access_Point_Name)
