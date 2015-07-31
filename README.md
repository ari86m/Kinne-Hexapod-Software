# Kinne-Hexapod-Software
Software for hexapod robot designed by Wayne Kinne and built at Michigan LDS Encampment High Adventure 2015
BOM: Arduino AT Mega 2560, custom shield board, PS2 compatible wireless controller & receiver, 7.2V NiMH hobby battery, 12 Tower Pro MG996R servos & lots of 3D printed parts made by Wayne Kinne. 

********************************************************
GOOD PRACTICES:

1- The 9V battery should be Alkaline or better. A heavy duty battery reading 9.5V may not provide enough current to run the Arduino with our shield board even with out any periferal LED's or sonar.

2- Prior to servo power on, move joints near a middle range position in case they do not have a signal from the Arduino. They will jump toward their zero degree position until the servo control electronics realizes the signal is not just a short pulse, but no pulse. A servo near it's zero position could jam up against it's internal hard stops, meaning pushing a rod into the gear teeth & chaning their shape. Afterward, a servo can have a grinding noise & a 'sticking' spot periodically thru its rotation range. 

********************************************************
Various troubleshooting tips for the robot:

MECHANICAL:

  Issue 1: shoulder to elbow attachment looseness
  Resolution: insert a small spacer (thin plastic - preferably compressible ) to take up the space. Do not use something that is both rigid & too thick because the fastener could break out of the back of the elbow joint. A folded strip of yoghurt lid could work. 

ELECTRICAL: 

  Issue 1: noise on some shield pins cause servo hunting
  Resolution 1: repair/remake shield, investigate adding capacitance, or move servo to different pin
  Issue 2: some shield pins do not drive servos thru a full range of motion
  Resolution 2: don't automatically blame the servos. Try the same servo on a known good shield connection. May need to move the servo to a different shield connection.

COMMUNICATION between PS2 controller, receiver & Arduino:
  Issue 0: Controller not connecting to receiver
  Resolution 0: Remove power for 30 seconds & retry. Make sure 9V battery is an Alkaline or better & not low (the red light can still work, but it won't stay connected). Verify controller battery. Upon Arduino power up, make sure green receiver light is blinking & then turn on controller. If controller was on & has gone to power save mode, press "start" button. 
  
  Issue 1: Pairing the controller to the receiver & arduino
  Resolution 1: Move receiver clock to Arduino pin 9 & ground to the side near pin 9. Then change the clock divider setting in PS2X_lib.h file from the default 4 to 15. Compile, Upload & disconnect USB. Wait 30 seconds. Reconnect USB & open serial monitor. Look for flashing green light on the receiver. 

  Issue 2: Noise (unknown source) causes return data to show button mashes or single button/stick commands that were not given by the user.
  Resolution 2: Band-aid for now: software reports each command to the serial monitor & filters out some combinations of commands that have been seen 

SOFTWARE: 
  Issue 1:  Serial monitor not showing what is expected. It is reporting garbage or nothing at all.
  Resolution 1:  Make sure baud rate at the bottom right in the serial monitor matches the baud rate in the program. Also make sure the sketch does not set the baud rate more than once unless that is what was intended. The command looks like this: Serial.begin(57600); or Serial.begin(9600);








