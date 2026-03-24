# SDR-Based AoA Direction Finding for Drone RF Signals
This repository contains the GNU Radio Companion (GRC) flowgraphs and supporting files developed for a capstone project on Angle of Arrival (AoA) estimation for SDR-based drone direction finding.

The project investigates the use of Bartlett, MVDR, and MUSIC algorithms using a USRP B210 and GNU Radio.


**Prerequisites**

**Hardware**

•	USRP B210 

•	Two receive antennas 

•	Signal generator 

•	Horn antenna 

•	Computer with USB 3.0 

**Software**

•	Linux Ubuntu 22 or 24

•	GNU Radio 

•	UHD drivers 

•	Python 

•	gr-aoa 

•	Git 

**Software Setup**

Install the required tools before running the flowgraphs:
1.	Install GNU Radio using binary package
    sudo apt install gnuradio
3.	Install UHD drivers for the USRP B210
    Follow the Ettus Research installation guide for building and installing the USRP open-source toolchain on Linux:
  	https://kb.ettus.com/Building_and_Installing_the_USRP_Open-Source_Toolchain_(UHD_and_GNU_Radio)_on_Linux
4.	Install gr-aoa from https://github.com/MarcinWachowiak/gr-aoa
5.	Clone this repository

**Flowgraphs**
1. Bartlett and MVDR Flowgraph
Implements Bartlett and MVDR using:

    •   USRP Source 

    •	Stream to Vector 

    •	Embedded Python Block 

    •	QT GUI

2. MUSIC Flowgraph
Implements MUSIC using gr-aoa blocks:

    •	USRP Source 

    •	DC Blocker 

    •	Correlate 

    •	Root-MUSIC 

    •	MUSIC Linear Array 

    •	QT GUI

3. Combined Comparison Flowgraph

    •	Integrates the outputs of Bartlett, MVDR, and MUSIC for direct comparison.

**How to Run**

  1.	Connect the USRP B210 to the computer. 
  2.	Attach the receive antennas to the B210. 
  3.	Open GNU Radio Companion. 
  4.	Open one of the .grc files in the examples/ folder. 
  5.	Check the USRP Source settings: 
      center frequency 
      sample rate 
      receive gain 
  6.	Run the flowgraph. 
  7.	Observe the spectrum or AoA output on the QT GUI.

**Recommended Test Settings**

•	Center frequency: 2.4 GHz 

•	Sample rate: 1 MHz 

•	Alternative sample rate: 500 kHz if overflow occurs 

•	RX gain: 40 dB

**Notes**

•	The system was mainly tested under broadside, non-broadside, and endfire conditions. 

•	Broadside produced the most stable results. 

•	Endfire was found to be less stable and more ambiguous. 

•	The MUSIC flowgraph depends on the gr-aoa package. 

**Troubleshooting**

Overflow in GNU Radio:

Reduce the sample rate from 1 MHz to 500 kHz.

gr-aoa blocks missing:

Ensure gr-aoa has been installed and built correctly.

USRP not detected:

Check UHD installation and USB 3.0 connection.


**References**

Wachowiak, M. (n.d.). gr-aoa [Computer software]. GitHub. https://github.com/MarcinWachowiak/gr-aoa
