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
4. Polar non-return to zero 
	1. Polar non-return to zero level *Polar NRZ-L*
	2. Polar non-return to zero level, invert-on-ones *Polar NRZ-I* 
> In return to zero types, the transition to zero occurs before then end of the bit period (even if the next bit is not a zero)
> In Polar NRZ-I, the transition is only done if the next bit is a 1.

[[Excalidraw/Drawing 2024-06-03 10.19.17.excalidraw.md#^bAJxZQO5JWRSrTrvhffjc|Return to zero uni polar]]

## Types of Digital to Analog Modulation
1. Digital-to-analog conversion -> Broken down into
2. Amplitude shift keying (ASK), Frequency shift keying (FSK), Phase shift keying (PSK) -> Can be combined into
3. Quadrature amplitude modulation (QAM)

> In ASK, signals are only shown when there is a 1.
> In FSK, frequency of the signal increases when there is a 1. If not, it goes back to the resting state
> 
> 

