# CAN-Bus-MultiNode-ADC-Network

This project demonstrates how to build a three-node communication system using the MCP2515 CAN controller and PIC16F877A microcontrollers. It uses the CAN bus to transmit analog data (via ADC) from **Node A** to **Node B** and **Node C**, where it is displayed on 16x2 LCDs.

---

## 📦 Project Overview

- **Node A**:
  - Reads analog voltage using the built-in 10-bit ADC.
  - Transmits the ADC value via CAN bus.
  - Displays the transmitted value on its own LCD.

- **Node B & Node C**:
  - Receive the ADC data sent from Node A over CAN.
  - Display the received value on their LCDs.

---

## 🔌 Hardware Used

- 3 × PIC16F877A Microcontrollers  
- 3 × MCP2515 CAN Modules (SPI based)  
- 3 × 16x2 LCD Displays  
- Potentiometer (for ADC input)  
- SPI Communication lines  
- External 16MHz Crystal + Capacitors  
- Breadboard or custom PCB  
- Power Supply (5V regulated)

---

## 🧠 Software Used

- MikroC PRO for PIC  
- MPLAB X (optional for simulation)  
- Proteus (for circuit simulation and testing)  
- Git (for version control)  

---

## 📁 Folder Structure

```bash
CAN-Bus-MultiNode-ADC-Network/
│
├── NodeA_ADC_Transmitter.c
├── NodeB_Receiver.c
├── NodeC_Receiver.c
├── README.md
├── LCD_CAN_Diagram.pdsprj         # Proteus project file (optional)
└── schematics/                    # Circuit images or Proteus design files


📡 Communication Details
CAN Baud Rate: Configured using CANSPIInitialize(1,3,3,3,1,...)

IDs Used:

Node A → ID: 12111

Node B → ID: 2

Node C → ID: 3

[Potentiometer]
      ↓
  [Node A]
(ADC Conversion)
      ↓
(CAN Transmit → ID: 12111)
      ↓              ↓
   [Node B]       [Node C]
 (CAN Receive)   (CAN Receive)
      ↓              ↓
  [Display LCD]  [Display LCD]
