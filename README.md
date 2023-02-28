# create3_examples

Example nodes to drive the iRobot Create 3 Educational Robot.

# Setting up the Pi and connecting to the Create 3
To set up the Pi on the Roomba, we mostly followed [this official guide](https://iroboteducation.github.io/create3_docs/setup/pi4/), with some slight modifications. For completeness, the following is the entirety of what we did to get the Pi connected to the Roomba:

1. Connect Roomba to Raspberry Pi 4 via USB-C as described in [this guide](https://iroboteducation.github.io/create3_docs/hw/rpi_hookup/).
2. Follow steps 1-3 in the [official guide](https://iroboteducation.github.io/create3_docs/setup/pi4/)
3. Follow step 4 in the official guide, including the UWNet wifi in addition to the usb0 connection:
```
        usb0:
            dhcp4: false
            optional: true
            addresses: [192.168.186.3/24]
        wlan0:
            optional: true
            access-points:
                "UWNet": {}
            dhcp4: true
```
4. Follow steps 5, 6, and 7 as in the official guide. On the first boot with a Raspberry Pi, you will be prompted to enter a username and password, but the default username and password will not work immediately. Wait a few minutes for the Pi to run some first-time setup, and you'll see some message about tty, at which point you can enter the default username and password (both `ubuntu`).
5. Reboot the Pi by typing `reboot` to the console
6. Follow step 8 in the official guide. If you have some trouble with packages installing, read the error message and do as directed, (should be `sudo apt get update`)
7. Follow step 9 directions for rmw_fastrtps_cpp. No custom configuration is needed for fastrtps, it should work out of the box. Make sure that the RMW for the Create 3 is set to fastrtps as well, as described [here](https://iroboteducation.github.io/create3_docs/setup/xml-config).
8. Reboot the Pi: `reboot`
9. Running `ros2 topic list` should give a long list of topics provided by the create 3, as described [here](https://iroboteducation.github.io/create3_docs/api/ros2)

# Everything below this point comes from the forked create3_examples repository
### Dependencies

 - [ROS 2 Galactic](https://docs.ros.org/en/galactic/Installation.html)


### Build instructions

First, source your ROS 2 workspaces with all the required dependencies.
Then, you are ready to clone and build this repository.
You should only have to do this once per install.

```sh
mkdir -p create3_examples_ws/src
cd create3_examples_ws/src
git clone https://github.com/iRobotEducation/create3_examples.git
cd ..
rosdep install --from-path src --ignore-src -yi
colcon build
```

### Initialization instructions

You will have to do this in every new session in which you wish to use these examples:

```sh
source ~/create3_examples_ws/install/local_setup.sh
```

### Run the examples

Refer to the individual examples README.md for instructions on how to run them.

### Potential pitfalls

If you are unable to automatically install dependencies with rosdep (perhaps due to [this issue](https://github.com/ros-infrastructure/rosdep/issues/733)), please do be sure to manually install the dependencies for your particular example of interest, contained in its package.xml file.
