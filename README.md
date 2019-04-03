# BMES Basic Arduino Workshop

*by Anson Fu for NTU Biomedical Engineering Society*

This workshop is based on ARDUINO IDE 1.8.5, ARDUINO UNO R3 Board and assumes zero knowledge of C Language.

***Disclaimer*** *-* *This document is only meant to serve as a reference for the attendees of the workshop. It does not cover all the concepts or implementation details discussed during the actual workshop.*

<hr>

### Workshop Details:

**When?**: Satauday, 12 May 2018. 9:00 AM - 1:00 PM.</br>
**Where?**: TR +27, The Hive, Nanyang Technological University</br>
**Who?**: NTU Biomedical Engineering Society

<hr>

## Step 0 - Initial Setup

1. Download [ARDUINO IDE](https://www.arduino.cc/en/Main/Software).
2. Pair up as a team.
3. Make sure your team has one Arduino UNO board with USB cable and solderless breadboard.
4. Turn on Arduino IDE.

<hr>

## Step 1 - Introduction of Arduino

### 1.1 What is Arduino? Why Arduino?
Arduino is an open-source electronics platform based on easy-to-use hardware and software. Arduino boards are able to read inputs and turn it into an output. </br>
Arduino boards are relatively inexpensive compared to other microcontroller platforms. The Arduino Software (IDE) is easy-to-use for beginners, yet flexible enough for advanced users to take advantage of as well.

### 1.2 Arduino integrated development environment (IDE)
In this workshop, we will be using the Arduino IDE to write code to program the Arduino board.
The Arduino IDE is a cross-platform application provides a text editor with the typical IDE
features like syntax highlighting, a compiler to compile and upload code to the board. </br>
A program written with the Arduino IDE is called a sketch. Sketches are saved on the
development computer as text files with the file extension ".ino". The Arduino IDE utilises C++
as its programming language and contains various libraries catered to the Arduino.</br>
![sketch image](image/sketch.JPG)

### 1.3 The Arduino Board (UNO)
![Arduino_Board](image/Labellings/ArduinoBoard.png)
![Arduino_Board Labellings](image/Labellings/ArduinoBoardLabellings.PNG)

<hr>

## Step 2 - Electronic Prototyping

### 2.1 Electronic Components
#### 1. Diodes: Current passing through a diode can only go in one direction, called the forward direction. Current trying to flow the reverse direction is blocked. Diodes have polarity, so take note of the polarity when connecting them up. </br>E.g. Light Emitting Diode(LED): 
![LED](image/Diode.png)</br>
#### 2. Resistors : To reduce current flow, adjust signal levels and to divide voltages.</br>
![resistor](image/Resistor.png)</br>
#### 3. Solderless Breadboard : is a construction base for prototyping of electronics.</br>
![bread](image/Breadboard.png)</br>

### 2.2 Electronic Concepts

Logic Levels: A logic level is a specific voltage or a state in which a signal can exist. A digital
circuit can have two states: ON or OFF. In binary, ON means 1 and OFF means 0. In Arduino,
we call these signals HIGH or LOW, respectively.
</br>
![LL](image/LogicLevel.PNG)

### 2.3 Electrical Concepts
![OhmLaw](image/OhmLaw.jpg)

### Task 1 Set up LED
![LEDschematic](image/Breadboard/LEDschematic.jpg)
![LED](image/Breadboard/LED.jpg)

## Step 3 - Introduction to C++ Programming

### 3.1 Anatomy of a Sketch
There are two functions that have to be in every sketch. They are **Setup()** and **Loop()**. The
setup() function is called when a sketch starts. It is used to initialize the variables, pin modes,
start using libraries. The setup function will only run once, after each power up or reset of the
Arduino board. The loop() function loops consecutively, allowing your program to change and
respond. It is used to actively control the Arduino board.

### 3.2 Variables
#### 3.2.1 Variables and constants: 
A variable is a way of naming and storing a value for later use by the program, such as
data from a sensor or an intermediate value used in a calculation.
#### 3.2.2 Variable Scope:
Another important choice that programmers face is where to declare variables. The
specific place that variables are declared influences how various functions in a program
will see the variable. This is called variable scope.
#### 3.2.3 Initializing Variables:
Variables may be initialized (assigned a starting value) when they are declared or not. It
is always good programming practice however to double check that a variable has valid
data in it, before it is accessed for some other purpose.
#### 3.2.4 Using Variables:
Once variables have been declared, they are used by setting the variable equal to the
value one wishes to store with the assignment operator (single equal sign). The
assignment operator tells the program to put whatever is on the right side of the equal
sign into the variable on the left side.

### 3.3 Variable Data Types
* **void**: The void keyword is used only in function declarations. It indicates that the
function is expected to return no information to the function from which it was called.
* **boolean**: A Boolean holds one of two values, true or false. Each Boolean variable occupies
one byte of memory.
* **char**: A data type that takes up one byte of memory that stores a character value.
Character literals are written in single quotes like this: 'A'. For multiple characters, strings
use double quotes: "ABC".
* **byte**: A byte stores an 8-bit unsigned number, from 0 to 255.
* **int**: int stores a 16-bit (2-byte) value. This yields a range of -32,768 to 32,767.
* **unsigned int**: unsigned ints (unsigned integers) are the same as ints in that they store
a 2 byte value. Instead of storing negative numbers, they only store positive values, yielding
a useful range of 0 to 65,535.
* **long**: long variables are extended size variables for number storage, and store 32 bits (4
bytes), from -2,147,483,648 to 2,147,483,647.
* **unsigned long**: Unsigned long variables are extended size variables for number
storage, and store 32 bits (4 bytes). Unlike standard longs unsigned longs won't store
negative numbers, making their range from 0 to 4,294,967,295.
* **float**: Floating-point numbers are numbers that have a decimal point. Floating-point
numbers are often used to approximate analog and continuous values because they have
greater resolution than integers. Floating-point numbers can be as large as 3.4028235E+38
and as low as -3.4028235E+38. They are stored as 32 bits (4 bytes) of information.
* **double**: Double precision floating point number. On the Uno, this occupies 4 bytes. That is,
the double implementation is exactly the same as the float, with no gain in precision.
* **string**: Text strings can be represented in two ways. you can use the String data type,
which is part of the core as of version 0019, or you can make a string out of an array of
type char and null-terminate it.

### 3.4 Strings/Char Arrays
Special attention is brought to strings because in C++, strings are actually character arrays. </br>
```C++
void setup(){
  Serial.begin(9600);
  char Str1[7] = {'a', 'r', 'd', 'u', 'i', 'n', 'o'};
  char Str2[7] = "arduino";
  Serial.println(Str1);
}
```
### 3.5 C++ comments
Comments are lines in the program that are used to inform yourself or others about the way
the program works. They are ignored by the compiler, and not exported to the processor, so
they don't take up any space on the chip. Comments only purpose are to help you understand
(or remember) how your program works or to inform others how your program works. There
are two different ways of marking a line as a comment:
</br>● Single line comment: Denoted by “//”.
</br>● Multi-line comment: Denoted by “/* ” and “ */”.

### 3.6 C++ Operators
![AO](image/Operators/ArithmetricOperator.PNG)
![CO](image/Operators/ComparisonOperator.PNG)
![LO](image/Operators/LogicalOperator.PNG)
![BO](image/Operators/BitwiseOperator.PNG)
![CdO](image/Operators/CompoundOperator.PNG)

### 3.7 Functions
For controlling the Arduino board and performing computations. Segmenting code into functions allows a programmer to create modular pieces of code that perform a defined task and then return to the area of code from which the function was "called". Functions help the programmer stay organized.</br>
#### 3.7.1 Fuction Example </br>
```C++
void setup(){
  Serial.begin(9600);
  Serial.println(myFunc(1,2));
  Serial.println(myFunc(3,4));
}
void loop(){
}
  int myFunc(int a,int b){
  int c = a + b;
  return c;
}
```
#### 3.7.2 Long way without function </br>
```C++
void setup(){
  Serial.begin(9600);
  int a = 1;
  int b = 2;
  int c = a + b;
  Serial.println(c);
  a=3;
  b=4;
  c = a + b;
  Serial.println(c);
}
void loop(){
}
```
### Task 2 LED Blink
```C++
const int LEDpin = ...;   // the digital pin the LED is attached to

// the setup routine runs once when you press reset:
void setup() {
  // declare LEDpin to be an output:
  pinMode(...);
}

// the loop routine runs over and over again forever:
void loop() {
  digitalWrite(...);    // turn the LED on (HIGH is the voltage level)
  delay(...);           // wait for a second
  digitalWrite(...);    // turn the LED off by making the voltage LOW
  delay(...);           // wait for a second
}
```

### 3.8 Control Structures
We will use the LED Blink code above to introduce you different types of control structures.
</br>
#### 3.8.1 if statement example
```C++
const int LEDpin = ...;
int delayPeriod = 500;   //set the initial value for 'delayPeriod' as 500, 0.5second

void setup() {
  pinMode(...);
}

void loop() {
  digitalWrite(...);
  delay(...);
  digitalWrite(...);
  delay(...);
  delayPeriod = delayPeriod + 100;    // increase the delay timing by 0.1 second through the loop:
  if (delayPeriod > ...)    //Check the condition of 'if statement', if True, run 'if statement', if False, return.
  {
    delay(...);
    delayPeriod = 500;   //reset the value of delayPeriod
  }
}
```
#### 3.8.2 if-else statement example
```C++
const int LEDpin = ...;
int delayPeriod = 500;
int i = 0;    //set a condition variable 'i' as 0

void setup() {
  pinMode(...);
}

void loop() {
  
  if (i < ...){
    digitalWrite(...);
    delay(...);
    digitalWrite(...);
    delay(...);
    ...;
  }
  else{         //run 'else statement' when 'if statement' is False
    delay(...);
    i=...;
  }
}
```
#### 3.8.3 for loop example
```C++
const int LEDpin = ...;
int delayPeriod = 500;

void setup() {
  pinMode(...);
}

void loop() {
  
  for (int ... ; ... ; ...) { //delare variable; loop & check condition ; action for each loop
    digitalWrite(...);
    delay(...);
    digitalWrite(...);
    delay(...);
  }
    ...
}
```

## Step 4 Activities
### 4.1 Activity 1: LED Fade
In this activity, we will use Pulse Width Modulation, or PWM, to control the brightness of the
LED. By varying the brightness of the LED continuously, a fading effect can be created.
```C++
const int LEDpin = ...;

void setup() {
  pinMode(...);
  }

void loop() {
  for (int ...){
  analogWrite(...);  //conditions: i as brightness,  maximum brightness is 255
  delay(5);
  }
  for (...){
  analogWrite(...);
  delay(5);
  }
}
```
#### Alternatively
```C++
int LEDpin = ...;           
int brightness = 0;     // how bright the LED is
int fadeAmount = 5;    // how many points to fade the LED by

void setup() {
  pinMode(...);
}

void loop() {
  analogWrite(...);

  // change the brightness for next time through the loop:
  brightness = brightness + fadeAmount;

  // reverse the direction of the fading at the ends of the fade:
  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
  // wait for 30 milliseconds to see the dimming effect
  delay(30);
}
```

### 4.2 Activity 2: Press and hold to turn on LED
In this activity, the pushbutton is used to turn the LED on when the button is pressed. How this
works is the Arduino reads the input on one pin, then changes the output on another pin to turn
the LED on or off.
![switch](image/Breadboard/Switchbreadboard.jpg)
```C++
const int buttonPin = 2;     // the number of the pushbutton pin
const int LEDPin =  13;      // the number of the LED pin
 
// variables will change:
int buttonState = LOW;         // variable for reading the pushbutton status
 
void setup() {
  // initialize the LED pin as an output:
  pinMode(...);
  // initialize the pushbutton pin as an input:
  pinMode(...);
}
 
void loop() {
  // read the state of the pushbutton value:
  buttonState = digitalRead(buttonPin);
 
  // check if the pushbutton is pressed.
  // if it is, the buttonState is HIGH:
  if (...) {
    // turn LED on:
    digitalWrite(...);
  } else {
    // turn LED off:
    digitalWrite(...);
  }
}
```

### 4.3 Activity 3: Press to turn on LED, press to turn off LED
This activity demonstrates how to change the state of a pin based on input from another. Also,
the concept of button debouncing is introduced. 
```C++
int buttonPin = 2;
int LEDPin = 13;
int LEDstate = LOW;
int buttonState;
long time = 0;
long debounce = 200; //checking twice in a short period  of time(200) to make sure the pushbutton is definitely pressed 

void setup() {
  pinMode(buttonPin, INPUT);
  pinMode(LEDPin, OUTPUT);
}
void loop() {
  buttonState = digitalRead(buttonPin);
  if(buttonState == HIGH && millis() - time > debounce) { /*millis() function to keep track of the time passed since the button was pressed*/
    if(LEDstate == HIGH){
    LEDstate = LOW;
    }else{
    LEDstate = HIGH;
    }
    time = millis();
  }
digitalWrite(LEDPin, LEDstate);
}
```
