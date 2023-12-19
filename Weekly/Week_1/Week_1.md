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

## Source

- Videos that I watched for setting-up raspberry:
    - [How to Enable SSH on a Raspberry Pi (and connect via IP)](https://www.youtube.com/watch?v=63yw7b0NuWc&t=319s&ab_channel=TonyTeachesTech)
    - [How to Access your Raspberry Pi via SSH over the Internet (port forwarding)](https://www.youtube.com/watch?v=ZKfnGqMrnug&ab_channel=TonyTeachesTech)
    - [How to Edit the Hosts File on Windows 10](https://www.youtube.com/watch?v=Htn3WojEdMI&t=158s&ab_channel=TonyTeachesTech)


## Research Stage

### Keywords

- AT commands
- LTE
- LTE Base HAT
- PCIe LTE Module
- baudrate
- parity

### Topics

- AT commands
- Python - Modem communication (libraries etc.)
- Port forwarding
- What's Webhook
- What's MQTT broker
- What's hivemq and hivemq topics
- Protocols
  - PPP Protocol
  - QMI/RMNET protocol
  - ECM protocol


### Research notes:

#### AT Commands

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
  - **AT**: This command is used to check communication between the module and the computer.
    - Returns "OK" or "ERROR"
  - **+CMGF**: This command is used to set the SMS mode. Either text or PDU mode can be selected by assigning 1 or 0 in the command.
    - AT+CMGF=`<mode>` (0: PDU mode, 1: text mode)
    - PDU: Protocol Data Unit
    - **PDU is more complex but allows more features**
  - **+CMGW**: This command is used to store message in the SIM.
    - AT+CMGW=”Phone number”> *Message to be stored* *(Ctrl+z)*
  - **+CMGS**: This command is used to send a SMS message to a number.
    - AT+CMGS= *serial number of message to be send.*
  - **ATD** : This command is used to dial or call a number.
    - ATD<`Phone number`>;*(Enter)*
  - **ATA**: This command is used to answer a call.
    - An incoming call is indicated by a message ‘RING’ which is repeated for every ring of the call.
    - When the call ends ‘NO CARRIER’ is displayed on the screen.
  -  **ATH**: This command is used to disconnect remote user link with the GSM module.

<br>

> [!NOTE]
> More detailed info can be found [here](https://www.engineersgarage.com/at-commands-gsm-at-command-set).

#### Sources
- [AT Commands, GSM AT command set](https://www.engineersgarage.com/at-commands-gsm-at-command-set/)
- [What are AT Commands?](https://www.cavliwireless.com/blog/nerdiest-of-things/an-introduction-to-cellular-at-commands.html)
- [Hayes AT command set](https://en.wikipedia.org/wiki/Hayes_AT_command_set)
- [Introduction to AT Commands](https://www.youtube.com/watch?v=g1nxe_J3DVI&t=765s&ab_channel=emnify)