# Fight Motion Sim
This project integrates an Arduino microcontroller, a 2-axis joystick, and multiple continuous servos to translate hand inputs into real-time physical flight movements via a 4-string suspension rig. The primary challenge was severe voltage sag and random motor spinning caused by drawing too much current from the Arduino's 5V pin, which repeatedly crashed the USB port connection. I learned that high-current motors require an isolated external battery pack, a shared common ground wire with the Arduino to stabilize control signals, and staggered code delays to prevent power spikes.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Smayan Beedanagari | Dougherty Valley High School | Aerospace Engineering | Incoming Sophmore

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)

# Final Milestone


<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone


<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 

# First Milestone


<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

My project currently has 4 servos mounted onto the pvc frame and 1 joystick that controls the 4 servos to spin based on what would theoretcally move the entire spacecraft forward, backward, left, and right on the x and y axis only. 
For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project


# Starter Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/HAAt5699cr8?si=lJUN_Jn4P_0Znk9a" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Project Overview
I designed and built a handheld retro arcade console from scratch. The hardware features an 8x16 LED matrix screen for visuals, a 3-digit display for real-time score tracking, and a 7-button layout for the controls. On the software side, the console runs five different playable games and includes an automated save system that keeps track of high scores even after the device is turned off.

### Technical Progress
The console is fully assembled, soldered, and 100% operational. During testing, everything booted up smoothly—the games load without errors, the buttons feel responsive with zero noticeable lag, and the high-score memory system tracks and saves data exactly as planned.

### Challenges & Solutions
The biggest hurdle was definitely the soldering. Dealing with so many dense, closely packed connections on a compact board was incredibly frustrating at first. My early attempts were messy and risked shorting out the components. To fix this, I took a step back, practiced my wire management, and learned how to better regulate the iron's heat. With some patience, my technique drastically improved, and I was able to finish the rest of the board with clean, solid joints.

### Future Plan: Flight Simulator Chassis
Now that the arcade console is complete, I'm moving on to my intensive project: building a physical flight simulator chassis.

### Next Steps

  -**The Frame:** Assembling a rigid, lightweight cockpit structure out of PVC pipes.

  -**The Rigging:** Setting up a custom 4-string suspension rig to handle motion physics.

  -**Controls & Automation:** Integrating my flight joystick and wiring up continuous motors to turn digital in-game movements into physical feedback.


# Schematics 

Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 
-->

# Code

This Arduino program runs a 4-motor flight simulator rig by mixing joystick and button inputs. It filters out hardware jitters using custom deadzones, combines your movements (pitch, roll, yaw, and lift) mathematically, and outputs the final speeds to four continuous servos.

<br>

### System Initialization and Pin Mapping

This section maps your physical hardware connections to specific Arduino pins and initializes the system. On startup, it sets all four motors to a universal "stop" position (90) so the simulator chassis doesn't violently jump when powered on.


```c++
#include <Servo.h>

Servo motor1; // Front-Left (Pin 9)
Servo motor2; // Front-Right (Pin 10)
Servo motor3; // Back-Left (Pin 12)
Servo motor4; // Back-Right (Pin 13)

// Joystick Pins
const int pinJoy1X = A0; 
const int pinJoy1Y = A1; 
const int pinJoy2X = A2; 
const int pinJoy2Y = A3; 

// Button Pins for Z-Axis (Altitude Speed)
const int pinBtnUp = 2;   
const int pinBtnDown = 3; 

void setup() {
  Serial.begin(9600);
  motor1.attach(9);
  motor2.attach(10);
  motor3.attach(12);
  motor4.attach(13);

  // Set as regular INPUT. Assumes buttons connect to 5V when pressed
  // with a 10k ohm pull-down resistor to GND on pins 2 and 3.
  pinMode(pinBtnUp, INPUT);
  pinMode(pinBtnDown, INPUT);

  // Force stop on startup
  motor1.write(90);
  motor2.write(90);
  motor3.write(90);
  motor4.write(90);
}
```

### System Initialization and Pin Mapping

This section maps your physical hardware connections to specific Arduino pins and initializes the system. On startup, it sets all four motors to a universal "stop" position (90) so the simulator chassis doesn't violently jump when powered on.


```c++
#include <Servo.h>

Servo motor1; // Front-Left (Pin 9)
Servo motor2; // Front-Right (Pin 10)
Servo motor3; // Back-Left (Pin 12)
Servo motor4; // Back-Right (Pin 13)

// Joystick Pins
const int pinJoy1X = A0; 
const int pinJoy1Y = A1; 
const int pinJoy2X = A2; 
const int pinJoy2Y = A3; 

// Button Pins for Z-Axis (Altitude Speed)
const int pinBtnUp = 2;   
const int pinBtnDown = 3; 

void setup() {
  Serial.begin(9600);
  motor1.attach(9);
  motor2.attach(10);
  motor3.attach(12);
  motor4.attach(13);

  // Set as regular INPUT. Assumes buttons connect to 5V when pressed
  // with a 10k ohm pull-down resistor to GND on pins 2 and 3.
  pinMode(pinBtnUp, INPUT);
  pinMode(pinBtnDown, INPUT);

  // Force stop on startup
  motor1.write(90);
  motor2.write(90);
  motor3.write(90);
  motor4.write(90);
}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Arduino Uno R3 | Motherboard of the Flight Sim | $49 | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://store-usa.arduino.cc/products/uno-q-4gb?utm_source=google&utm_medium=cpc&utm_campaign=US-Pmax-Promo-UNOQ&gad_source=4&gad_campaignid=23949316248&gbraid=0AAAAACbEa84VuBlStXMRnLnVjRm0AkVPi&gclid=Cj0KCQjwo_PRBhDNARIsAEcVALUivuxEE-o1Mw77WlOxLyeZLmHbGiXBh5vLvHzij_ToqQfj5GiRdhMaAu6QEALw_wcB)](https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6?th=1)"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
