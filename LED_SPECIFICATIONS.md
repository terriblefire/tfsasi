# SASI HDD Activity LED Signal Specifications

## Overview

Unfortunately, specific documentation for SASI LED signal levels is not readily available online. The SASI specification documents from Shugart Associates (late 1970s/early 1980s) are not accessible in readable form.

## Expected Characteristics (Based on Era-Appropriate Standards)

### Voltage Levels

SASI used **TTL/LSTTL logic levels** (5V signaling), so the LED signal was likely:
- **0V to 5V voltage range**
- Standard TTL output characteristics
- VOL (low-level output voltage) ≤ 0.4V
- VOH (high-level output voltage) ≥ 2.4V

### Most Likely Implementation

Based on typical HDD activity LED implementations from the late 1970s/early 1980s:

- **Open collector/open drain output** (active low)
- Signal pulls to ground (0V) when active
- Requires external pull-up resistor (typically to +5V through LED)
- Typical current drive capability: 10-20mA
- Could potentially handle up to 48mA (standard TTL sink current)

### Typical LED Driver Circuit

```
+5V ─┬─ [Current Limiting Resistor: 220-470Ω] ─┬─ LED+ (Anode)
     │                                           │
     │                                         LED
     │                                           │
     └─────────────────────────────────────── LED- (Cathode to Pin 12)
```

**Resistor calculation:**
- For 20mA LED current: R = (5V - LED_Vf) / 0.02A
- Red LED (Vf ~2V): R = (5V - 2V) / 0.02A = 150Ω (use 220Ω standard value)
- Green LED (Vf ~2.2V): R = (5V - 2.2V) / 0.02A = 140Ω (use 220Ω standard value)

### Alternative: Push-Pull Output

Some implementations may use **push-pull output**:
- Active high: +5V when drive is active
- Active low: 0V when drive is idle
- Can source and sink current

## Uncertainties

Without the actual SASI specification or specific drive/controller datasheets, the following cannot be confirmed:

- Exact voltage levels
- Maximum current capacity
- Whether output is open collector or push-pull
- Polarity (active high vs active low)
- Whether current limiting is built into the drive controller

## Verification Methods

If you have access to the actual vintage hardware, you can verify these specifications:

1. **Voltage measurement**: Use a multimeter to measure voltage on pin 12
   - Measure when drive is idle
   - Measure when drive is active (during read/write operations)

2. **Current capacity test**: Connect a test LED with series resistor
   - Start with 470Ω resistor for safety (~10mA)
   - Observe if LED illuminates during drive activity
   - If too dim, reduce resistor value incrementally

3. **Signal characteristics**: Use an oscilloscope to observe
   - Signal voltage levels
   - Active high vs active low polarity
   - Pulse width and frequency during activity

4. **Circuit topology**: Check with multimeter in diode/resistance mode
   - Measure resistance between pin 12 and ground
   - Measure resistance between pin 12 and +5V
   - This can indicate if it's open collector (pull-down only) or push-pull

## SASI Pin Assignments

### SASI 20-Pin
- **Pin 12**: LED / HDD Activity (NOT CONNECTED in current adapter)

### SASI 26-Pin
- **Pin 16**: LED / HDD Activity (NOT CONNECTED in current adapter)

## Recommendations

1. Design LED driver circuit that is compatible with both open collector and push-pull outputs
2. Include current limiting resistor in the adapter circuit (don't rely on drive's internal limiting)
3. Use standard 220-470Ω resistor for 5V operation with typical indicator LEDs
4. Consider using a buffer/driver IC if multiple LEDs need to be driven
5. Verify polarity and drive capability before connecting to final LED circuit

## References

- SCSI-1 electrical specifications (SASI's successor): VOL = 1.7V max at 55mA, VOH = 2.7V min
- TTL standard specifications: VOL ≤ 0.4V, VOH ≥ 2.4V
- SASI was the direct predecessor to SCSI-1 and used similar electrical characteristics
