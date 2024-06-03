## 
**Analog modulation types**
amplitude, frequency, phase

## Digital Modulation
- Encoding a digital signal onto an analog wave
- Useful when transmitting over a medium that does not accept digital signals
- Known as *line coding*
- Three basic types: *amplitude, frequency, phase*
- Main goal: To be robust against noise, inteference and other impariments
**Advantages**
1. Makes better use of bandwidth
2. Requires less power to transmit
3. Performs better when the signal experiences interference
4. More compatible with error-correcting techniques
Have 2 formats
1. Uni Polar - Voltages are present on one side of time axis (only positive values)
2. Polar / Bipolar - Voltages are present on both sides of time axis, uses 2 voltage levels

**Types of Line Encoding**
1. Return to zero, *RZ* (uni polar)
2. Return to zero *RZ* (polar)
3. Non-return to zero *NRZ* (uni polar)
4. Polar non-return to zero *Polar NRZ* (polar)
> In return to zero, the transition to zero occurs before then end of the bit period (even if the next bit is not a zero)