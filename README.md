# Arduino Bluetooth Controlled Car  
## *Introduction*
The Project is a 2-wheel motor car which is controlled by an android application namely Bluetooth RC Controller and made using Arduino Uno. This car can move in all the directions can also give an amazing whirl.The car runs on a rechargeable power source also got some alluring well-rounded lights and a display to show charging percentage of the car. 
![car](https://user-images.githubusercontent.com/79688020/114798629-019f5e00-9d53-11eb-974f-8733bfa60182.jpg)
## *Motivation*
The aha moment was when we saw of our team member’s  brother playing games on thw smartphone and we wanted him to be more practical and give him a sense of connecting to the real world. So we came up with a real life application in which we though of connecting a self-made car with mobile phone and have fun with it.

## *Hardware requirements*
-	Arduino UNO
-	Power Bank
-	LED Strips
-	Motor shield
-	HC – 06 Bluetooth module
-	Robot chassis
-	Jumper Wires
	
## *Circuit* 
You have to be very careful while making all the connections and it can be very confusing, if you don’t know how to do. The
Instructions for each connection are as follow:
**Bluetooth:**
For Bluetooth we have to connect ***(VCC to 5V) , (GND to GND) , (TXD to RXD) , (RXD to TXD).***

**Battery:**
For battery we have to connect the positive terminal to of the battery to the (M+) terminal in separate two slots made for power. Further, we have to connect negative terminal to the (GND) terminal of the power supply.

**HC- SR04 (sensor):**
For sensor we have to connect ***(GND to GND) , (ECHO to A1 terminal) , (TRIG to A0 terminal) , (VCC to 5V).***

**MOTORS**:
For connecting the motors we have to connect the positive and negative terminal of the one motor to M3 terminal. Similarly we also have to connect the other motor positive and negative terminal of the other motor to M4 terminal.

NOTE: If you are making the 4 motor Bluetooth car then you also have to connect to the M1 and M2 terminal.
![image](https://user-images.githubusercontent.com/79688020/114804129-0584ad80-9d5e-11eb-8e6b-81c6b7704454.png)

## *Software requirements*
- Arduino IDE
- Bluetooth RC Controller (Android app)
- fritzing (Schematics)
#### Library
- AFMotor.h
## *Source Code*
#### HEADER
***AF Motor library  means adafruit motor library which gives us the flexibility of the code. This makes the code a lot more easier and important things that are
   included in the library are inbuilt functions like:
   run, forward, backward, set speed and others.
   This makes the code loosely coupled and gives flexibility over editing. We can set the particular wheels that are in operation and edit the code accordingly.***
*******************************************************************************************************************************************************************
***"F" for forward , "B" for backward, "R" for right, "L" for left and "s" for stop, after putting the command we can press send and it will obey the command.***
*******************************************************************************************************************************************************************
  ***So for manual reading we have chosen character "bt" it reads the instructions from the serial monitor.
     we choose 1KHZ (AF_DCMotor motor3(3,MOTOR34_1KHZ) because we are using a regular battery for power source but if we use wired power source then we can use 64kHZ
     The frequency only used  is 9600 and also for serial monitor it should be same. we faced this minor problem.
     Rest of the code is simple when connected with app then pressing the button gives the instructions to the serial monitor and then it obey the instructions. Each
     instruction for specific output.***

 ***Code Begins***
```
#include <AFMotor.h> // including the library


AF_DCMotor motor3(3, MOTOR34_1KHZ); // setting the frequency for the wheel 3

AF_DCMotor motor4(4, MOTOR34_1KHZ); // setting the frequency for the wheel 4

char bt = 'S'; // setting the character to the bt char datatype so that it donot move
void setup() // setup function declaration
{
  Serial.begin(9600);  // setting the frequency



  // setting the speed for both wheels
  motor3.setSpeed(255);
  motor4.setSpeed(255);
  Stop(); // stop function called
}


void loop() { // loop function initiation

  bt = Serial.read(); // bt starts reading the charcters from the serial monitor.

  if (bt == 'F') // checking the conditional statement that whether bt equals "F" to not
  {
    forward(); // forward fucntion called 
  }

  if (bt == 'B') // checking the conditional statement that whether bt equals "B" to not
  {
    backward(); //backward function called 
  }

  if (bt == 'L') // checking the conditional statement that whether bt equals "L" to not
  {
    left(); // left fucntion called 
  }

  if (bt == 'R') // checking the conditional statement that whether bt equals "R" to not
  {
    right(); // right function called 
  }

  if (bt == 'S') // checking the conditional statement that whether bt equals "S" to not
  {
    Stop(); // stop function called 
  }

}
void forward() // declaration of forward function 
{

  motor3.run(FORWARD); // object calls run function and passes the forward  as parameter 
  motor4.run(FORWARD);  // object calls run function and passes the forward  as parameter 
}

void backward()// declaration of backward function 
{

  motor3.run(BACKWARD); // object calls run function and passes the backward  as parameter 
  motor4.run(BACKWARD); // object calls run function and passes the backward  as parameter 
}
void right() // declaration of right  function 
{

  motor3.run(BACKWARD); // object calls run function and passes the backward  as parameter 
  motor4.run(FORWARD); // object calls run function and passes the forward  as parameter 
}
void left() // declaration of left function 
{

  motor3.run(FORWARD); // object calls run function and passes the forward  as parameter 
  motor4.run(BACKWARD); // object calls run function and passes the backward  as parameter 
}
void Stop() // declaration of stop function 
{

  motor3.run(RELEASE); // object calls run function and passes the release as parameter 
  motor4.run(RELEASE); // object calls run function and passes the release  as parameter 
}
```
## *Operating and Video*
-Upload the code on arduino, unplug from computer. 

-Connect bluetooth RC controller app on phone to HC-06.

-Once Connections are done play and have fun.

***Link to youtube video of our project***
https://youtu.be/RKsb_GMkkJw
## *Challenges*
-So whenever we play with electronics we go through a lot of mess, So our part started when we tried plugging in bluetooth we thought it was working fine but it took us     	moment to realise that its not working, So we order HC-06 new one. 

-Frequency setting should be same as the serial begin and the serial monitor bauds.

-We accidently wrote delay 500 which gave us trouble spinning wheel.

-So we had a real hard time to set the communication between bluetooth and arduino, later fixed by trying many times with serial monitor.

## *Team Roles*
*Being the part of the team we allotted different roles to each other depending on our capabilities.* 

•***Gurasis Singh***, Good writer has the responsibility of documentation. 

•***Noordeep Singh***, Good programmer has the responsibility to write code. 

•***Himanshu Sharma***, Good sense of electronics has the role to wire everything up

## ***Credits***
We got the project help from ***Mr.Vishal Soni***'s project.

*Refer to the link below for his work*

 https://www.hackster.io/vishal-soni/mobile-controlled-bluetooth-car-easy-simple-hc-05-59a002
#### ***Special Thanks***
***Alex Clarke***, *the man who played the master stroke as he helped us on the last day as we were stuck with an error.*

*The lit trio (**Levi,Payton,Justin**) of Lab instructors was amazing.*

*And yes finally **Dr.T**, name is enough. We had a beautiful semester with you.*
