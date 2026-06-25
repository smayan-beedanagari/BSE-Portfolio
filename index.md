# Fight Motion Sim
This project integrates an Arduino microcontroller, a 2-axis joystick, and multiple continuous servos to translate hand inputs into real-time physical flight movements via a 4-string suspension rig. The primary challenge was severe voltage sag and random motor spinning caused by drawing too much current from the Arduino's 5V pin, which repeatedly crashed the USB port connection. I learned that high-current motors require an isolated external battery pack, a shared common ground wire with the Arduino to stabilize control signals, and staggered code delays to prevent power spikes.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Smayan Beedanagari | Dougherty Valley High School | Aerospace Engineering | Incoming Sophmore

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
<!--  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 

# First Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

My project currently has 4 servos mounted onto the pvc frame and 1 joystick that controls the 4 servos to spin
For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project
-->

# Starter Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/HAAt5699cr8?si=lJUN_Jn4P_0Znk9a" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Project Description: I built a handheld retro arcade console featuring an 8x16 LED matrix screen, a 3-digit score display, and a 7-button control layout. It runs five different games and saves high scores automatically.

Technical Progress: All components are fully assembled, soldered, and operational. The games load, accept button inputs, and track scores correctly.

Challenges & Solutions: The biggest hurdle was the steep learning curve of soldering so many dense connections. My first attempts were rough, but through patience and practice, my technique drastically improved.

Future Plan: I am now moving on to my intensive project: building a physical flight simulator chassis using PVC pipes, a 4-string suspension rig, and integrating my joystick and continuous motors.

<!--
# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 
-->

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 


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

void loop() {
  // Read raw inputs from both joysticks (0 to 1023)
  int raw1X = analogRead(pinJoy1X);
  int raw1Y = analogRead(pinJoy1Y);
  int raw2X = analogRead(pinJoy2X);
  int raw2Y = analogRead(pinJoy2Y);

  // Read button states (1 = Pressed, 0 = Released)
  int btnUpState = digitalRead(pinBtnUp);
  int btnDownState = digitalRead(pinBtnDown);

  // Variables to hold final movement speeds
  int moveY  = 0;
  int strafe = 0;
  int yaw    = 0;
  int pitch  = 0;
  int lift   = 0; 

  // --- BUTTON LIFT SPEED CONTROL ---
  // Raised speed to 60 for strong, fast vertical movement
  if (btnUpState == HIGH) {
    lift = 60;  
  } 
  else if (btnDownState == HIGH) {
    lift = -60; 
  }

  // --- WIDER HARD DEADZONES ---
  // Raised mapping max to 60 so your joysticks have strong power too
  if (raw1Y >= 640) moveY = map(raw1Y, 640, 1023, 0, 60);
  else if (raw1Y <= 560) moveY = map(raw1Y, 0, 560, -60, 0);

  if (raw1X >= 650) strafe = map(raw1X, 650, 1023, 0, 60);
  else if (raw1X <= 570) strafe = map(raw1X, 0, 570, -60, 0);

  if (raw2Y >= 640) pitch = map(raw2Y, 640, 1023, 0, 60);
  else if (raw2Y <= 560) pitch = map(raw2Y, 0, 560, -60, 0);

  if (raw2X >= 650) yaw = map(raw2X, 650, 1023, 0, 60);
  else if (raw2X <= 570) yaw = map(raw2X, 0, 570, -60, 0);

  // --- THE FLIGHT MIXER MATH ---
  int s1 = 90 + moveY + strafe + pitch + yaw + lift; // Front-Left
  int s2 = 90 + moveY - strafe + pitch - yaw + lift; // Front-Right
  int s3 = 90 + moveY + strafe - pitch - yaw + lift; // Back-Left
  int s4 = 90 + moveY - strafe - pitch + yaw + lift; // Back-Right

  // Constrain to safe servo limits (0 to 180)
  s1 = constrain(s1, 0, 180);
  s2 = constrain(s2, 0, 180);
  s3 = constrain(s3, 0, 180);
  s4 = constrain(s4, 0, 180);

  // --- DISPLAY RAW VALUES AND SERVO OUTPUTS ---
  Serial.print("J1X:"); Serial.print(raw1X); Serial.print(" ");
  Serial.print("J1Y:"); Serial.print(raw1Y); Serial.print(" ");
  Serial.print("J2X:"); Serial.print(raw2X); Serial.print(" ");
  Serial.print("J2Y:"); Serial.print(raw2Y); Serial.print(" ");
  Serial.print("U:"); Serial.print(btnUpState); Serial.print(" ");
  Serial.print("D:"); Serial.print(btnDownState); Serial.print(" | ");
  
  Serial.print("M1:"); Serial.print(s1); Serial.print(" ");
  Serial.print("M2:"); Serial.print(s2); Serial.print(" ");
  Serial.print("M3:"); Serial.print(s3); Serial.print(" ");
  Serial.print("M4:"); Serial.println(s4);

  // Write commands to the continuous rotation servos
  motor1.write(s1);
  delay(2);
  motor2.write(s2);
  delay(2);
  motor3.write(s3);
  delay(2);
  motor4.write(s4);

  delay(40); 
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Arduino Uno R3 | Motherboard of the Flight Sim | $49 | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://store-usa.arduino.cc/products/uno-q-4gb?utm_source=google&utm_medium=cpc&utm_campaign=US-Pmax-Promo-UNOQ&gad_source=4&gad_campaignid=23949316248&gbraid=0AAAAACbEa84VuBlStXMRnLnVjRm0AkVPi&gclid=Cj0KCQjwo_PRBhDNARIsAEcVALUivuxEE-o1Mw77WlOxLyeZLmHbGiXBh5vLvHzij_ToqQfj5GiRdhMaAu6QEALw_wcB)"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
