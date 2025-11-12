# SASI 20-Pin, SASI 26-Pin, and SCSI 50-Pin Pinouts

## SASI 20-Pin Connector Pinout

**Connector Type**: 2x10 pin header (0.1" / 2.54mm pitch)
**Pin Numbering**:
```
  2  4  6  8 10 12 14 16 18 20
  1  3  5  7  9 11 13 15 17 19
```

### Pin Assignments

| Pin | Signal      | Direction | Description                    |
|-----|-------------|-----------|--------------------------------|
| 1   | -DB0        | I/O       | Data bit 0 (LSB)              |
| 2   | -DB1        | I/O       | Data bit 1                     |
| 3   | GND         | -         | Ground                         |
| 4   | -DB2        | I/O       | Data bit 2                     |
| 5   | -DB3        | I/O       | Data bit 3                     |
| 6   | -DB4        | I/O       | Data bit 4                     |
| 7   | GND         | -         | Ground                         |
| 8   | -DB5        | I/O       | Data bit 5                     |
| 9   | -DB6        | I/O       | Data bit 6                     |
| 10  | -DB7        | I/O       | Data bit 7 (MSB)              |
| 11  | GND         | -         | Ground                         |
| 12  | LED         | Output    | HDD Activity LED (not connected)|
| 13  | -BSY        | I/O       | Busy                           |
| 14  | -ACK        | I/O       | Acknowledge                    |
| 15  | -RST        | I/O       | Reset                          |
| 16  | -MSG        | I/O       | Message                        |
| 17  | -SEL        | I/O       | Select                         |
| 18  | -C/D        | I/O       | Control/Data                   |
| 19  | -REQ        | I/O       | Request                        |
| 20  | -I/O        | I/O       | Input/Output                   |

**Notes**:
- Pins 3, 7, 11 are Ground
- Pin 12 is HDD Activity LED signal - **NOT CONNECTED** in this adapter (requires separate handling)
- All signals are active-low (indicated by - or / prefix)
- Data bits DB0-DB7 form an 8-bit bidirectional data bus
- All control signals are present on this 20-pin connector

---

## SASI 26-Pin Connector Pinout

**Connector Type**: 26-pin IDC ribbon cable connector (2x13, 0.1" / 2.54mm pitch)
**Pin Numbering**:
```
  2  4  6  8 10 12 14 16 18 20 22 24 26
  1  3  5  7  9 11 13 15 17 19 21 23 25
```

### Pin Assignments

| Pin | Signal      | Direction | Description                    |
|-----|-------------|-----------|--------------------------------|
| 1   | -DB0        | I/O       | Data bit 0 (LSB)              |
| 2   | -DB1        | I/O       | Data bit 1                     |
| 3   | GND         | -         | Ground                         |
| 4   | -DB2        | I/O       | Data bit 2                     |
| 5   | -DB3        | I/O       | Data bit 3                     |
| 6   | -DB4        | I/O       | Data bit 4                     |
| 7   | GND         | -         | Ground                         |
| 8   | -DB5        | I/O       | Data bit 5                     |
| 9   | -DB6        | I/O       | Data bit 6                     |
| 10  | -DB7        | I/O       | Data bit 7 (MSB)              |
| 11  | GND         | -         | Ground                         |
| 12  | -DBP        | I/O       | Data parity bit                |
| 13  | TERMPWR     | Power     | Terminator power (+5V)         |
| 14  | -ATN        | I/O       | Attention                      |
| 15  | GND         | -         | Ground                         |
| 16  | LED         | Output    | HDD Activity LED (not connected)|
| 17  | -BSY        | I/O       | Busy                           |
| 18  | -ACK        | I/O       | Acknowledge                    |
| 19  | GND         | -         | Ground                         |
| 20  | -RST        | I/O       | Reset                          |
| 21  | -MSG        | I/O       | Message                        |
| 22  | -SEL        | I/O       | Select                         |
| 23  | GND         | -         | Ground                         |
| 24  | -C/D        | I/O       | Control/Data                   |
| 25  | -REQ        | I/O       | Request                        |
| 26  | -I/O        | I/O       | Input/Output                   |

**Notes**:
- Pins 3, 7, 11, 15, 19, 23 are Ground (alternating pattern)
- Pin 12 has parity signal (-DBP) which the 20-pin SASI lacks
- Pin 13 has TERMPWR (+5V for termination)
- Pin 14 has -ATN (Attention) signal which the 20-pin SASI lacks
- Pin 16 is HDD Activity LED signal - **NOT CONNECTED** in this adapter
- All signals are active-low (indicated by - prefix)
- This connector has all SCSI signals including parity and attention

---

## SCSI-1 50-Pin Connector Pinout

**Connector Type**: 50-pin IDC ribbon cable connector (2x25, 0.1" / 2.54mm pitch)
**Pin Numbering**:
```
  2  4  6  8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 42 44 46 48 50
  1  3  5  7  9 11 13 15 17 19 21 23 25 27 29 31 33 35 37 39 41 43 45 47 49
```

### Pin Assignments

| Pin | Signal      | Direction | Description                    |
|-----|-------------|-----------|--------------------------------|
| 1   | GND         | -         | Ground                         |
| 2   | -DB0        | I/O       | Data bit 0 (LSB)              |
| 3   | GND         | -         | Ground                         |
| 4   | -DB1        | I/O       | Data bit 1                     |
| 5   | GND         | -         | Ground                         |
| 6   | -DB2        | I/O       | Data bit 2                     |
| 7   | GND         | -         | Ground                         |
| 8   | -DB3        | I/O       | Data bit 3                     |
| 9   | GND         | -         | Ground                         |
| 10  | -DB4        | I/O       | Data bit 4                     |
| 11  | GND         | -         | Ground                         |
| 12  | -DB5        | I/O       | Data bit 5                     |
| 13  | GND         | -         | Ground                         |
| 14  | -DB6        | I/O       | Data bit 6                     |
| 15  | GND         | -         | Ground                         |
| 16  | -DB7        | I/O       | Data bit 7 (MSB)              |
| 17  | GND         | -         | Ground                         |
| 18  | -DBP        | I/O       | Data parity (separate connector)|
| 19  | GND         | -         | Ground                         |
| 20  | GND         | -         | Ground                         |
| 21  | GND         | -         | Ground                         |
| 22  | GND         | -         | Ground                         |
| 23  | GND         | -         | Ground                         |
| 24  | GND         | -         | Ground                         |
| 25  | Open        | -         | Not connected / Reserved       |
| 26  | TERMPWR     | Power     | Terminator power (+5V)         |
| 27  | Open        | -         | Not connected / Reserved       |
| 28  | GND         | -         | Ground                         |
| 29  | GND         | -         | Ground                         |
| 30  | GND         | -         | Ground                         |
| 31  | GND         | -         | Ground                         |
| 32  | -ATN        | Input     | Attention (not connected)      |
| 33  | GND         | -         | Ground                         |
| 34  | GND         | -         | Ground                         |
| 35  | GND         | -         | Ground                         |
| 36  | -BSY        | I/O       | Busy                           |
| 37  | GND         | -         | Ground                         |
| 38  | -ACK        | I/O       | Acknowledge                    |
| 39  | GND         | -         | Ground                         |
| 40  | -RST        | I/O       | Reset                          |
| 41  | GND         | -         | Ground                         |
| 42  | -MSG        | I/O       | Message                        |
| 43  | GND         | -         | Ground                         |
| 44  | -SEL        | I/O       | Select                         |
| 45  | GND         | -         | Ground                         |
| 46  | -C/D        | I/O       | Control/Data                   |
| 47  | GND         | -         | Ground                         |
| 48  | -REQ        | I/O       | Request                        |
| 49  | GND         | -         | Ground                         |
| 50  | -I/O        | I/O       | Input/Output                   |

**Notes**:
- All odd-numbered pins are Ground (except pin 25, 27 which are open)
- Even-numbered pins carry signals
- All signals are active-low (indicated by - prefix)
- TERMPWR (pin 26) provides +5V for termination resistors
- Pins 25 and 27 are reserved/not connected
- Pin 18 (-DBP) will be handled via **SEPARATE CONNECTOR** (to be added later)
- Pin 32 (-ATN) is **NOT CONNECTED** in this adapter (SASI does not have ATN signal)

---

## Signal Definitions

### Data Signals (DB0-DB7, DBP)
- **DB0-DB7**: 8-bit bidirectional data bus
- **DBP**: Data parity (odd parity, SCSI only)

### Control Signals
- **-BSY**: Busy - Asserted when bus is in use
- **-SEL**: Select - Used to select a target device
- **-C/D**: Control/Data - Indicates control or data phase
- **-I/O**: Input/Output - Indicates direction of data transfer
- **-MSG**: Message - Indicates message phase
- **-REQ**: Request - Data transfer request from target
- **-ACK**: Acknowledge - Data transfer acknowledge from initiator
- **-ATN**: Attention - Indicates initiator has message for target (SCSI only)
- **-RST**: Reset - Resets all devices on bus

### Power
- **TERMPWR**: Terminator power supply (+5V, typically 500mA-1A)

---

## Important Notes

1. **Signal Polarity**: All signals are active-low (logic 0 = asserted, logic 1 = deasserted)
2. **Ground Pattern**: Alternating signal-ground arrangement for noise immunity
3. **Voltage Levels**: TTL/LSTTL compatible (0V to +5V)
4. **SASI Variations**: This is one common SASI pinout. Different manufacturers may have used different configurations. Always verify with device documentation.
5. **Missing SASI Signals**: The 20-pin SASI connector shown here only includes data and BSY/SEL. Other control signals (REQ, MSG, C/D, I/O, ACK, RST) may be on additional pins or connectors depending on the implementation.

---

## Pinout Verification

Before connecting any hardware, verify pinouts using:
- Original device documentation
- Oscilloscope or logic analyzer
- Continuity testing with multimeter
- Examination of existing cables
