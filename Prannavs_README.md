# Steps to get the create_examples_py demos working

## Raspberry Pi Steps - Made with the help of Professor Bouchard at Tuft University
1. Follow these steps https://iroboteducation.github.io/create3_docs/setup/pi4humble/ 
2. Choose rmw_fast_rtps for your RMW_IMPLEMENTATION 


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
13. More info at https://iroboteducation.github.io/create3_docs/api/ros2/ and https://iroboteducation.github.io/create3_docs/hw/rpi_hookup/


## Importatnt
- Sometimes even though the roomba and Pi are connected and everything is setup the right way, ```ros2 topic list``` will not show the Create3's topics
- In this case, connect to ```192.168.186.2``` on your browser (on the Pi), and hover over the Application tab, click on Reboot Robot.
- Close the browser
- Optional: in your terminal type ```ros2 daemon stop```
- Wait for the Roomba to restart
- Try ```ros2 topic list``` in your terminal again and you should see all the Create3's topics
