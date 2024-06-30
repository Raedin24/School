Radio waves were first known as *Hertzian Waves*. 
- Hertz showed that electromagnetic phenomena could be used to transfer energy between locations without a physical connection
- **Guglielmo Marconi** reproduced Hertz's experiment over greater distances
- Resulted in the first radio link (wireless telegraph)

# Mobile Systems
- Designed to operate over large areas with limited bandwidth
- Cellular mobile communication systems use large numbers of *low-power wireless transmitters*  to create cells
- Offers larger capacity through cell splitting.
- Cells can be sized according to subscriber density and demand by varying power levels
- Conversations are handed off to new cells as mobile users move from one region to another
- Channels / frequencies used in one cell can be reused in a cell in another region

# Communication Systems
- Used to distribute info from one location to another.
- Information is more conveniently shared as signals
- *Communication engineers*  are concerned with the transmission and reception of such signals
## Communication Process
1. Generation of message signal (*Voice*, *music, picture, etc* )
2. Description of message signal (*electrical, aural, visual*)
3. Coding of signal for transmission
4. Transmission
5. Decoding and reproduction of original signal
6. Recreation of original message signal
# Components of Communication System
1. Transmitter
2. Channel
3. Receiver
![[Pasted image 20240630200017.png]]
#### Modes of Transmission
1. Guided propagation 
    - Telephone
    - Coaxial cable
    - Optical fiber
2. Free propagation
    - Wireless broadcast channels
    - Radio channels
`Isotropic antennas transmit in all directions. Omnidirectional antennas transmit equally well in all directions.`
The coverage area of a transmitter is known as a **cell**. Cells are grouped into **clusters**

# Cellular System Infrastructure
- Early mobile systems used one powerful transmitter located at a high spot to cover areas, with radius of up to **50km**
- Cellular systems use a number of low power transmitters to cover a large area
![[Pasted image 20240630201805.png]]
1. **PSTN** - Public switch telephone network
2. **MSC** - Mobile switching centre
3. **BSC** - Base station controller
4. **MS** - Mobile station
5. **BS** - Base station

### Factors Influencing Performance of Wireless and Mobile Networking System
1. Density of MS in a cell
2. Distribution of speed and direction of MS
3. Frequency of calls
4. Number of simultaneous calls
5. Duration of calls
6. Position of MS w.r.t each other and BS
7. Type of traffic real-time and non-real-time
8. Traffic in adjacent cells and frequency of handoff
### Base Station
Base stations maintain 4 channels
- **FCC** - Forward (Downlink) control channel
- **RCC** - Reverse (Uplink) control channel
- **FTC** - Forward (Downlink) traffic channel
- **RTC** - Reverse (Uplink) traffic channel

## Components of a Cellular System
1. Mobile unit(phone)
2. Base station
3. Mobile switching center
**Generic Mobile Unit**
![[Pasted image 20240630202519.png]]**Generic Base Station**
![[Pasted image 20240630202604.png]]
# Modulation
- Process of transferring information signal to a high frequency carrier
## Importance
1. Allows transmission of large amount of info using a single carrier frequency
2. Increases the transmission length
3. Shorter aerial length
4. Security
5. Quality of service
6. Multiplexing

- Can be classified into
	- Continuous wave modulation (cw)
	- Pulse wave modulation
## Continuous Wave
- Can be classified depending on the parameter of the high frequency carrier that is modified
	1. Amplitude modulation
	2. Frequency modulation
	3. Phase modulation

## Pulse Wave
- Uses periodic sequence of rectangular pulses
- Can be either **analogue** or **digital**
- Analogue pulse modulation focuses on
	- Pulse amplitude
	- Pulse position
	- Pulse duration
`Standard form of digital pulse modulation is pulse code modulation`

---
- A *signal*  is a single valued function of time (value changes with time)
- Can be expressed as a function of *frequency*
- Consists of components of different frequencies
- Can be
	1. One-dimensional (*speech, music, computer data*)
	2. Two-dimensional (*pictures*)
	3. Three-dimensional (*video*)
	4. Four-dimensional (*volume data over time*)

## Channel Capacity (C)
- Defined as the **maximum rate** at which information can be transmitted through a channel
- The *fundamental theorem of information* theory says that at any rate below channel capacity, an error control code can be designed whose probability of error is arbitrarily small

- *Data rate*  is the number of bits transmitted per second. Indicates how fast a signal can be transmitted reliably over a given medium
- Affected by
	- Amount of energy put into signal transmission
	- Distance to be travelled
	- Noise
	- Channel bandwidth
- *Bandwidth of a media*  is the range of frequencies that can pass through that medium
- *Bandwidth of a signal*  is the range of frequencies the signal carries
`The b.w of the communication medium should be large enough to transmit the digital signal reliably. An inadequate b.w will distort the signal and introduce errors into the received signal.`
```
Data rate depends on the amount of data that the user is sending, thus a variable. Can increase, decrease and may become zero if the user is not sending. The bandwidth depends on the natural property of the media and thus, a fixed value
```
- *Noise*  is an unwanted signal which interferes with the original message signal and corrupts its parameters
- Likely to be introduces on the **channel** or the **receiver**
- *Error rate*  is a measure of the **degree of prediction error** of a model made with respect to the true model
- *Bit error rate*  is calculated by dividing the quantity of bits received in error by the total numbers of bits transmitted within the same period
- **Nyquist Bandwidth** (noise free)
$$
C = 2B\space log_2M
$$
- **Shannon Capacity**
$$
C = B\space log_2(1 + SNR)
$$
where:
C = channel capacity
B = bandwidth of channel (in Hz)
SNR = 10 log(signal power / noise power)  in dB

- Mathematical models of wireless comm systems can be divided into
	1. Deterministic
	2. Stochastic