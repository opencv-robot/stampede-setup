# Stampede

## Objective
Create a rover with the ability to autonomously navigate to previously planned locations 
using GPS navigation. This will serve as the foundation for future rover projects.

	
## Hardware
### Bill of Materials (BOM)
	
### Chassis 
	Due to the narrow chassis of the Traxxas drivetrain, accommodations were made to allow for 4 mounting locations. Two of the provided holes on the chassis were manually threaded for M3 screws. In order to reveal these holes, the original module that contained the throttle and steering wires had to be removed. The other two holes were repurposed from the mounting holes for the original battery mount.
### Upper and lower plate 3D file


![](/images/CAD_pic1.png)

![](/images/CAD_pic2.png)

The lower plate contains most electrical components, such as the PIXHAWK 4 board, Jetson Nano, and battery pack. These components were placed here in order to be protected from the elements, as they are sensitive and prone to damage. The components on the actual plate of the rover are mostly mounted on additional standoffs in order to minimize interference with one another, but better planning in the future could eliminate this issue.
The upper plate only contains the GPS module and camera mount. The camera mount consists of a suction cup, which rendered the lower plate unsuitable due to the large number of mounting holes that compromised the suction’s ability to create a vacuum and properly adhere to the surface. Therefore, it was mounted on the top. During initial testing, we found that being in close proximity with other electrical components in the lower plate caused accuracy issues as well as electrical interference, so it was mounted on a mast above the upper plate to eliminate these issues.


### Wiring Diagram

## Setup

### QX7

Although the default settings on the controller allow for basic maneuverability of the rover, some minor adjustments allowed us to optimize it to suit our needs. 
Since radio channel 1 and 3 were used for throttle control and steering respectively in Mission Planner, the radio channel assignments in the controller were adjusted accordingly by pressing the menu button followed by the page button until the channel mixer page was reached.
After this change, the rover can be controlled intuitively, namely, the throttle is controlled by moving the left joystick up and down, and steering by moving the right joystick left and right.
In addition, a physical Arm/Disarm switch was set as the leftmost switch using the same process on channel 6.
Finally, a physical knob was mapped to switch between Manual and Guided Flight modes for testing purposes on channel 5.
### R9SX  
Need to Pair the R9SX and QX7 
update the firmware of R9SX steps 
Press and hole the R9SX pair button , then connect a external 5V power to R9SX any of IO port (+ and - ) , the led light should change from flashing red to solide red.   Then turn on the QX7 , follow the second hal


### Mission Planner Parameters
1. CH5_OPTION was set to the value that corresponds to changing Flight Modes.


2. CH6_OPTION was set to 41, for Disarm/Arm.
ARMING_REQUIRE was set to 1 instead of 0 so that the user can choose between disarming and arming after the rover is powered on.

3. ARMING_RUDDER was set to zero as it was replaced by the physical Arm/Disarm switch. Originally, this default setting would cause the rover to disarm during normal operation.

4. WP_SPEED was set to a lower value to ensure that the rover would not become hazardous during autonomous operation.

5. WP_RADIUS was set to a lower value so that the rover would be more precise when arriving at a waypoint.


## FAQ

### Why does the display show GPS No Fix?

Usually this is because the rover is in an indoor setting and the signal is too weak. Resolve this by placing the rover outdoors and this should go away.

### Why isn’t the remote controller working?

There can be a variety of reasons, but for the most part, it is because after the rover is powered on, the reset button on the ESC module needs to be pushed. Otherwise, no power is sent to the motors and servos.

Also try going to Config > Mandatory Hardware > Radio Calibration, and recalibrate the radio controller.

### Why does the display show BAD AHRS?

This can be ignored, and usually goes away after a while.

### Why does the display show BAD GYRO HEALTH?

This may have to do with the mounting of the GPS/Compass module. Try isolating it from other electrical components.


