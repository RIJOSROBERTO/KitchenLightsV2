# KitchenLightsV2
DMX-512 lighting controller running on ESP8266 and controlled by Samsung SmartThings Hub. 

V1 of this project started out with a Roboduino board in the back of a light switch, which controlled the kitchen lights which were mostly on DMX-512 bus using multiple controllers.  The human interaction is via 2 x faceplates with 6 buttons each and 4 LEDs.  The power for the Roboduino came from one of the DMX dimmers which supplied +12v on one of the connectors.  This worked extremely well for 7 years.  With the appearance in the house of a Samsung SmartThings, I wanted to make the lighting circuit communicate with this home automation platform, and the desire came at a time when I was playing with ESP8266 boards.
V2 of the Kitchen Lighting controller is still at the experimental stage, however in my thinking, the problems to be faced / considered are:
1)  Can WiFi be seen behind the metal facia of the light switch... if it can then this is represents a simple solution because the existing controller can just be relaced.
2)  The lighting units are scooped out versions of GET / Schneider Electric Ultimate Screwless Dual Gang Electronic dimmers which matched the rest of the outlets in the kitchen, but also had the buttons I needed.  Over the years, the surface of the switches has worn, and to be honest, behind the faceplate is a mess because I wanted to keep the switches on their PCBs to keep the spacing, but the removal of the unneeded components left a disaster area, which while functional, is not robust (or pretty).  If major rework is needed on the controller, then I may get new circuit board made in China for the controller and the switches.
3)  The ESP8266 boards I have been using will not be happy with the 12v due to their lightweight regulators, and I really do not want to put a buck converter behind the switch plate - partly due to the space etc.  If I am fabricating a new board then that is less of an issue, but currently is a concern
4)  Should I leave the existing face plates in place but change them from DMX to i2c along the current wiring to the ESP8266 board which is located in a more sensible position, and it can receive the switch positions from the facia from a more WiFi friendly position, and then it can communicate with SmarthThings and speak DMX to the lighting units.  I feel sure that i2c might not be up to (or reliable) due to the distance, but it is something to be considered.
5)  ST-Anything seems to be a good project to begin customising to control the lighting controller, but for some reason, I am a little uncomforable with the Parent / Child device handler arrangement being used.  In my mind I was hoping for a more feature rich single SmartThings device, but maybe that would cause problems.  This is likely to become clearer once I build some momentum.
6)  The 75176 used for the DMX transmission is a 5v part and the ESP8266 is 3v3.
7)  I would like to introduce a lux sensor into the controller
8)  I would like to incorporate a presence sensor into the kitched also.

DMX devices:
 These are the DMX devices controlled by this program:
 1)  NJD DPX12/4 Channel Mains lighting Dimmer (This now needs to be set to F9 as no GU10's are dimmable due to bulb failure rate).
 2)  CT305R LED Dimmer
 3)  3Ch Relay box  - This is a late addition to fix a problem with the CF GU10's which failed very easily and even when the DPX12 simply acted as a switch, this caused the replacement LED GU10s to flash.  While the code for this device is in this program, it is not currently used. (Obsolete - this DMX devioce was removed when better dimmable LED GU10's were brought in and could be controlled by the NJD DPX12/4 without flickering or expiring quickly).
