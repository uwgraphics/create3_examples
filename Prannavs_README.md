# iRobot Roombda Create3 Demos

# Steps to get the create_examples_py working

## Raspberry Pi Steps
1. Get a raspberry pi 4
2. Install Ubuntu 22.04.2 LTS Desktop from the Raspberry Pi Imager (https://www.raspberrypi.com/software/) <img width="564" alt="Screen Shot 2023-05-11 at 1 59 56 PM" src="https://github.com/uwgraphics/create3_examples/assets/71447892/9970da9a-06f6-4ffe-9371-33cfd515e001">
3. Create a user on your Pi and log in
4. 


## Create3 steps

1. Connect the roomba to the Pi with a USB cable
2. Make sure the switch in the control panel is swithed towards USB and not bluetooth (the light should be orange)
3. If the roombda to pi ethernet over usb connection is successful, you should be able to connect to ```192.168.186.2``` on your browser (on the pi) and see the Roomba's webserver page.
4. On the webserver, click on Application and then Configuration - you should be on the App config page
5. Set the RMW_IMPLEMENTATION to rmw_fastrtps_cpp
6. Click Save and then the blue link that says Restart Application
7. Close browser
8. Open a terminal
9. Type in ```ros2 daemon stop```
10. Wait for the roomba's restart chime
11. Type in ```ros2 topic list``` and you should see a the Create3's topics
12. Change lights color with ```ros2 topic pub /cmd_lightring irobot_create_msgs/msg/LightringLeds "{override_system: true, leds: [{red: 255, green: 0, blue: 0}, {red: 0, green: 255, blue: 0}, {red: 0, green: 0, blue: 255}, {red: 255, green: 255, blue: 0}, {red: 255, green: 0, blue: 255}, {red: 0, green: 255, blue: 255}]}"```
13. More info at https://iroboteducation.github.io/create3_docs/api/ros2/


