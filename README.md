# P2-PCA9685-Servo-Driver

Parallax Propeller V2 Interface object for the I2C 16-chan Servo Driver with demo of 6-Axis arm control

![Project Maintenance][maintenance-shield]

[![License][license-shield]](LICENSE) 

The goal of this project is to produce a P2 Obex object for control of 16-channels of PWM via I2C.

(while the Servos can be controlled directly from the P2, this demonstrates an alternative using fewer wires to control up to 16 servos for a couple of bucks more.)

The demo for this project is some quick software I whipped up to control a 6-axis arm which I'm using to position a motion sensor while i'm developing the motion sensor driver logic.  (This gives me highly repeatable positional testing of the sensor and is frankly quite fun.  *I dreamed of doing this back when I was testing an Apple Watch app that I was building to detect human falls.*)

And as I started in on this I also decided to use JonnyMac's FlySky SBUS support to also control the arm...


**Latest Repo Updates**:

```
14 Aug 2021 16:36
- Updated this readme with info about files in this repo
20 Jul 2021 16:16
- Moved to separate COG control of servo-slew for smooth arm movements
06 Jul 2021 17:52
- First working flysky positioning of arm so we can setup positions and get servo values
28 Jun 2021 
- Servo slewing is working well
14 Jun 2021 14:45
- Arm is starting to position nicely... now planning needed positions...
06 Jun 2021 17:35
- Just wiring up the hardware so we can develop this driver. 
- Seeding our code base with various starter objects
```

## Current status

I'm working on position placement using FlySky then getting servo position readouts when I get to a desired ARM configuration.  Figuring out the puposes of the FlySky controls for this use case is proving to be quite interesting...

### Current Compile Structure

Files are compiled as follows:

```
arm6axis_demo.spin2
|-isp_arm_6axis.spin2
|-|-isp_i2c_pca9685.spin2
|-|-|-isp_i2c_singleton.spin2
|-|-|-|-isp_serial_singleton.spin2
|-|-|-|-|-jm_nstr.spin2
|-|-|-isp_serial_singleton.spin2
|-|-isp_i2c_pca9685_servo.spin2
|-|-|-isp_i2c_pca9685.spin2
|-|-|-isp_serial_singleton.spin2
|-|-|-jm_nstr.spin2
|-|-isp_serial_singleton.spin2
|-isp_serial_singleton.spin2
|-isp_flysky_rx.spin2
|-|-jm_sbus_rx.spin2
|-|-|-isp_serial_singleton.spin2
|-|-isp_serial_singleton.spin2
```

### Files of Interest

Filename | Purpose | Notes
----- | ----- | -----
arm6axis_demo.spin2 | Top Level file | Demo routines, vairous bring up routines as we develop this code
isp\_arm_6axis.spin2 | Arm Control routines | (1) knows of arm servos and range of each, (2) contains task for slewing all servos (runs in separate Cog)
isp\_i2c_pca9685.spin2 | pc9685 object | all routes to interact with pca9685
isp\_i2c\_pca9685_servo.spin2 | servo object | servo routines which know servo is attached to channel of pca9685
isp\_i2c_singleton.spin2 | singleton i2c object | jm_i2c object reshaped as singleton
isp\_flysky_rx.spin2 | FlySky methods object (wrapper for SBus object) | New upper level routines providing FlySky control-centric methods
isp\_serial_singleton.spin2 | singleton serial object | jm_serial object reshaped as singleton
jm_nstr.spin2 | JonnyMac's string formatter object | 
jm\_sbus_rx.spin2 | JonnyMac's SBus object | Basic SBus access routines


## Up Next

- Work our way up from the hardware to the arm control to the scripting of the arm

## Arm hardware from Amazon

- ~ $41 No Servos [diymore Silver ROT3U 6DOF Aluminium Robot Arm Mechanical Robotic Clamp Claw Kits (Unassembled Parts Without Servos)](https://www.amazon.com/diymore-Aluminium-Mechanical-Robotic-Arduino/dp/B01LW0LUPT)
- ~ $70 w/Servos [Dmyond DIY Aluminium Smart 6-Dof Robot Mechanical Arm Robotic Clamp Claw Kit with MG996R Servos 25T Metal Disc Horns and Screw (Robot Mechanical Arm+Servo)](https://www.amazon.com/Dmyond-Aluminium-Mechanical-MEGA2560-Learning/dp/B07XJM1P21)
- ~140 Arm w/Servos Controller and SW [Robotic Arm Kit 6DOF Programming Robot Arm with Handle PC Software and APP Control with Tutorial](https://www.amazon.com/LewanSoul-Robotic-Arduino-Software-Tutorial/dp/B074T6DPKX)

- SEARCH: [More Arms](https://www.amazon.com/s?k=6dof+servo+arm&ref=nb_sb_noss)

- Servos [MG996R clones ~$20 4pk](https://www.amazon.com/4-Pack-MG996R-Torque-Digital-Helicopter/dp/B07MFK266B)

---

> If you like my work and/or this has helped you in some way then feel free to help me out for a couple of :coffee:'s or :pizza: slices! 
> 
> [![coffee](https://www.buymeacoffee.com/assets/img/custom_images/black_img.png)](https://www.buymeacoffee.com/ironsheep)

---

## License

Copyright © 2021 Iron Sheep Productions, LLC. All rights reserved.<br />
Licensed under the MIT License. <br>
<br>
Follow these links for more information:

### [Copyright](copyright) | [License](LICENSE)



[maintenance-shield]: https://img.shields.io/badge/maintainer-stephen%40ironsheep%2ebiz-blue.svg?style=for-the-badge


[license-shield]: https://camo.githubusercontent.com/bc04f96d911ea5f6e3b00e44fc0731ea74c8e1e9/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c6963656e73652f69616e74726963682f746578742d646976696465722d726f772e7376673f7374796c653d666f722d7468652d6261646765
