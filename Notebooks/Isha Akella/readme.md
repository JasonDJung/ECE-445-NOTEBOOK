# Isha's ECE 445 Lab Notebook

## 8/31: Meeting with Professor Gruev
We met with Professor Gruev to discuss the intricacies of his pitched project and clear up any of our doubts regarding the vision for the solution. Afterward, we created and submitted our RFA to the web board. 

## 9/4: Component Research & Project Timeline
We created a rough timeline for the remainder of the semester to have a general indication of when we would like to complete certain tasks. Afterward, we spent a couple of hours researching an image sensor that fit all the necessary criteria.

## 9/7: Component Research & Team Contract
We received confirmation from Prof. Gruev that the image sensor we chose was perfect for the scope of our project. Began researching microcontrollers that were MIPI and USB 3.0 compatible while staying within the desired size range. 
Additionally, we started and finished the team contract due 9/14.

## 9/11: Component Finalization & Project Proposal
We received feedback from Prof. Gruev related to the MCUs we found and used the feedback to narrow down and pick an MCU for the project. Worked on the deliverables necessary for our first TA meeting on 9/12 which included a block diagram [Figure 1], three high-level requirements, and one subsystem requirement.  
Finally, we began working on our project proposal which is due on 9/14.
<img width="572" alt="Screen Shot 2023-11-20 at 4 01 14 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/84357995/46022132-94df-47a0-b079-998e5052213b">
[Figure 1]
## 9/12: First TA Meeting
We had our first meeting with our TA, Jason, and discussed our project as well as our concerns. Afterward, we researched microcontrollers and development boards to find a dev board that was USB 3.0 and MIPI 2.0 compatible. 

## 9/14: Project Proposal Wrap Up
In this meeting, we finished the project proposal and found our desired image sensor/microcontroller. We sent out the email requests for the datasheets and quotes.

## 9/17: Start Design Document
We began working on the design document, specifically the problem, solution, high level requirements, tolerance analysis, and ethics. 

## 9/21: Second TA Meeting/First meeting with TA and Professor Gruev
Finalized image sensor with Prof. Gruev and discussed design document, 3D modeling, and PCB design with TA. We continued working on the design document and began working on the PCB design.

## 9/24: PCB Design
Sourced all required components, but cannot order due to lack of CFOP number. Worked on PCB design after adding all components to KiCAD.

## 9/25: Splitting PCB components
We split up the components for the PCB design in order to speed up the process. Our device has three main components, the MCU, image sensor, and power/USB -- we split up each of the components among the three members of our group to finish by the following week. 

## 9/28: Wrapping up Design Document
In this meeting, we finished and submitted all necessary aspects for our design document including preliminary schematics. **INSERT PICTURES**

## 10/1: Cross checking PCB
Prior to this meeting, each member finished creating the schematic for their respective component, read all three datasheets, and looked at all other schematics. At this meeting, we cross-checked the schematics and any questions that arose during individual checking.

## 10/2: Design Review & Consolidating PCB
We had our official design review with Jason Zhang, David Null, and Professor Fliflet. Afterward, we combined our individual PCB schematics into one schematic and connected our components. **Insert picture** 

## 10/3: PCB Questions at Office Hours
Once our PCB was finalized amongst the members of our group, we attended office hours to ask questions that remained after consolidating. 

## 10/6: PCB Review
Attended the PCB review to ask more clarifying questions. Began routing our schematic and determined that 2/3 of us would continue routing before our next meeting while the third member began looking at code for our development board.

## 10/9: PCB
Met as a group to finalize the PCB design and components before meeting with the TA/Professor.

## 10/12: TA Meeting
Met with our TA to discuss PCBWay ordering. Following this meeting, we ordered our development board. 

## 10/16: Professor Gruev
In this meeting, our team met with Professor Gruev to discuss our PCB design and schematic before submitting a PCBWay order. He offered some suggestions that we began implementing following the meeting and will complete before the next meeting. 

## 10/18: Enclosure
I began learning Autodesk Fusion 360 in order to begin creating our 3D enclosure design. Aspects of the design will continue to be finalized later, but preliminarily we have a 2x2x7in enclosure with an opening on one end for the image sensor, an opening on the side for the USB connection, and a removable cap. **Insert Pictures**

## 10/19: PCB Sent to Head TA
We have our finalized PCB design that has passed the audit for PCBway. In this meeting, we consolidated all required components and emailed them to the head TA, Jason P., to order our PCB through turnkey with PCBWay. Additionally, we started finalizing some design aspects of our enclosure so that I may finish our first iteration in CAD.

## 10/23: 
We met with the head TA Jason P. as he had some questions regarding our order (which he will submit tomorrow). Additionally, we began experimenting with the development board and I finished one iteration of our enclosure design. **INSERT PICTURES**

## 10/26:
I finalized the iteration of the enclosure that we decided to print. Additionally, we were informed that the lead time for our PCB if we did turnkey assembly with PCBWay was around 28-30 days which meant we would not get our PCB until Thanksgiving break. We started exploring other options to get our PCB assembled, but in the end, we decided to just order our board, unassembled, and stencil from PCBWay and all our components through myECE to solder our board ourselves. 

## 11/2 
Today we had our weekly meeting with our TA. Following the meeting, our digikey parts and board arrived. We didn't have enough time today to solder our board, however, we set up a meeting with Jason P for tomorrow.

## 11/3: First attempt at soldering
With the help of Jason P, we soldered the frontside of our board using the reflow oven. The overall process took around 5 hours. Afterward, we went to Siebel Center for Design to print the first iteration of our enclosure. 

## 11/4:
Today I went back to SCD to pick up our 3D-printed enclosure. After sanding the components, I realized that the snap-fit components were slightly misaligned, so I adjusted the CAD file, reprinted the enclosure lid, waited for it to finish printing, and then sanded the component. The snap fits were properly aligned and the components did snap into place. 

## 11/5: 
Today, Amartya and I looked through the development board code to see what needed to be changed to adjust for our image sensor, the AR0330, compared to the one already on the dev board, the OV5640. Jason attempted soldering the backside of the PCB but the irons not in use weren't small enough. 

## 11/6
We were able to successfully solder the backside of the board. When we plugged it into a computer, it was detected as a device, but there was no voltage going through the board. Additionally, we spent numerous hours looking through the dev board code to build our own image, but we were unable to create our makefile, preventing us from making adjustments to the existing code. 

## 11/8:
We discovered that one of the problems with our board was with the clock. We removed all the 1.65 MOhm resistors on the clock and added pull-up resistors from an external breadboard. After doing both of these, we were able to get a clock signal on both the input and output pins, however, it was very noisy. We plugged it into the lab computers and got a power surge message.

## 11/9:
We had our TA meeting with Jazon Z and were joined by Zhongmin Z as well. Zhongmin gave our group a power meter to use for a few weeks so we can see if our board is drawing power and how much. At this point, we have two options that we can pursue: try and get our PCB to work or move forward with testing the dev board. For now, we are working on our board. We spent the rest of today resoldering a new board but the USB-C receptacle came off when we plugged it into the computer. Supplying external power, we also realized that the voltage regulator on the backside of the board was not working. While Jason and I were resoldering the board, Amartya was working on the dev board code. We can now make our own makefile and successfully upload it to the dev board. 

## 11/10:
Today we tried 3 different things to reattach the USB-C receptacle but none of them fully worked. We tried using the flux pen and applying heat through the heat gun, using solder paste and applying heat with the heat gun, and applying solder paste and putting the PCB back into the reflow oven. Surprisingly, putting the board back in the reflow oven fixed the regulator on the backside of the board. 

## 11/11:
Today, we tried applying solder paste to only one row of the usb pins, applied heat from the bottom of the board using the heat gun, and then used flux on the top row. This method seemed to work initially as the device drew power for short amount of time. Additionally, we realized that the USB only works in one direction which implied that one of the two usb pin rows was not properly soldered on. When plugging the device into Amartya's computer, the device was recognized as the same device as the development board since they use the same microcontroller. 

## 11/13:
Whenever we plugged our board into a computer, the board would heat up very quickly and we kept getting power surge messages, this led us to believe there was a short in the board. Using a USB-C cable that we had cut previously to expose the wires, we found that the short circuit impedance was around 16 ohms which was similar to what our board was reading; this confirmed that there was a short in the board. Jason and I removed components one by one and tested the impedance until we found all the components causing the short. It was primarily the voltage regulator on the backside of the board, one voltage regulator on the frontside (U5), as well as the USB mux. We began placing the components back onto the board using the heat gun and confirming that the impedance was still around 80K Ohms after each one. We didn't finish placing the components back on today. During that time, Amartya was able to get the dev board to work on MacOS and not just on Windows. 

## 11/14:
Today we placed the remaining components back onto the board. After we finished, the short was gone, we no longer got the power surge message on the computers, and all the LDOs were functioning. Unfortunately, the clock was still noisy and the lab computer was still unable to detect the device. 

## 11/15
We assumed that one reason the computer did not detect our device was due to the clock, so we experimented with different resistor values for the pull-up. Originally, we used 1k, however, we found that 100 ohms, 50 ohms, and 27-ohm resistors made the output waveform of the clock buffer look similar to the input waveform. We decided to solder the 27-ohm resistors from the output pins of the clock buffer to the output pin of a 1.8 V regulator to eliminate any noise/capacitance from the breadboard. Doing so stabilized the clock, but still did not allow the lab computer to detect the device. 

## 11/16: Testing Dev Board + Mock Demo + Breakthrough 
Today, we went into the basement of ECEB with Zhongmin to try and test the dev board's UV/NIR capabilities. Unfortunately, the dev board came with a filter already installed which prevented proper testing.
Unsure of what may be preventing the computer from detecting the device we poured through datasheets again. We realized that the clock buffer voltage was not the same as the VDDIO1 and CVDDQ voltages even though it was supposed to be according to the datasheet; so we cut the trace of the 3.3V regulator to the clock buffer and soldered on another resistor to make the input voltage 1.8V.
Following this, we had our mock demo in which Jason Z told us that if we could test NIR and UV with the dev board, we would be able to get the majority of the functionality points. 
After the mock demo, we continued to look through the data sheets and found a major issue with our board. The MCU we are using has 4 different boot mode options that are defined by 3 pins: PMODE[2:0]. To get the MCU to boot on USB, the pins needed to be set as F11, however, after crosschecking with our layout we realized ours were routed as 11F which corresponded with none of the boot options. Initially, we thought we would have to solder an entirely new board while bridging the P[1] and P[0] pins and cutting a trace to leave P[2] floating. The trace we needed to cut was on the backside of the board and after looking more at the datasheet, we decided to cut the trace on our current board which would set the boot mode to F1F which was I^2C, on failure USB enabled. Since we hadn't set any of the I^2C pins other than those necessary for MIPI, we were hopeful that USB would default and allow information to reach the MCU. After cutting the trace and plugging the device in, the computer recognized it and we were able to program it! With the dev board, after programming the device, it unenumerates as a USB device and re-enumerates as a camera; our PCB was unenumerated as a USB device but did not re-enumerate as a camera. 

## 11/17: Meeting with Professor Gruev
Today, we had a meeting with Professor Gruev to provide him with updates and potentially reassess the goals for the project. After speaking with him, we decided to try testing the dev board again. The filter already on the dev board was soldered on, so Professor Gruev removed it which allowed us to test the board using his filters'. After confirming with one filter that we could test, Professor Gruev told us to 3D print an encolure for the dev board that had an opening solely for the filters to be screwed in so that we could test without any external light coming in. The enclosure needs to sit 17.526mm from the top of the lens and have threads for the filters to screw in. Seeing as how we are all leaving for Thanksgiving break, I will create the CAD design over break, 3D print/adjust it next weekend, and resume dev board testing on the Monday we return from break. 
