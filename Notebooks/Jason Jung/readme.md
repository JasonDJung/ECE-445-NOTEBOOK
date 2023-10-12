# 9/11/2023 Group Meeting
* Prepared for TA meeting, proposal rought draft, created a table for potential MCUs to choose from.

# 9/12/2023 Jason Zhang (TA) Meeting

# 9/14/2023 Meeting #2 with Professor Gruev and Jason 

* We can compromise a tradeoff if we cna’t do everything, getting camera components in, may compromise some efficiency 
* Emphasis on PCB design, simple MCU, image sensor, find code that does that job for you before getting MCU, make sure layout is
* Image Sensor : any camera will have some UV and NIR sensitivity . over 1 MP camera,
* Barebone bumps, ball bonding chips suck and require high precision
* Will need to remove them, Reflowing BGAs are really tough
* QFNs or surface mounts are easier
* Power subsystem = usb c connection
** Where is the main power coming form in our subsystem
** Image sensor will have multiple power supplies
** Analog PS, digital PS, pixel power supplies: Separate voltage regulator
** Separate voltage Regulator for MCU
** Values needed for diagram
** 5 V = USB itself
** 3.3 V = Regulator

# 9/21/2023 Meeting #2 with Professor Gruev and Jason 
* NDAs still getting signed:
* Goal is to Order next week or ASAP once CFOP is acquired

* 2 MIPI cameras

### 3D printing
* Siebel Design Center has 3D printing available to ECE445 Teams
* Order Spools, Bring own filament and design, Flex cables specifically meant for PCBs
* Autodesk Cad for 3d Enclosure CAD> Go to Jason’s Office Hours
* DRC: Design Rule Check , run this KiCAD when designing PCB
### Team Meeting after 
* Started Design Document
# 9/24/2023 Team Meeting
* Sourced Parts for PCB
* Need to ask questions to TA about clock oscillator options
* Started PCB design
#### Splitting up KiCad
* Power: Isha
* Camera Connection : Isha
* Make Symbol for Camera : Jason
* MCU (All Hands) :
* MIPI and USB C Connectors : Amartya
# 9/27/2023
* Design Document 
# 9/28/2023 Meeting Notes with Jason Zhang and Professor Gruev
* Logistic Boards
  * Use Electronics Service Shop before ordering, 
  * Go to PCB review on Tuesday
  * Before submitting , we have to pass audit on PCBWay before submitting it on PCBWay or else it won't be able to order.
  * have to pass audit through PCBway website BEFORE 10/10
  * email jason P abt process to approve PCBway assembly of our board
  * Order dev board and camera TODAY
  * Email Gruev data sheets TODAY
  * Email Gruev schematics early next week
  * Start Layout before meeting w Gruev
* Useful Links
* https://docs.google.com/spreadsheets/u/3/d/153RUJO1VnosQzeARsF-QkoYVccRl2KKlXqfhqvoIaU0/edit#gid=0
* https://docs.google.com/spreadsheets/d/1pqk_fN6fMIju8Ngkg-_4KTQ6uj0hrlnuv49PCC0ijBk/edit#gid=1992434365
  
# 10/07/2023 > 10/08/2023 :
* Isha and Jason routed, Amartya looked into post processing
* Generated BOM
* 
# 10/09/2023
# 10/10/2023
# 10/12/2023
# 10/12/2023
