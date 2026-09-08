IoT Based Industrial Device Control and Automation System
1. Objective

The main objective of this project is to develop an IoT-based industrial device control and automation system using the LPC2129 ARM7 microcontroller and NodeMCU ESP8266 Wi-Fi module.

The system aims to:

    Control four electrical devices remotely through the Internet.
    Use the NodeMCU ESP8266 for Wi-Fi-based communication.
    Use the LPC2129 as the main controller for processing control commands.
    Control four electrical loads using a 4-channel relay module.
    Display the operating status of the system on a 16×2 LCD.
    Reduce manual intervention in industrial device operation.
    Provide a simple and low-cost solution for basic industrial automation.

2. Abstract

The IoT Based Industrial Device Control and Automation System is designed to provide remote control of electrical devices using the LPC2129 ARM7 microcontroller and NodeMCU ESP8266 Wi-Fi module. The NodeMCU ESP8266 provides wireless connectivity between the user and the control system, while the LPC2129 acts as the main processing and control unit.

Control commands received through the IoT interface are transmitted from the NodeMCU ESP8266 to the LPC2129 through UART communication. The LPC2129 processes the received commands and generates corresponding GPIO control signals. These signals are connected to a 4-channel relay module, which switches four electrical loads independently.

A 16×2 LCD is used to display the system information and the ON/OFF status of the controlled devices. The proposed system provides a convenient method for remotely controlling electrical equipment and can reduce manual intervention in industrial environments.

The system demonstrates the basic concept of Industrial Internet of Things (IIoT) by combining a microcontroller, Wi-Fi communication, relay-based device control, and local status display. The design can be further extended with sensors, cloud monitoring, scheduling, energy measurement, and automatic control.
3. Existing Problem

In conventional industrial systems, electrical devices are generally controlled manually through switches or centralized control panels. Such systems can become inconvenient when the equipment is located at a distance from the operator.

The major problems with conventional systems include:

  >  Requirement for manual operation.
  >  Difficulty in controlling devices from remote locations.
  >  Increased human intervention.
  >  Limited remote monitoring capability.
  >  Difficulty in monitoring the ON/OFF status of individual devices.
  >  Extensive wiring in conventional control systems.
  >  Limited flexibility for future expansion.
  >  Increased possibility of human error.
  >  Lack of Internet-based control and monitoring.

Therefore, an IoT-based system can provide a more convenient method of remotely controlling industrial electrical devices.
4. Proposed Method

The proposed system consists of three major control sections:

   > NodeMCU ESP8266 – provides Wi-Fi and IoT connectivity.
   > LPC2129 – processes the received commands and controls the devices.
   > 4-channel relay module – switches the four electrical loads.

The working sequence:
User
  ↓
IoT / Wi-Fi
  ↓
NodeMCU ESP8266
  ↓
UART Communication
  ↓
LPC2129
  ↓
GPIO
  ↓
4-Channel Relay
  ↓
Electrical Loads

The user sends a command through the IoT interface. The NodeMCU ESP8266 receives the command through Wi-Fi and sends the corresponding control data to the LPC2129 through UART.

The LPC2129 identifies the received command and controls the appropriate relay channel.

Command mapping
Command	  Device	Operation
1	      Bulb 1	ON
2	      Bulb 1	OFF
3	      Bulb 2	ON
4	      Bulb 2	OFF
5	      Bulb 3	ON
6	      Bulb 3	OFF
7	      Bulb 4	ON
8	      Bulb 4	OFF

In your program, the LPC2129 uses:
P0.3 → Relay Channel 1
P0.4 → Relay Channel 2
P0.5 → Relay Channel 3
P0.6 → Relay Channel 4

5. Hardware Components
5.1 LPC2129 Microcontroller

The LPC2129 is the main microcontroller used in the project. It is an ARM7-based microcontroller and performs the main control operations.

Its functions in this project are:

    Receiving commands from NodeMCU through UART.
    Processing the received commands.
    Controlling the four relay channels through GPIO.
    Interfacing with the LCD.
    Maintaining the device-control logic.

The LPC2129 acts as the central control unit.
5.2 NodeMCU ESP8266

The NodeMCU ESP8266 is used as the IoT and Wi-Fi communication module.

Its functions include:

    Connecting to a Wi-Fi network.
    Receiving commands from the user/application.
    Sending commands to the LPC2129.
    Providing Internet-based connectivity.
    Acting as the communication interface between the user and the LPC2129.

The NodeMCU does not directly perform the main relay-control logic in this design. Instead, it communicates the commands to the LPC2129 through UART.
5.3 4-Channel Relay Module

A 4-channel relay module is used to control four electrical loads.

The relay module provides an interface between the low-voltage microcontroller GPIO signals and the electrical loads.

The four channels are connected as:
LPC2129 P0.3 → Relay IN1 → Device 1
LPC2129 P0.4 → Relay IN2 → Device 2
LPC2129 P0.5 → Relay IN3 → Device 3
LPC2129 P0.6 → Relay IN4 → Device 4

The actual relay module should be appropriately rated for the voltage and current of the loads being controlled.
5.4 16×2 LCD

The LCD is used to display:

    Project title.
    System status.
    Device ON/OFF information.

For example:
IOT Based Module
Bulb 1 is ON

5.5 Power Supply

A regulated power supply provides the required operating voltage to the LPC2129, NodeMCU, LCD, and relay module.

The power supply must provide the correct voltage and sufficient current for each component.
5.6 Electrical Loads

Four bulbs are used as the demonstration loads in the project.

The same concept can be used for other suitable electrical devices such as fans, pumps, lights, and industrial equipment when appropriate switching/protection hardware is used.

6. Block Diagram
┌──────────┐
│   User   │
└────┬─────┘
     │
     ▼
┌────────────────┐
│ NodeMCU ESP8266│
│   Wi-Fi Module │
└──────┬─────────┘
       │ UART
       ▼
┌────────────────┐
│    LPC2129     │
│ Microcontroller│
└──────┬─────────┘
       │
       ▼
┌────────────────┐
│ 4-Channel Relay│
│     Module     │
└─┬────┬────┬────┬┘
  │    │    │    │
  ▼    ▼    ▼    ▼
 B1   B2   B3   B4

       │
       ▼
┌──────────────┐
│   16×2 LCD   │
└──────────────┘

7. Working Principle

The system works based on IoT communication followed by UART-based device control.
Step 1: Wi-Fi connection

The NodeMCU ESP8266 connects to the available Wi-Fi network.
Step 2: User command

The user sends a command through the IoT interface to control one of the four devices.

For example:
1 → Turn ON Bulb 1

Step 3: Command received by NodeMCU

The NodeMCU ESP8266 receives the command through the Wi-Fi/IoT connection.

Step 4: UART communication

The NodeMCU sends the command to the LPC2129 using UART communication.
NodeMCU ESP8266 ───── UART ─────► LPC2129

Step 5: Command processing

The LPC2129 receives the command using the UART receive function:
