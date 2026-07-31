# 4DoF Motion Flight Simulator 
This project integrates an Arduino microcontroller, two sepereate 2-axis joystick, and multiple continuous servos to translate analog inputs into real-time physical flight movements via a 4-string suspension rig. The primary challenge was severe voltage sag and random motor spinning caused by drawing too much current from the Arduino's 5V pin, which repeatedly crashed the USB port connection. I learned that wire magament is essential to the suceess of ones own project as it makes way for ease of debugging. I also leanred that while some things may work or seem perfect on paper, they can actually be screwed up during real physical tests, no mater how prepared you are.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Smayan Beedanagari | Dougherty Valley High School | Aerospace Engineering | Incoming Sophmore

![Headstone Image](logo.svg)

<br>

# Third Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/TGuS3Kq9ppw?si=J4U4_iM2vDg7UaVS" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Project Overview
This final phase focuses on the gyroscope that trakcs he x, y, and. coordinates within the system as well as calculate the pitch, yaw and rotation, and then displaying that information on the arduino uno serial monitor. This allows for the user to debug and track exactly where the spacecraft is located within the box

### Technical Progress
The 3-string suspension rig now includes the gyroscope and also includes the very precise position of where the spacecraft is located at. I fine tuned the coordinte tracjing simulation to figure out within a few millimeters of where the spacecraft is located at. 

### Takeaways
The biggest takeaway I had from Bluestamp was learning exactly how a engineer is able to complete their project while also tracking their project with detail. Another big thing i leaned from BSE is how a engineer is able to use the engineering process to debug and finish a project.


### Next Steps

  -**Bluetooth Module:** Use a bluetooth module instead of the wiring sstem i have currently which would allow for me to connect from anywhere in the clasroom

<br>


<br>

# Second Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/uG7d_T7f3lo?si=XROaKxHfgMTZGOT8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Project Overview
This phase focuses on the complete physical assembly and wiring of the controller. It includes 6 buttons and 2 joysticks which help maneuver the spacecraftar ound the box. Joysticks are used for basic x, y, and z movement, and he buttons allow fr pitches up, down, and yaw left and right giving access to 6 DOF, however in real world application due to the servos and arduinos limited processing power yaw is not achievable and pitch is very limited with 3 motors

### Technical Progress
The 3-string suspension rig is fully assembled, and the cockpit chassis is successfully suspended within the PVC frame. The control system has been upgraded to include the second joystick and motor control buttons. Lines are routed from the continuous servos to the central rig, and the software flight mixer now calculates outputs for combined 3D motion and elevation control.

### Challenges & Solutions

  -**Line Sag & Calibration:** Uneven weight distribution on the PVC frame can cause unwanted twisting, which I'll fix by adding physical counterweights.

### Next Steps
  -**System Testing:**  Fine-tune the PVC counterweights to ensure the cockpit centers automatically when joysticks are released.


  -**Final Mechanical Calibration:** Assemble the 3-string suspension rig and hang the cockpit chassis to complete the project

<br>

# First Milestone


<iframe width="560" height="315" src="https://www.youtube.com/embed/moCCDCpR0_c?si=OevAo0dc6RMtJR8k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Project Overview
This project is a physical flight simulator chassis built from PVC pipes and a 4-string suspension rig. It integrates an Arduino, a joystick, and four continuous-rotation servos to simulate physical flight motion. Moving the joystick sends X and Y signals to the Arduino, which calculates and spins the servos to physically tilt or pull the suspended cockpit forward, backward, left, or right.

### Technical Progress
The core electronics and basic flight logic are fully operational. The four servos are securely mounted to the PVC frame, and a single joystick is wired and functioning. The software successfully processes the vector mixing, meaning a joystick input accurately commands the specific combination of servos needed to move the rig.

### Challenges & Solutions
  -**Mechanical Tension:** Continuous servos pulling strings will definitively slack or erratic shaking during sudden joystick inputs.

  -**Software Smoothing:** I'm solving this by widening the deadzones and smoothing out the motor acceleration profiles in the code.

  -**Chassis Balance:** Uneven weight distribution on the PVC frame can cause unwanted twisting, which I will fix by adding physical counterweights.

### Next Steps
  -**Milestone 2:** Attach the lines to the servos and calibrate structural movements to match the joystick inputs, and add in the second joystick and altitude buttons for full Z-axis

  -**Milestone 3:** Assemble the 4-string suspension rig and hang the cockpit chassis to complete the project
<br>

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

  -**The Rigging:** Setting up a custom 4-string  rig to handle motion physics.

  -**Controls & Automation:** Figuring out wether buttons, potentiometers, or even joysticks are the way to go in terms of controls, and when selected integrating that control into the breadboard

<br>

# Schematics 

Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

<br>

# Code

This Arduino program runs a 4-motor flight simulator rig by mixing joystick and button inputs. It filters out hardware jitters using custom deadzones, combines your movements (pitch, roll, yaw, and lift) mathematically, and outputs the final speeds to four continuous servos.

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

### Input Processing and Deadzone Management

This section reads live data from the joysticks and buttons, clearing out any minor hardware jitters using custom deadzones. If a joystick is pushed past these thresholds, the code automatically scales the raw signal into a clean control range from -60 to 60.

```c++
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
```

### System Initialization and Pin Mapping

This math engine blends your desired flight movements (pitch, roll, yaw, lift) into specific directions for each corner of the chassis. It also applies a safety restriction to ensure the calculated values never exceed your motors' physical limits.
```c++
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
```

### Motor Execution and Diagnostic Telemetry

This final section outputs all raw inputs and motor speeds to your computer screen for real-time troubleshooting. It then writes the final commands directly to the physical servos using micro-delays to keep the system stable.
```c++
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
```

<br>

# Bill of Materials

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Arduino Uno R3 | Motherboard of the Flight Sim | $49 | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Continuous Rotation Servos | Pulls or Loosens String on Flight Sim | $16 | <a href="https://www.amazon.com/MTDELE-10Pcs-Arduino-Raspberry-Controls/dp/B0D6FR6WYV/ref=sxin_17_pa_sp_search_thematic_sspa?content-id=amzn1.sym.292df443-b323-44ae-8b40-9a666975b8b5%3Aamzn1.sym.292df443-b323-44ae-8b40-9a666975b8b5&crid=3MZ61HWBLRMAN&cv_ct_cx=rotation%2Bservos%2Barduino&keywords=rotation%2Bservos%2Barduino&pd_rd_i=B0D6FR6WYV&pd_rd_r=ee5cafa6-50be-47e8-8f2a-2492eeed9690&pd_rd_w=9Nlxe&pd_rd_wg=1Swbw&pf_rd_p=292df443-b323-44ae-8b40-9a666975b8b5&pf_rd_r=X6MZPQXAD9EVK4J62976&qid=1785513546&s=electronics&sbo=RZvfv%2F%2FHxDF%2BO5021pAnSA%3D%3D&sprefix=roation%2Bservos%2Barduino%2Celectronics%2C147&sr=1-4-6024b2a3-78e4-4fed-8fed-e1613be3bcce-spons&aref=6yFOVV2beB&sp_csd=d2lkZ2V0TmFtZT1zcF9zZWFyY2hfdGhlbWF0aWM&psc=1"> Link </a> |
| Joystick Modules | Used to Control Servos | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/DEVMO-Joystick-Breakout-Controller-Arduino/dp/B07RB493PT/ref=sr_1_2_sspa?crid=2RE8DQDGZOK1M&dib=eyJ2IjoiMSJ9.7lIMH6yxfSaOcCdCzoE1yNN7Xz4tG2qC5BGCAOAWz5RznLU4AP-QmA53FVRn2CkjBNjvPJ8HgB8ufQ8ZAyGPCwcNDlo8Bi0Dsp5zdEQGptbZhlIecbcD8QP6c1sn9rjSDvZBI6rI6u-f6MqO0vwu65ncg_p9MxL4blS9oS7czmv9p1Hgq3zF6vZtyu3IiWWWg4CfQcuU-4ns8thI5vufVVhUzaWb8_fSzBtKeNqanlQzHHv8Oswu8taDDplm-qj8Ual3xBLGJK8ZmmfT473b8-pyiNdKlNn1s4y_LrHvxbQ.sLVhfMweibswbvSQ2S7SWCCXqBsra_r9y0EJWUh8IZk&dib_tag=se&keywords=joystick%2Barduino&qid=1785513747&s=electronics&sprefix=joystick%2Barduin%2Celectronics%2C185&sr=1-2-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&th=1)"> Link </a> |
| Button Modules | Used to Control Servos | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Metal Screw Eyes | Used to Route String to Spacecraft | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Slick String | Attaches from Servo to Spacecraft | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
