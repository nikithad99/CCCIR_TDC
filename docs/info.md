<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

The circuit consists of a time-to-digital converter (TDC) integrated with a variable delay line. Its output corresponds to the TDC result, implemented using eight stages that generate eight discrete output bits. The primary function of this chip is limited to validating and characterizing the TDC architecture.

The TDC operates by employing flip-flops as time comparators in conjunction with a delay line that produces incrementally delayed replicas of the input start signal. The phase difference between the start and stop signals is measured by propagating the start signal through the delay line, while the stop signal acts as the clock input to the flip-flops. Each flip-flop output goes high if the corresponding delayed start signal arrives before the stop signal, and remains low if it arrives afterward. The number of high outputs therefore represents the measured phase difference, with a resolution defined by a single delay element.


## How to test

The chip features a single analog input, 14 digital inputs, and 8 digital outputs. To reset the TDC after a prior measurement, the start-enable signal should be driven low; following a brief delay, the stop input is driven high. For testing, the TDC can be evaluated by sweeping the digital input codes while applying a square-wave signal to the analog stop input.

The fine delay control is implemented using thermometer coding, whereas the coarse delay control employs one-hot encoding. In both schemes, an all-zero input code is considered a valid configuration.

## External hardware

External hardware components, including a Raspberry Pi (RPi) and a level shifter, are necessary to interface with and drive both the analog and digital inputs.
