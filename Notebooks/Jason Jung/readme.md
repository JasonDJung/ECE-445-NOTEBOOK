# 9/12/2023 Jason Zhang (TA) Meeting

# 9/14/2023 Meeting #2 with Professor Gruev and Jason 

* We can compromise a tradeoff if we can’t do everything, getting camera components in, may compromise some efficiency 
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
# 10/02/2023:
* 10am: Design Review For Cross Checking
* 3pm - 5pm: Team Meeting to Review Cross Checking Documents and questions
* All checked each other's schematics and asked questions as appropriately
* Jason (USB-C Schematic)<img width="524" alt="Screenshot 2023-12-05 at 5 00 53 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/f0950ba9-e4a2-47ab-93b6-439e89ec0256">
Voltage Regulators:
<img width="617" alt="Screenshot 2023-12-05 at 5 01 54 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/6f91dd3a-8452-4d8d-b910-99985ea0fe60">
Clock Oscillator:
<img width="376" alt="Screenshot 2023-12-05 at 5 03 54 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/bc3d28ef-4e9e-44d6-887c-f0f82269b97b">

* Isha (MCU Schematic)<img width="283" alt="Screenshot 2023-12-05 at 5 00 40 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/8e959c02-b8bd-4f23-ba7c-39754bbfbe84">

* Amartya (Imager Sensor)
* <img width="382" alt="Screenshot 2023-12-05 at 5 00 27 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/b636e418-1d51-4d36-9546-18dc04958b68">

* Prepared questions to ask Jason P tomorrow
   * Clock Buffer
   * Translators vs LDOs
   * Which pins to ignore: GND_MIPI, S_ADDR, XRST
   * OVP vs Zener Diode
   * ESD Diodes?
# 10/03/2023:
* Met with Jason P to go over design questions (4 - 6pm)
* Compiled a list of questions to ask Professor Gruev during our weekly meeting
# 10/05/2023:
* Geometry of Traces: Including width, length, spacing, differential signals
 * Use calculator IPC 2141:
 * <img width="780" alt="Screenshot 2023-12-05 at 5 05 08 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/bc42aae3-b25e-4488-9421-5e582e6fb3b9">
 * https://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-pcb-trace-impedance
* Analog/Digital Grounds
 * Use Single Ground
* Connect XRST to imagesensor
* Keep Differential pairs close together, keep power lines short and fat
* Capacitors as close as possible to the LDO
# 10/06/2023:
* PCB Review sesions 3-5pm
* Learned about trace geometry and board stackup
# 10/07/2023 > 10/08/2023 :
* Isha and Jason routed, Amartya looked into post processing
* Generated BOM
  <img width="396" alt="Screenshot 2023-12-01 at 3 31 27 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/c99818ac-3d57-455f-884b-203617f6229c">
# 10/09/2023
* Looked over routes, looked over BOM, Submitted to PCBWay for Audit
# 10/10/2023
* First Audit failed, resubmitted after making modifications
# 10/12/2023
* Team meeting with Jason Zhang
* Went over DRC Constraints, and rerouted
* Jason started new Revision for PCB
# 10/14/2023
* Round 2 of Routing:
* ## Setting Up Board Constraints for the Board Advanced PCB Assembly:
* ### Hole Diameter
  * Given Hole diameter of 0.2mm, max board thickness is 1.6mm
  * Given Hole diameter of 0.25mm, max board thickness is 2 mm
  * Hole Position Tolerance is +/- 0.0075 mm
  * Aspect Ratio = Board Thickness / Drill hole
  * Hole to Hole Spacing >= 0.3 mm
* ### Trace Width Calculation
* Following the standard above, the following widths were calculated
 * 0.254 mm trace width for power
  * When Routing Power Traces, 
 * USB 3 = 90 Ohm Differential Impedance +/- 5 Ohm
 * Be conscious of the return path for signal traces
# 10/16 - 10/17
* Met with Professor Gruev to go over design, implemented feedback. Finished new revision of PCB Board
* <img width="275" alt="Screenshot 2023-12-01 at 3 32 22 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/1d88eeb5-db1f-4eed-a9f2-c6e7519a14c9">
<img width="579" alt="Screenshot 2023-12-01 at 3 33 08 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/1f0a5112-6ed6-4ecd-b684-0fa4bd10d9ae">
* Sources:
* https://www.pcbway.com/capabilities.html#
# 10/19 
* Submitted Email to Jason P to Submited PCBWay Order
* Development board came in this week, started looking at code that can be prototyped
# 10/23
* Met with Jason P to go over PCBWay order and adjust design to account for Manufacturing capabilities
* Dielectric and PrePeg layers were intiially thought to be 4.5 and 0.1mm when they are 4.29 and 0.11mm respectively in reality.
* Had to rerout USB 3.1 Traces, but kept MIPI CSI-2 Signals the same.
* Started Development Board Code Research because it came in:
<img width="653" alt="Screenshot 2023-12-05 at 5 22 06 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/e69d884a-d206-4622-b39b-646085580c1a">
* We had the OV5640 Camera board attachment
https://www.e-consystems.com/CX3-Reference-Design-Kit.asp
# 10/24
* Looked into code for Development Board
* Was able to display video on the development board, but now need to use that on the IDE.
# 10/26 Project Emergency
* Found out today that our lead time to get PCB assembly is up to 30 days. We have started exploring other options through 4PCB and JLCPCB, as well as potentially soldering components on our own
* This lead time prevents us from getting our PCB until the week of the mock demo.
* Will order components separately through myECE as a contingency plan.
# 10/30 : 
* Got digikey order approved
* PCBWay Board and Stencil shipped today
# 11/3/23: Finished Soldering PCB Board:
<img width="335" alt="Screenshot 2023-12-01 at 3 33 29 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/3aebd50f-255c-4b24-9c1c-41275c259d0f">

### Procedure for Board Assembly (~4 hours):
* Get PCB and PCB Stencil, and align the stencil along the board so that the pads are only showing. Tape down the board to the stencil without disturbing this alignment
* Place PCB and Stencil on the table, and grab boards of the same thickness (Extra Square PCBs are fine) to stabilize the PCB in place.
* Grab a stick and press down on top of the stencil to keep it flesh against the PCB. Not doing this can result in solder paste smearing underneath the pad.
* Using solderpaste that is lukewarm, get a metal scraper and smear it evenly across the stencil, making sure to fill in for every pad exposed.
* If not down successfully, you will have to repeat the previous steps
* Carefully remove the stencil from the PCB, and place the PCB in the fridge while you get your components ready for placement on the PCB
* Using tweezers, place components on each of their respective PADs on the PCB. Using a microscope is helpful in this case.
* Bake in the reflow oven after doing this according to your solder paste's specifications.

# 11/4/23:
* There were issues with the clock in our PCB, resistors that were in series had to be removed, and the output of our clock buffer required pull up resistors.
* Our voltage regulators were also not all working, they needed to be resoldered and some parts needed to be removed.
* After working on removing the resistors, we decided that it was best to start again since our board started to get damaged.
* e-con Systems Developmenbt

# 11/6/23: Soldered 2nd PCB Board
* Issues with our clock were fixed, but then we realized that we were not getting voltage on our board after plugging it in.
* Also certain parts of the board were getting hot.
* Soldered pull up resistors to the board
* <img width="213" alt="Screenshot 2023-12-01 at 3 34 09 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/0e78b294-316a-4d49-b674-11e3f1d5c5c8">

# 11/8/23: 
* Resoldered the mux
* Worked on firmware
* USB C connector kept falling off.
# 11/9/23:
* After meeting with our TA and one of his peers, we were advised that there was probably a short on the board.
* Used a power meter and a breakout board to debug our circuit.
* <img width="370" alt="Screenshot 2023-12-01 at 3 34 34 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/4de7065c-d674-433e-a09d-025fa8a820fa">

# 11/10/23:
*  Determined that it was the back LDO that was the issue, removed this and things wroked out.
# 11/11/23:
* Took measurements on the output of the clock buffer, noticed a good amount of noise 
# 11/13/23:
* Met with Jason P, who helped us verify where the short was on the board
* Ripped apart a USB C cable, measured Power to Ground impedance using a multimeter, verified that a short existed.
* Removed every component on the board, one by one, using a multimeter to check the impedance to see if it changed.
* USB C Connector kept falling off, soldered it back on aggressively
# 11/15/23:
* Soldered pull up resistors on Vcc on the clock buffer
* Clock is noisy, not identified correctly on the device:
* 
* 
# 11/16/23:
* Realized that our PCB was on the wrong bootmode
* Are able to download to the program., still not recognized as a camera.
* Met with Zhongmin, took us down to the Biosensors Lab to test our development board's multispectral capabilities. Development board does not work
# 11/17/23:
* Met with Professor Gruev, he helped us take off the IR lens on our development board. Development board can now see in IR. Tested with IR light on iPhone.

# 11/24/23:
* Ran USB 2.0 Firmware on the board, were able to enumerate a pattern directly from memory:
<img width="204" alt="image" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/f5bf8966-296f-4350-b8cd-9f2a20be9859">
# 11/25:
* Isha designed CAD enclosure for development board so that it can fit a C Mount lense
<img width="696" alt="Screenshot 2023-12-05 at 5 29 28 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/7ba88ddd-0a76-447c-90f2-cf02b1bdce21">
<img width="655" alt="Screenshot 2023-12-05 at 5 29 40 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/97842905-1afa-462e-9302-a25e4c1040bc">

# 11/28/23:

* Tested the development board code in the Biosensor's Lab, was able to get IR spectral sensitvity
* Experimental Setup:
<img width="283" alt="Screenshot 2023-12-05 at 5 16 25 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/ba486b58-89b0-413c-a315-2b0f21e3b7d7">
<img width="166" alt="Screenshot 2023-12-05 at 5 16 33 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/8b59c936-78a3-457b-a784-52323eb93db9">
* IR Sensitvity Result
<img width="45" alt="Screenshot 2023-12-05 at 5 17 37 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/b025490f-1443-4a06-805a-1ae03e94ab03">
# 11/28/23:
* Final Demo
# 11/29/23:
* Since preliminary CAD Enclosures didn't work, we reiterated our CAD Design with same dimensions
* <img width="241" alt="Screenshot 2023-12-05 at 5 31 42 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/c5f9d5b5-2714-4873-87d9-d05a69fb0ed9">
# 12/1/23:
* CAD Print Warped
<img width="185" alt="Screenshot 2023-12-05 at 5 32 21 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/81931855/3409c790-73f7-4622-a7ed-346ddc227092">
# 12/3/23:
* Worked on Final Presentation and Final Report
# 12/4/23:
* Worked on Final Report, practiced final presentation
# 12/5/23:
* Pitched final presentation, finished final report.
* Got CAD enclosure from Siebel Center. 
