<div>
<img src="https://img.shields.io/badge/MicroController%3A-Arduino%20UNO%203-green[700]" align="left">
<a href="https://www.tinkercad.com/things/1cJAQMVVZKf-motor-driver-controller"><img src="https://img.shields.io/badge/Simulation:-Click%20to%20Tinker-blue"></a>
<img src="https://img.shields.io/badge/Processor%3A-Atmega328P-black" align="right">
</div>

<div align="center">
    <h1>Motor Controlled Drivers</h1>
</div>

Electric motors consume almost half of the electricity produced worldwide. They, in fact, provide the necessary driving force for much of today’s equipment. Motors, pumps, and fans are present in an ever-wider range of products, from small consumer items to large industrial machines.

### What exactly is a Controller!? 🤔
- The control of the speed and direction of the motors presupposes the mode of operation of the motor in use and requires different techniques and circuits depending on the type of motor and the different application requirements.
- The purpose of a motor controller is to be able to act manually or automatically on the electric motor (start-stop, advance-inversion, speed, torsion, and protection against voltage overloads).

### Why exactly do we need Motor Control Driver? Is Arduino not sufficient? 🤔
- Arduino is very much capable of controlling a DC motor efficiently but the only issue here is that we don't know how much torque is needed by the area where this DC motor device is going to be deployed, hence we are bound to create an additional driver setup for motor in Arduino.