# SENZ022 L298N双路电机驱动

###### 翻译

> `英文` 请参考 [`这里`](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/README.md)

> `中文` 请参考 [`这里`](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/README_CN.md)

![](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/pic/SENZ022.jpg "SENZ022")
 

### 产品介绍

> SENZ022 这个直流电机驱动模块是为了做ROBOT而开发的东东。当然，如果你有更好的想法，比如用于驱动步进电机也行。 我们做ROBOT的想法是：把大部分功能集成化，使得做机器人更加方便。 本模块采用LGS公司优秀大功率电机专用驱动芯片L298N，可直接驱动直流电机，驱动电流达2A。该电路线路布线合理、均采用贴元件片、体积小、方便安装，输出端采用高速肖特基二极管作为保护。


### 产品参数

- 逻辑部分输入电压VD：5 V
- 驱动部分输入电压VS：5～35V
- 逻辑部分工作电流Iss：≤36mA
- 驱动部分工作电流Io：≤2A
- 最大耗散功率：25W（T=75℃）
- 控制信号输入电平：
	- 高电平：2.3V ≤ Vin ≤ 5V
	- 低电平：-0.3V ≤ Vin ≤ 1.5V
- 工作温度：-20℃～＋130℃
- 驱动形式：双路大功率H桥驱动
- 模块尺寸：43 mm × 43mm

### 使用教程

#### 电机控制端口说明

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

#### 引脚定义

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


![](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/pic/SENZ022_pin.jpg "引脚定义") 


#### 连线图

![](https://github.com/njustcjj/SENZ022-L298N-Dual-Motor-Controller/blob/master/pic/SENZ022_connect.png "连线图") 


### 示例代码

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


### 购买[*SENZ022 L298N双路电机驱动*](https://www.ebay.com/).