# Python-Robot-Car
A fully functional Python-controlled robot car for REXTRO exhibition.

## Team Members
| Name            | Role               | Contribution |
|------           |------              |--------------|
| Ramitha | Documentation | README, diagrams |
| Praveen | Documentation | README, diagrams |
| Sajini  | Documentation | README, diagrams |
| Kaveesha| Documentation | README, diagrams |
| Himantha| Documentation | README, diagrams |
| Sakindu | Documentation | README, diagrams |
| Danushka| Documentation | README, diagrams |

## Hardware
- ESP32 / Raspberry Pi
- L298N Motor Driver
- DC Motors(Servors)
- Ultrasonic Sensor
- Battery Pack
- Wheels + Chassis
- Jumpers
- IR sensors
- Buzzer
- LED

## Software
- Python 3
- GPIO libraries
- WiFi/Bluetooth control software



## circuit diagram photos
<img width="194" height="260" alt="image" src="https://github.com/user-attachments/assets/2df807d7-faef-4729-84be-1ffe474d95c0" />




 ## How the Robot Car Works

The robot car operates using Python code to control motors, sensors, and communication modules.  
Here is a breakdown of the working process:

---

### Movement Logic
The car moves by controlling two DC motors through an L298N motor driver:

- *Forward:* Both left and right motors spin forward.
- *Backward:* Both left and right motors spin backward.
- *Turn Left:* Right motor spins, left motor stops.
- *Turn Right:* Left motor spins, right motor stops.
- *Stop:* Both motors stop.

---

### Control Methods
Depending on your design, the robot can be controlled using:

- *WiFi:* The car hosts a small web server; user controls via phone or laptop.
- *Bluetooth:* Commands sent from a mobile app.
- *Keyboard (PC):* Python script listens for key presses.
- *MQTT:* Cloud or WiFi-based IoT control.
---

### Python Code Execution Flow
The normal flow of the Python program is:

1. Initialize GPIO pins  
2. Load motor & sensor modules  
3. Start control loop  
4. Read sensor values  
5. Decide movement  
6. Execute motor command  
7. Repeat the loop continuously  

---

### Power System
- Motors powered by 6–12V battery pack  
- Microcontroller powered by 5V  
- Common ground shared between battery + board  

---

## running videos and photos

