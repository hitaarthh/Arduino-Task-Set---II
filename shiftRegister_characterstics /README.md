<div>
<a href="https://www.arduino.cc/"><img src="https://img.shields.io/badge/MicroController%3A-Arduino%20UNO%203-green[700]"height="25" align="left"></a>
<a href="https://www.microchip.com/en-us/product/ATmega328P"><img src="https://img.shields.io/badge/Processor%3A-Atmega328P-black" height="25"align="right"></a>
</div>

<div align="center">
<h1> SISO, SIPO, PIPO Shift Registers </h1>

</div>

### ⚡️ Introduction: 
- Registers are sequential circuits made with flipflops to store and transfer binary information.
- Shift registers are primarily made with D flipflops in a daisy chain structure. These <a href="https://en.wikipedia.org/wiki/Flip-flop_(electronics)">flipflops</a> can each store one bit of binary information, all of which are controlled by a shared input clock. DFF's can read and store the value of the input signal at every rising edge of the clock. This property of the DFF can be used to build various registers. 
- Different forms of registers like SISO, SIPO, PISO, PIPO are differentiated by the way data is loaded and retrieved.

### --> SISO Shift Register: Serial In Serial Out Shift register
- SISO is one of the most basic forms of the shift registers. The data is loaded serially and retrieved serially. The output of the first DFF is fed into the input of the next DFF at each clock cycle, eventually reaching the last DFF / Output. This Shift register output is delayed from the input. The shift register shifts, or streams, one-bit data per clock cycle.

![image](https://support.dialog-semiconductor.com/documents/AN-CM-303/AN-CM-303_1.jpeg)

- As shown in the design above, DFF3 is fed with the input data bits serially and the output is taken from DFF10 serially. All the DFFs share the same clock. nReset is set high to ensure that all DFF's are enabled for normal operation.

- The timing diagram shown below has clock and input data stream as first and second waveforms. The rest of the waveforms show how the output of each DFF shifts serially. If we consider the first 8 input bits which are 10011010, we can clearly observe that these 8 bits appear one after another by the 8th rising edge clock at the output of DFF10

- One of the main applications of the SISO register is to act as a delay element. The delay can be controlled by the number of stages in the register and the frequency of the clock. In the design below the clock is at 1kHz, so the delay that is observed is 7 ms.

 <a href="https://www.tinkercad.com/things/ac5QUiI0cXO?sharecode=4eqq5bDAycv2kkFbsGoY9DTJIchsb8LClVbj3-nD-7E"><img src="https://img.shields.io/badge/SISO_CHARACTERTSTICS%3A-Click%20to%20Tinker-blue" height="25"></a>

<img width="1351" alt="Screenshot 2022-05-04 at 5 42 20 PM" src="https://user-images.githubusercontent.com/91147942/166678718-196b2d19-c761-4f14-9d2b-4d0c4a7709b7.png" >

### --> SIPO Shift Register:
    

