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
  
