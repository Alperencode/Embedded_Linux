# Embedded Linux Team Internship - First Project

## Objectives
* Introduction to Embedded Linux systems.
* Working with Raspberry Pi.
* Using basic Linux commands.
* Writing readable, sustainable code in Python with an Object-Oriented Programming (OOP) approach.
* Using Git and Github.
* Project planning and management.
* Document creation.
* Preparing a Gantt chart.
* Learning basic information about cellular network modems. Sending and receiving data using basic protocols with a modem.

## Project Requirements
* A Python library will be developed to communicate with the modem, change its settings, send and receive data. The library should be able to send AT commands to communicate with the modem and process the responses.
  * Extra: Automatic detection of the modem's serial port.
  * Extra: Customization of serial port settings such as serial port, baudrate, parity, etc.
* An example code will be written that sends HTTP GET and POST requests to [webhook.site](http://webhook.site) via the modem. This code will use the library we developed earlier.
* An example code will be written that sends an MQTT message to a topic on the free and open MQTT broker [hivemq](https://www.hivemq.com/mqtt/public-mqtt-broker/) via the modem. Subscribing to the same topic will allow reading the message sent here again by the modem. This code will use the library we developed earlier.
* Establishing internet connectivity for Raspberry Pi through the modem.
  * Using PPP protocol.
  * Using QMI/RMNET protocol.
  * Using ECM protocol.
* The speeds of the connections established with these 3 protocols will be measured, and a general comparison of the protocols will be made.

## Action Plan
### Week 1
* Learning basic Git commands.
* Creating the Github repository for the project.
* Learning how to create documents with Markdown.
* Initial setup of Raspberry Pi 3B+, preparing the operating system, and learning basic bash commands.
* Project planning. The project is planned to be completed in a maximum of 6 weeks. Tasks to be done weekly for this 6-week period will be determined.
* Creating the Gantt chart. You should add this chart to the Github repository in a viewable format.
* Reporting.

### Week 2, 3, 4, 5, 6, 7
Completing the tasks weekly according to the project plan and reporting weekly.

## Tools to be Used
### Software Tools, Technologies, and Languages
* **Python:** To be used as the programming language.
* **Linux:** To be used as the operating system.
* **Bash:** To be used as the command-line interface on Linux.
* **Git/Github:** To be used for project management and tracking.
* **Markdown:** To be used for document creation, report preparation, etc.
* **Gantt Chart:** To be used for project management/timeline.

### Hardware
* [Raspberry Pi 3B+ Kit](https://sixfab.com/product/raspberry-pi-3-kit/)
  * Raspberry Pi 3B+
  * SD Card
  * SD Card Reader
  * 5V Adapter
* [Sixfab 4G/LTE Cellular Modem Kit](https://sixfab.com/product/raspberry-pi-4g-lte-modem-kit/)
  * Sixfab Base HAT
  * Quectel EG25-G Modem
  * Antennas
  * Sixfab SIM Card

## Reporting
* Weekly reports will be created under the `weekly` directory in the Github repository.
* Weekly reports should be in Markdown (.md) format.
* Weekly reports can be supported with visuals and tables.
* Citations should be added for information obtained in the research section of weekly reports.

## Weekly Team Meetings
* A team meeting will be held every week, limited to 1 hour.
* If there are demos or anything to be shown, they will be presented in the meeting. A general assessment of the situation will be made. The completed and upcoming tasks will be discussed. Unless there is a change, we can continue to hold these meetings every Thursday at 20:00.
