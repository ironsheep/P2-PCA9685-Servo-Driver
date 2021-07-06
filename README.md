# P2-PCA9685-Servo-Driver
Parallax Propeller V2 Interface object for the I2C 16-chan Servo Driver with demo of 6-Axis arm control

![Project Maintenance][maintenance-shield]
[![License][license-shield]](LICENSE) 

The goal of this project is to produce a P2 Obex object for control of 16-channels of PWM via I2C.

(while the Servos can be controlled directly from the P2 this demonstrates an alternative fewer wires control of up to 16 servos for a couple of bucks more.)

The demo for this project is some quick software I whipped up to control a 6-axis arm which I'm using to position a motion sensor while i'm developing the motion sensor driver logic.  (This gives me highly repeatable positional testing of the sensor and is frankly quite fun.  *I dreamed of doing this back when I was testing an Apple Watch app which was detecting human falls.*)

And as I started in on this I also decided to use JonnyMac's FlySky SBUS support to also control the arm...

## Current status

What's completed and what's not:

```
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

## Up Next

- Work our way up from the hardware to the arm control to the scripting of the arm

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
