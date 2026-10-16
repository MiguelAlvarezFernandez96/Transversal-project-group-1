# Transversal Drone Project (GROUP 1)
Transversal project from group 1. Project made at EETAC as part of the master of drones.

## Very Basics of the Drone and its Components 

When we started the transversal project, the first thing we had to understand was simply: what is a drone, and what are the main parts that make it fly? 

A drone (or UAS) is basically a flying robot made of several subsystems that work together: the frame, the motors and propellers, the electronics, the sensors, the battery, and the software that controls everything.  

The Hexsoon EDU450 is a quadcopter designed for education and research. Understanding this particular drone helped us connect the basic theory to a real system. 

The EDU450 is built around a 450mm carbon fiber frame, which makes it lightweight but strong enough for training flights and small payloads. The frame follows the classic 'X' quadcopter layout, meaning it has four arms with one motor on each arm this layout is very common because it provides good stability and simple control 

 

### Airframe (Structure) 

The frame is the physical body of the drone. It's usually made of carbon fiber because it's strong and lightweight, its job is to hold everything together: motors, flight controller, battery, GPS, wiring, etc. 

The frame of the EDU450 is made of Carbon fiber plates and arms. 

During the first sessions, we noticed how rigid the material is.  

This is important because it reduces vibrations that could affect the sensors. 

The frame includes:  

Central Plates for mounting the flight controller 

Four arms for the motors 

Landing gear 

Space for the battery Underneath 

 

### Propulsion system 

This is the part that makes the drone fly 

### Motors 

The EDU450 uses brushless motors that are typical for medium-size quadcopters. 

Each motor has a specific rotation direction (two clockwise, two counterclockwise), which is essential for stable flight. 

### Propellers 

The propellers are also matched to the motors, we learned that installing a propeller in the wrong direction would make the drone unable to lift off, so this detail is more important than it seems 

 

### ESCs (Electronic speed controllers)  

ESCs are small electronic boards that control how fast each motor spins. 

They receive commands from the flight controller and adjust the motor speed instantly to keep the drone stable.  

### Power System 

The drone is powered by a LiPo battery. 

These batteries are lightweight and can deliver high current (usually 4S {14.8V}), which provides enough power for the motors and electronics. 

The battery is mounted under the frame using straps, and it connects to the power distirbution board that sends power to the ESCs and the flight controller. 

### Autopilot 

This is basically the brain of the drone. 

The EDU450 is designed to work with open-source autopilots like Pixhawk, and it runs PX4 or ArduPilot Firmware 

It includes: 

IMU (accelerometer + gyroscope)  

Magnetometer 

Barometer 

Microprocessor 

This controller is mounted on vibration-damping foam or rubber to reduce noise from the motors.  

We also connected: 

GPS module 

Telemetry radio 

RC receiver 

The flight controller reads all these sensors and constantly adjusts the motors to keep the drone stable.  

It also receives commands from the pilot and executes them. 

Navigation & Sensors 

The GPS module is mounted on a small mast to reduce interference from electronics. 

It provides positions, altitude, and heading. 

 

Telemetry is done through a radio module that sends real-time data to QGroundControl.  

 

 

### Raspberry Pi Integration (Optional) 

This project also introduced the possibility of using a Raspberry Pi as a Companion computer. 

This allows more advanced tasks like  

Autonomous missions 

Computer vision 

Data logging 

Custom scripts 


During the project we had to deal with some missing or broken components that we had to wait for the teacher to change them. 

## Frame Assembly (Part 1)

The main objective of this step of the transversal drone project was to assemble the frame and main flying elements of the drone our group will utilize going forward. 

The transversal drone is a simple quad-copter layout; therefore, the assembly of the frame included the central body containing the power distribution board and the four arms connecting to the set of four brushless DC motors. The result of this step yields a drone frame as shown below:

<img src="Fotos%20Transversal%20project/Config_1.png" alt="Foto 2" width="500">

The assembly of the drone frame wasn’t particularly complicated, however, there were some key things to keep in mind: one, that the drone’s motors were correctly mounted making sure that they are spinning in the correct direction during flight, two, that the arms and frame were correctly oriented, and three, that there was sufficient space inside the frame for all the wiring to be well organized and functional. Note that the side with the orange arms was defined to be the front face of the drone.

In the end, the first part of the drone frame assembly was completed without issue, and the assembly of the drone frame would continue in the second part focusing more on guidance and power systems.

## Autopilot Configuration and Calibration

In this activity, we worked with the Pixhawk Orange Cube autopilot to learn how it works and how to prepare it for the drone project.

The autopilot is also capable of generating the motor control signals to maintain the stability of the drone, depending on the flight mode that has been chosen. For example, in Alt Hold flight mode the drone will keep its height constant as long as the drone operator does not modify it from the radio. To do this, the autopilot will use the information it obtains from internal sensors (such as the barometer, accelerometer, gyroscope). 
We are gonna configure the SB switch to control the flight mode. Since the SB only have 3 positions, we configure 3 different mode: 

Alt hold: Stabilizes in altitude using the internal barometer
Loiter: Stabilizes in altitude, pitch and roll using the GPS (needs good GPS coverage)
RTL (return to Launch): The drone will return directly to the launch position. First will ascend to a defined altitude.
The autopilot can also execute a flight plan autonomously. In this project, we will configure the laptop as a ground station with the flight plan using Mission Planner.

First, we connected the radio receiver, GPS module and buzzer to the autopilot. 
https://www.youtube.com/watch?v=2Jm9zshM1Sc

Then, we installed Mission Planner on the laptop, which we used as a ground station to configure the autopilot and communicate with it.
https://ardupilot.org/planner/docs/mission-planner-installation.html

Once everything was connected, we installed the required firmware (https://www.youtube.com/watch?v=MUiUbNqETsk). For this we need to connect the Pixhawk Orange Cube to the computer with Mission Planner and go to the setup to install the firmware "Orange cube Plus". When we had the firmware installed, we configured the necessary parameters. First we start with the Frame type. After applying the changes following the tutorial, we rebooted the autopilot to check that everything was working correctly. We verified that the LEDs turned on and that the buzzer produced a sound.

<img src="Fotos%20Transversal%20project/Config_1.png" alt="Foto 2" width="500">


https://www.youtube.com/watch?v=8aF4e0XCMpo
 
Next, we calibrated the accelerometer and compass to ensure that the autopilot could correctly estimate the drone's orientation and heading. 

https://www.youtube.com/watch?v=slux0oX2Qig&feature=youtu.be 

We also calibrated the radio and checked the minimum and maximum PWM values generated by the throttle, which were approximately 982 and 2006.

https://www.youtube.com/watch?v=0Ii1I8D2gro&feature=youtu.be 

Finally, we configured the three flight modes using switch SB on the radio: Alt Hold, Loiter and RTL. Alt Hold allows the drone to maintain its altitude using its internal sensors, while Loiter uses GPS to help maintain its position. RTL is used to make the drone return to its home position. We also configured the RTL altitude to 7 metres, so that the drone climbs to the selected altitude before returning to the launch point.
youtube.com/watch?v=PNEuuCZnhX0&feature=youtu.be 

Overall, this activity helped us understand the basic configuration and calibration process of the Pixhawk Orange Cube and prepare it for use in the transversal project.

## Frame Assembly (Part 2)

The aim of the second part of the frame assembly of the Transversal Project Drone was to finalize the assembly of the drone frame by placing and incorporating the radio receiver, autopilot system, GPS, optical sensor, telemetry radio, and the power supply while ensuring everything is properly connected and integrated. The result of this was a drone that after some final calibrations and some software configuration would be able to begin its maiden flight. 

The first task was to fix the autopilot atop the frame using adhesive. Once in position (ensuring it is facing the correct direction) and connected to the power cables, the next device to be connected was the radio receiver. It was important for this step to ascertain that the device was specifically connected to the SBUS OUT and RCIN input ports of the autopilot system. 

After that, the next devices to connect were the four DC motors to the input ports of the autopilot system. Keeping in mind the rotation direction and connections mentioned in part one of the frame assembly the motors were successfully connected. Following that, the GPS system was connected to the autopilot atop the frame using the CAN 1 input. Next was the telemetry radio, this was necessary to ensure proper communication between the drone and Mission Planner for both telemetry and flight plans. This device was connected to the Telem 1 port of the autopilot positioned within the central body with the antenna protruding out the side of the drone. 

The last element that was incorporated was the battery. A setup of two Velcro straps was used to hang the large battery on the underside of the central body of the drone in a manner that facilitated the connection of the power supply to the rest of the systems on the drone. With all the basic elements of the drone assembled, it was time to move on to further calibrations of the drone.

## More Calibrations

In this activity, we continued configuring the Pixhawk Orange Cube to prepare the drone for its first flight test.

First, we configured the telemetry radio to establish communication between the drone and the ground station. https://www.youtube.com/watch?v=6xqEbOzUQSo&feature=youtu.be 

Then, we calibrated the ESCs (Electronic Speed Controllers) and configured the servo functions, the failsafe system and the arming and disarming procedures.
https://www.youtube.com/watch?v=wO8QJQpC3IM&feature=youtu.be 

The failsafe configuration was particularly important because it determines how the autopilot reacts when something goes wrong. We configured the system to return to the home position if the drone loses contact with the radio. We also adjusted the throttle PWM threshold to avoid arming errors related to the failsafe settings.

After that, we configured the battery monitor to check the battery status during operation. We also tested the motors to verify that they responded correctly to the autopilot commands. 
youtube.com/watch?v=DGpoN0KlAYY&feature=youtu.be

Before completing the setup, we loaded the default parameters for our drone frame https://www.youtube.com/watch?v=9pilQ3uT8mA&feature=youtu.be and performed the final configuration checks.
https://www.youtube.com/watch?v=Af_ygwTi_s0 

We also learned the importance of checking the battery level before each flight, making sure that every battery cell has a sufficient charge.

## Simulator, Geofences and Mission Planning 

In this activity, we explored some of the main tools available in Mission Planner to prepare and test drone flights before operating the real platform.
First, we learned about the SITL (Software In The Loop) simulator, which allows us to simulate the behaviour of the autopilot without using the physical drone. This is useful for testing flight plans and understanding how the drone is expected to behave before carrying out an actual flight.
https://www.youtube.com/watch?v=1BPK29MOLlg&feature=youtu.be 

Next, we explored the geofence function, which allows us to define geographical limits for the drone's operating area. We learned how to create a boundary on the map so that the autopilot can detect when the drone leaves the permitted area. We also explored different options, including circular geofences, fence margins, the actions triggered when a boundary is breached, and the difference between inclusion and exclusion zones.

Finally, we worked with the mission planning tools in Mission Planner. We learned how to create a flight plan by adding waypoints, upload the mission to the autopilot and simulate its execution. We also examined what happens when the drone crosses the geofence boundaries.
https://www.youtube.com/watch?v=g-UfZ4gamq8 

Overall, this activity helped us understand how to plan autonomous flights and use simulation and geofencing tools to improve flight preparation and safety. 

## Flight and log analysis 
*TBD*
