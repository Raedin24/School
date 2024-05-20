# Radio Frequency Communications
## Components of a Radio System
- Filter
- Mixer
- Amplifier
- Antenna
> Mixed signals are combined in such a way that the original signals can be extracted

### Filters
- Used to remove unwanted RF signals
- **RF Filter** - Passes or rejects signal based on frequency
- Used in transmitters to remove unwanted frequencies known as *harmonic oscillations*
> Harmonic oscillations result from the process of modulating the signal before transmission.
- **Intermediate frequency (IF)** signals are the output from the modulation process. Can be filtered using a bandpass filter.
#### Types of filters
1. **Low-pass filter** - Max frequency is set and all signals below that value is allowed
2. **High-pass filter** - Min frequency is set and all signals above that value is allowed
3. **Bandpass filter** - Sets a range called *passband*  and allows signals that fall within that range

> Signals can be decomposed into sin or cos waves using fourier transformations


#### Mixers
- Used to combine two radio frequency inputs to create a single output
- Resultant output is the range of the *highest sum* and *lowest difference* of the two frequencies
- Resultant maximum signal is the combination of the higher frequency signal + the message frequency. 
- *Sidebands* are created from this process (basically a spillover of the signal)
- *Dark bands* are left in between radio signals to prevent them from interfering with each other

#### Amplifier
- Used to increase the amplitude of an RF signal
- Is an active device
	- Must be supplied with electricity
	- Electricity is used to increase signal's intensity/strength
- RF signals lose intensity(amplitude) by travelling through circuits, space
- Formula to determine how much power remains after a certain distance
$$
P_{\gamma} \propto P_r \frac{l}{r^2}
$$

#### Antennas
- Used to transmit / receive an RF signal
- *Antenna reciprocity*  refers to how a single antenna can be used to both transmit and receive signals.

### Multiple Access
- Needed because only a limited number of frequencies are available for radio transmission
- Two types of access techniques
	1. Contention-based
	2. Contention-free
- Methods that allow multiple access
	- *Frequency Division Multiple Access* (*FDMA*) - Available bands are divided into slots for use by users, meaning there's a limit on how many can use it at one time. Used with *analog*  transmissions. Causes crosstalk/inteference
	- *Time Division Multiple Access* (*TDMA*) - Whole band is given to a user, but they're only allowed a short period
	- *Code Division Multiple Access* (*CDMA*) - Whole band is available for use at any time