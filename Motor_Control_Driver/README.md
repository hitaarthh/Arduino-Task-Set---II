<div>
<a href="https://www.arduino.cc/"><img src="https://img.shields.io/badge/MicroController%3A-Arduino%20UNO%203-green[700]"height="25" align="left"></a>
<a href="https://www.tinkercad.com/things/1cJAQMVVZKf?sharecode=2LWaF92oow0fe8p9A4l09VfqHvAKeLk3FCUbaxs3V1A"><img src="https://img.shields.io/badge/Simulation:-Click%20to%20Tinker-blue" height="25"></a>
<a href="https://www.microchip.com/en-us/product/ATmega328P"><img src="https://img.shields.io/badge/Processor%3A-Atmega328P-black" height="25"align="right"></a>
</div>

<div align="center">
    <h1>Motor Controlled Drivers</h1>
</div>

Electric motors consume almost half of the electricity produced worldwide. They, in fact, provide the necessary driving force for much of today’s equipment. Motors, pumps, and fans are present in an ever-wider range of products, from small consumer items to large industrial machines.

### --> Objective:
- To built a Motor Control Driver which can control the direction of rotation of the motor and as well as the RPM and torque of the given DC Motor.

### --> What exactly is a Controller!? 🤔
- The control of the speed and direction of the motors presupposes the mode of operation of the motor in use and requires different techniques and circuits depending on the type of motor and the different application requirements.
- The purpose of a motor controller is to be able to act manually or automatically on the electric motor (start-stop, advance-inversion, speed, torsion, and protection against voltage overloads).

### --> Why exactly do we need Motor Control Driver? Is Arduino not sufficient? 🤔
- Arduino is very much capable of controlling a DC motor efficiently but the only issue here is that we don't know how much torque is needed by the area where this DC motor device is going to be deployed, hence we are bound to create an additional driver setup for motor in Arduino.

### --> Devices Used:
- Arduino UNO3
- Breadboard small
- DC Motor
- <u><a href="https://electrosome.com/dc-motor-driving-using-h-bridge/#:~:text=H%20Bridge%20is%20a%20simple,in%20clockwise%20or%20anticlockwise%20directions.">H-bridge Motor Driver</a></u>
- 9V Battery(Optional)
- Connecting Wires

### --> Approach:
- The approach is to make a menu-driven program which can rotate the Motor in the direction on the basis of input in Serial monitor.

```C
if character ch=='a' which means it will rotate in antiClockwise.
```

```C
if character ch=='c' which means it will rotate in Clockwise.
```
### --> Simulation Diagram:
![image](https://user-images.githubusercontent.com/91147942/166149110-c672a2f9-2d7b-4533-851f-6e461717316e.png)

```C
/* This function intends to change the direction 
of the DC Motor*/
void direction()
{
    if(Serial.available())
    {
      ch = Serial.read();
      if(ch=='a')
      {
        Serial.print("Anti-Clockwise Spin Started!!");
        digitalWrite(6, HIGH);
        digitalWrite(7, LOW);
        speed(7,6);
      }
      else if(ch=='c')
      {
        Serial.print("Clockwise Spin Started!!");
        digitalWrite(6, LOW);  
        digitalWrite(7, HIGH);
        speed(6,7);
      }
      else if(ch=='s')
      {
        Serial.print("Motor has Spin Stopped!!");
        digitalWrite(6, LOW);  
        digitalWrite(7, LOW);
      }  
    }
}
```
- Now the approach is to render the Speed, RPM and torque of the given DC motor so, this could be done by calling a function of speed in the direction function which can render the speed in both clockwise and anticlocwise conditions.

```C
/* This function is intended to simply 
control the RPM and Torque for this particular motor*/
void speed(int x, int y) 
{
	  
     digitalWrite(x, LOW);
	 digitalWrite(y, HIGH);
    for (int i = 0; i < 256; i++) 
    {
		analogWrite(10, i);
		delay(20);
	}
	for (int i = 255; i >= 0; --i) 
    {
		analogWrite(10, i);
		delay(20);
	}
}
```
###  --> Complete Circuit Diagram:

![image](https://user-images.githubusercontent.com/91147942/166145340-be1d28fa-0ff0-4d9f-ad44-f4f336ddf2dd.png)

### --> Complete Source Code:


```C
char ch;
void setup()
{
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(10, OUTPUT);
  digitalWrite(10, HIGH);
  Serial.begin(9600);
}

void loop()
{
    direction();
}

/* This function intends to change the direction 
of the DC Motor*/
void direction()
{
    if(Serial.available())
    {
      ch = Serial.read();
      if(ch=='a')
      {
        Serial.print("Anti-Clockwise Spin Started!!");
        digitalWrite(6, HIGH);
        digitalWrite(7, LOW);
        speed(7,6);
      }
      else if(ch=='c')
      {
        Serial.print("Clockwise Spin Started!!");
        digitalWrite(6, LOW);  
        digitalWrite(7, HIGH);
        speed(6,7);
      }
      else if(ch=='s')
      {
        Serial.print("Motor has Spin Stopped!!");
        digitalWrite(6, LOW);  
        digitalWrite(7, LOW);
      }  
    }
}

/* This function is intends to simply 
control the RPM and Torque for this particular motor*/
void speed(int x, int y) 
{
	  
     digitalWrite(x, LOW);
	 digitalWrite(y, HIGH);
    for (int i = 0; i < 256; i++) 
    {
		analogWrite(10, i);
		delay(20);
	}
	for (int i = 255; i >= 0; --i) 
    {
		analogWrite(10, i);
		delay(20);
	}
}
```