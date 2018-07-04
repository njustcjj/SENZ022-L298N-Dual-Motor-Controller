# SENZ022-L298N-Dual-Motor-Controller

###### Translation

> For `English`, please click [`here.`](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/README.md)

> For `Chinese`, please click [`here.`](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/README_CN.md)

![](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/pic/SENZ022.jpg "SENZ022")


### Introduction


> SENZ022 is a 5-35V, 2A Dual Motor Controller. It can bear larger current due to the increased haetsink dissipation. It is easy to control, using LGS's outstanding high-power motor driver chip, the L298N. This chip allows for direct drive of two bi-directional DC motors, and incorporates high-speed short diodes for protection. Drive current up to 2A per motor output. The driver uses a broad-brush design to reduce wire resistance.

### Specification

- The logic part of the input voltage: 5V
- Driven part of the input voltage Vs: 5 ~ 35V
- The logical part of the work current Iss: 36mA
- Drive part of the operating current Io: 2A
- Maximum power dissipation: 25W（T=75℃）
- Control signal input level:
	- High level: 2.3V ≤ Vin ≤ 5V
	- Low level:-0.3V ≤ Vin ≤ 1.5V
- Operating temperature: -20℃～＋130℃
- Drive Type: Dual high-power H-bridge driver
- Module Size: 43 mm × 43mm

### Tutorial

#### Motor  Control Pins 

|Motor|ENA|ENB|IN1|IN2|IN3|IN4|Description|
|-|:-:|:-:|:-:|:-:|:-:|-|
|MotorA|Low|-|High/Low|High/Low|-|-|Stop|
|MotorA|High|-|Low|Low|-|-|Stop|
|MotorA|High/PWM|-|Low|High|-|-|Back direction/ PWM speed regulation at back direction|
|MotorA|High/PWM|-|High|Low|-|-|Forward direction/ PWM speed regulation at forward direction|
|MotorA|High|-|High|High|-|-|Stop|
|MotorB|-|Low|-|-|High/Low|High/Low|Stop|
|MotorB|-|High|-|-|Low|Low|Stop|
|MotorB|-|High/PWM|-|-|Low|High|Back direction/ PWM speed regulation at back direction|
|MotorB|-|High/PWM|-|-|High|Low|Forward direction/ PWM speed regulation at forward direction|
|MotorB|-|High|-|-|High|High|Stop|

#### Pin Definition

|Sensor pin|Ardunio Pin|Function Description|
|-|:-:|-|
|VD|+ 5V|Drive the logical control part|
|VS|+5 ~ 35V||
|GND|GND||
|ENA|Digital 4||
|ENB|Digital 5||
|IN1|Digital 6||
|IN2|Digital 7||
|IN3|Digital 8||
|IN4|Digital 9||

> Note: When VS is powered with above 5V, and "EN 5V" is connected, then VD can be hung without input.

![](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/pic/SENZ022_pin.jpg "Pin Definition") 

#### Connecting Diagram

![](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/pic/SENZ022_connect.png "Connecting Diagram") 


#### Sample Code


	int ENA = 4;
	int ENB = 5;
	int IN1 = 6;
	int IN2 = 7;
	int IN3 = 8;
	int IN4 = 9;

	void setup() 
	{ 
	    pinMode(IN1, OUTPUT);   
	    pinMode(IN2, OUTPUT); 
		pinMode(IN3, OUTPUT);   
	    pinMode(IN4, OUTPUT); 
	} 

	void loop() 
	{ 
	  int value;
	  for(value = 0 ; value <= 255; value+=5) 
	  { 
	    digitalWrite(IN1,HIGH);   
	    digitalWrite(IN2,LOW);
	    digitalWrite(IN3,HIGH);   
	    digitalWrite(IN4,LOW);       
	    analogWrite(ENA, value);   //PWM Speed Control
	    analogWrite(ENB, value);   //PWM Speed Control
	    delay(30); 
	  }  
	}


### Purchasing [*SENZ022 L298N Dual Motor Controller*](https://www.ebay.com/).
