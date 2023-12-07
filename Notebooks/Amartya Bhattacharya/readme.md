# Amartya Bhattacharya ECE 445 Lab Notebook

## 9/11
- Inquired into quotes for per-unit cost and lead time for camera module
- Researched potential microcontrollers, fitting them against specific requirements
- Drafted project proposal
- Set up git repo for lab notebook

## 9/12
- First meeting with TA, Jason Zhang
- Spoke about block diagram and tolerance requirements
- Reviewed project proposal

## 9/14
- Finished writing up project proposal
- Met with Professor Gruev to discuss potential component selections
- Sony IMX487 just not possible
- Revised what we thought we needed with new, slightly looser specifications
- Image sensor selection was far too expensive, learned that some degree of multispectral sensitivity can be achieved with almost any CMOS sensor
- BGA/QFN components might be impossible/difficult to hand-solder

## 9/21
- Met with Professor Gruev to discuss scheduling goals and component selections
- AR0330 from OnSemi might be suitable
- Waiting on manufacturer NDAs to be signed before we can move forward with data sheet review
- Hopefully this can coincide with the CFOP arrival, to order parts ASAP
- 3D print vs. ECE shop, 3D print preferred

## 9/24
- Finalizing component selections
- Started schematic design
- I took image sensor and associated voltage regulators
- Jason took USB C connections and associated peripheral ICs
- Isha took MCU
- Once schematics are ready we can start design doc

## 9/28
- Design document submitted
- Met with Professor Gruev to discuss PCB ordering
- CFOP still in question
- Supply shop preferred before Digikey
- Jason Paximadas said we might be able to rely on PCBWay to assemble board
- Need to pass audit first
- Will send Prof. Gruev datasheets and schematics for review

## 10/02
- Cross checked each other's schematics
- <img width="376" alt="Screenshot 2023-12-07 at 1 08 30 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/b1bd290d-35a8-4b1c-b640-50d043a9c91f">
- <img width="519" alt="Screenshot 2023-12-07 at 1 07 19 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/ebb2343a-a277-42d0-aa55-0c2fc142d351">
- <img width="607" alt="Screenshot 2023-12-07 at 1 07 39 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/000bcdb3-dd17-4cf7-bda8-6565a1bc300d">
- <img width="372" alt="Screenshot 2023-12-07 at 1 07 57 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/83c4ee36-e1ca-4edc-85e5-2e7df65aad9f">
- <img width="274" alt="Screenshot 2023-12-07 at 1 08 14 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/b4b5479f-85a0-43d2-a70e-fe6a524134e1">

## 10/03
- Went to design review, got a bunch of questions answered, but also raised some new questions
- Board physics, interference possibility hadn't been considered

## 10/06
- Went to PCB review, need to figure out board layer count, stackup order, and trace geometries; Jason taking the lead on this
- Doing research on Python or C to process RAW10/12 image input data
- Might need to have some calculation to convert the raw data into 3 separate spectral streams
- https://www.hindawi.com/journals/jece/2013/908906/
- https://www.sciencedirect.com/topics/engineering/spectral-decomposition

## 10/07
- Jason and Isha taking the lead with PCB routing
- Writing some preliminary C code to test some spectral decomposition algorithm ideas, still very very rough stage, using lots of dummy values
- ```
// Function to unmix RGB values into UV, NIR, and VIS components
void unmix_spectra(int R, int G, int B, float *UV, float *NIR, float *VIS) {
    // Dummy values based on quantum efficiency curves
    // Needs to be updated with actual sensor data
    float coef_R[3] = {0.2, 0.5, 0.3};
    float coef_G[3] = {0.1, 0.6, 0.3};
    float coef_B[3] = {0.1, 0.2, 0.7};

    // Unmixing using the coefficients
    *UV  = coef_R[0] * R + coef_G[0] * G + coef_B[0] * B;
    *NIR = coef_R[1] * R + coef_G[1] * G + coef_B[1] * B;
    *VIS = coef_R[2] * R + coef_G[2] * G + coef_B[2] * B;
}

// Main function for testing
int main() {
    int R = 120, G = 130, B = 140;
    float UV, NIR, VIS;

    unmix_spectra(R, G, B, &UV, &NIR, &VIS);

    printf("UV: %f, NIR: %f, VIS: %f\n", UV, NIR, VIS);

    return 0;
}
```
- Generating a dataset to potentially test on, using color and QE values from the image sensor datasheet
- ```
#define WIDTH 2304
#define HEIGHT 1296
#define MAX_RGB_VALUE 4095  // 12-bit

typedef struct {
    int R;
    int G;
    int B;
} Pixel;

void generate_dataset(Pixel dataset[WIDTH][HEIGHT]) {
    for (int x = 0; x < WIDTH; ++x) {
        for (int y = 0; y < HEIGHT; ++y) {
            // Simulate RGB values (simple version)
            dataset[x][y].R = rand() % MAX_RGB_VALUE;
            dataset[x][y].G = rand() % MAX_RGB_VALUE;
            dataset[x][y].B = rand() % MAX_RGB_VALUE;
        }
    }
}

int main() {
    Pixel dataset[WIDTH][HEIGHT];
    generate_dataset(dataset);

    return 0;
}
```
- Continued trying to iterate and test, but proving frustrating. Might not be the best approach

## 10/09
- Wrote up the BOM for the PCBWay audit
- Finalized routing
- Submited for audit

## 10/10
- Audit failed
- Modified and resubmitted
- Need to understand DRC better

## 10/16
- Met with Professor Gruev to discuss board review
- 4 mounting holes instead of 2 for better stability
- Need to be aware of overlapping power planes - analog vs digital power
- Need to be aware of overlapping power and data planes
- Can use multiple layers to distribute across the board to minimize overlap, not using board space efficiently as is
- Leads to cross-talk, interference, noise
- Wide traces for power, thin traces for data
- Need to have polar data lines exactly equal length
- Keep USB connector close to edge
- Potentially use an orthogonal mount to route USB cable through enclosure handle
- Schematic might have some issues we weren't cognizant of
- Might need screw holes by the sensor to attach lens directly to board

## 10/17
- Final PCB design: <img width="272" alt="Screenshot 2023-12-07 at 1 25 37 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/656786e4-8c31-4f6b-98cf-3952d0fdf3cf">
- <img width="574" alt="Screenshot 2023-12-07 at 1 25 53 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/aa6f3664-991e-4bcc-a10d-aa0c37b98d90">

## 10/19
- Emailed Jason Paximadas for PCB order
- Started looking at dev board SDK now that it's here
- Documentation seems sparse and a little old
- https://www.e-consystems.com/CX3-Reference-Design-Kit.asp
- <img width="661" alt="Screenshot 2023-12-07 at 1 28 02 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/b7268dee-f04d-4cf0-9b4e-069f06a1cd47">
- Looking directly into MCU SDK instead
- Having trouble setting it up on MacOS, even though it is supposedly compatible
- Also having trouble accessing application notes, getting service unable - dns failure error
- Opened support thread with their technical staff

## 10/20
- Researching boot process for CYUSB MCU
- Still not able to access code examples and application notes and programmer's data sheet

## 10/23
- Met with Jason Paximadas to better undertand PCB order logistics
- Looking into MIPI-USB FIFO code examples to better understand CX3 interface
- Data needs to come in from sensor over MIPI, and MCU needs to format and send over USB

## 10/24
- Dev board SDK is useless, it's less for programming and re-programming the board as it is to just get a video from the camera
- Need to be able to recreate that functionality by ourselves


## 10/26
- PCBWay suddenly updated their delivery ETA to 30 days, even though before it was 11
- Even then we weren't sure if that included sourcing or not, and it might've been dicey
- Need to look into alternatives
- Suggestions have included JLCPCB and 4PCB, because USA options might be faster, albeit more expensive
- Reached out to a few different manufacturers and requested quotes
- They all said 72hrs just to get a lead time/price quote...
- Might have order components directly through CFOP and hand-solder using reflow oven
- Either way PCB won't arrive until very close to mock demo date
- Need to email Professor Gruev and ask about testing and if we need special access
- Also need to figure out how 3D printing at SCD will work re. CFOP
- Also need to figure out how to program CX3 MCU to work with different image sensor than what is included on the dev board
- Not apparent from data sheets
- Still not able to access application notes, tech support is being unresponsive

## 10/30
- Ordered components, PCB, and stencil
- Not able to open included Eclipse IDE in SDK
- Crashes immediately upon opening, despite correct Java versions, etc. installed
- There is a newer version of the SDK available (1.3.5), but when I try to download it, it says error 403: forbidden
- Also there is a file that is supposed to be in the SDK called cyu3imagesensor.c that supposedly contains helper functions for setting up different image sensors, but it literally does not exist in my SDK folder

## 11/03
- Soldered PCB using stencil and solder paste and reflow oven, with extensive help from Jason Paximadas
- <img width="333" alt="Screenshot 2023-12-07 at 1 56 12 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/7bf03601-c915-4269-bf84-0f811a16305e">
- Downloaded Windows over Bootcamp, and SDK seems to work better in windows
- 1.3.5 download issue fixed, Eclipse IDE issue fixed, cyu3imagesensor.c issue fixed
- But now very confused about driver resell and signature changing
- Not able to flash dev board, as computer is not able to modify the .inf file for the driver
- Following the instructions in the CyUSB.pdf. In section 2, ‘Modifying CyUSB3.INF’, it states to locate a section in the .inf file and 'change VID_XXXX to contain the hexadecimal value of the VendorID for the device, and change the PID_XXXX to contain the hexadecimal value of the ProductID for the device.’
- Not sure where to find these vendor and product IDs
- When I connect the dev board to my PC’s USB port, and go to Device Manager, I see the e-con CX3 RDK with OV5640 under the Camera section, and in the Details -> Device instance path, it lists ‘USB\VID_2560&PID_D051&MI_00\6&30F2AD37&0&0000.’
- But reading on the Infineon community forums, it seems that this is a random string generated by Windows...

## 11/04
- Identified some issues with PCB, lots of clock noise
- Some resistors in series that had to be removed, and pull up resistors added to clock buffer
- LDOs not working

## 11/05
- Continuing MCU SDK research on my part
- https://www.infineon.com/cms/en/design-support/tools/sdk/usb-controllers-sdk/ez-usb-fx3-software-development-kit/?tab=~%27all#!designsupport
- https://www.infineon.com/cms/en/design-support/software/code-examples/usb-controllers-code-examples/usb-super-speed-code-examples/#!documents
- https://www.infineon.com/dgdl/Infineon-AN90369_How_to_Interface_a_MIPI_CSI-2_Image_Sensor_With_EZ-USB_CX3-ApplicationNotes-v05_00-EN.pdf?fileId=8ac78c8c7cdc391c017d073e56bf6257
- <img width="625" alt="Screenshot 2023-12-07 at 1 40 35 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/c89de994-745e-4bf5-90df-5147a68dc2d0">
- <img width="625" alt="Screenshot 2023-12-07 at 1 40 51 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/f488537e-0d2b-46b7-b230-4b1557ade380">
- <img width="281" alt="Screenshot 2023-12-07 at 1 44 05 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/3afed9a7-dc1f-4743-bdcd-72822c9d7386">
- Notable files:
/FX3_SDK_1.3.4_MacOS/cyfx3sdk
| --- /doc/firmware/FX3APIGuide.pdf
| ---/firmware/cx3_examples/cycx3_uvc_ov5640
	|---cycx3_uvc.c: implements a USB UVC 1.1 compliant video camera on the CX3 using an Omnivision OV5640 image sensor
	|---cycx3_uvcdscr.c: contains the UVC enumeration data
	|---cyfxtx.c: provides the application specific exception handlers and memory allocation routines
- cyfxtx.c : No changes needed. Use this file as provided with the project.
It contains the variables that the RTOS and the CX3 API library use for memory mapping and the functions
that the CX3 API library uses for memory management.
- cycx3_uvc.c : Main source file for the UVC application. Changes are needed when modifying the code to support controls
such as brightness, PTZ, etc., and when modifying to add support for different video streaming modes, or if you’re using another sensor. 
Contains the following functions:
main: Initializes the CX3 device, sets up caches, configures the CX3 I/Os, and starts the RTOS kernel.
CyFxApplicationDefine: Defines the two application threads that are executed by the RTOS.
CyCx3AppThread_Entry: This function is executed by the first application thread. It calls the initialization functions for CX3’s internal blocks, enumerates the device, and then handles the device suspend and frame completion tasks.
CyCx3AppMipiErrorThread: This function is executed by the second application thread. It waits for events that indicate errors in the MIPI CSI-2 controller and then reads them using CyU3PMipicsiGetErrors.
CyCx3AppDebugInit: Initializes CX3’s UART block for printing debug messages
CyCx3AppInit: Initializes CX3’s GPIO block, Processor Block or PIB (GPIF II is a part of PIB), I2C/CCI interface, MIPI CSI-2 Rx interface and the sensor (sets configuration to 1080p 30fps in SuperSpeed mode). It also initializes the USB block for enumeration, and endpoint configuration memory for USB transfers and creates DMA channel configuration for data transfers from two GPIF II sockets to the USB sockets.
CyCx3AppGpifCB: Handles CPU interrupts generated from the GPIF II state machine
CyCx3AppDmaCallback: Keeps track of the outgoing video data from CX3 to the Host. It adds the header to the image data and can signal the first application thread to indicate frame completion.
CyCx3AppUSBSetupCB: Handles all control requests sent by the Host, sets events indicating that UVC-specific requests have been received from the Host, and detects when streaming is stopped. It also handles the UVC class-specific probe and commit control requests that are required to start and stop video streaming.
CyCx3AppUSBEventCB: Handles USB events such as suspend, cable disconnect, reset, and resume.
CyCx3AppErrorHandler: Error handler function. This is a placeholder function for you to implement
error handling if necessary.
CyCx3AppAddHeader: Adds a UVC header to the video data during active streaming.
- cycx3_uvcdscr.c : Contains the USB enumeration Descriptors for the UVC application. This file needs to be changed if the
frame rate, image resolution, bit depth, or supported video controls need to be changed. The UVC
specification has all the required details.
- cycx3_uvc.h : Contains switches to modify the application behavior to turn ON/OFF the debug prints for frame counts and
the MIPI error thread.
Contains constants that are used in common by the cycx3_uvc.c and cycx3_uvcdscr.c files.
- cyfx_gcc_startup.s : This assembly source file contains the CX3 CPU startup code. It has functions that set up the stacks and
interrupt vectors.
No changes needed.

## 11/06
- Soldered second board, first one had too many issues
- No voltage output when plugging in
- Board getting very hot to the touch
- Pull up resistors soldered directly onto board
- <img width="212" alt="Screenshot 2023-12-07 at 1 55 51 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/f851b476-9106-455d-8eca-092f44fbf60a">


## 11/08
- Adaptations required for AR0330CM image sensor:
- For other image sensors, the cyu3imagesensor.c file has a few helper functions that can be used to configure the image sensor. The image sensor is configured using CX3’s I2C master block. SensorWrite2B, SensorWrite, SensorRead2B, and SensorRead functions in the cyu3imagesensor.c file can be used to write and read image sensor configuration over I2C. The SensorWrite2B and SensorWrite functions call the CyU3PI2cTransmitBytes standard API to write data to the image sensor. The SensorRead2B and SensorRead functions call the CyU3PI2cReceiveBytes standard API to read data from the image sensor. For more details on these APIs, refer to the FX3 SDK API Guide.
- Faulty mux resoldered
- USB C connector not sitting stably on the board

## 11/13
- Heat problem is a short on the board
- Used breakout board to probe power and resistance across the board
- Removed components one by one, testing in between
- Faulty LDO on back of board removed and resoldered; impedance back to normal
- Clock still noisy

## 11/14
- Having a new problem now with the PCB not being recognized by computer
- Might be an electrical issue, might be a driver issue
- PCB gets recognized by Device Manager, but when I try to assign the correct device driver using the correct cyusb3.inf file as directed in the CyUSB.pdf guide in Cypress/EZ-USB FX3 SDK/1.3/driver folder, I get this error: "Windows encountered a problem installing the drivers for your device: Windows found drivers for your device but encountered an error while attempting to install them. -> Cypress FX3 USB BootLoader Device -> This device cannot start. (Code 10). If you know the manufacturer of your device, you can visit their website and check the support section for drivers."
- Need to better understand the driver resell process, instructions in data sheet aren't very clear. They're also written for Windows Vista, so that might explain part of the issue.

## 11/16
- When I initially plug in my pcb, and go to the Hardware Ids property in the Details tab in Windows Device Manager, it shows up as a USB Root Hub (USB 3.0): USB\ROOT_HUB30&VID8086&PID15EC&REV0006
- But this doesn't seem correct, because since I'm using the exact same microcontroller as on the development board (which enumerates correctly, as the following Hardware Id: USB\VID_04B4&PID_00F3&REV_0100)
- Expected that the VID and PID would be the same, might be a wrong assumption?
- Electrically board seems to be sound, but MCU might have been configured in the wrong boot mode. This would explain the driver issues as well
- Cut a trace on the board to switch it to I2C boot mode, which reverts to USB on failure (F1F). All I2C pins are floating on our board, so hopefully this should work
- Now, I can get the PCB to be recognized by the computer, and try to flash it with the firmware. But it unenumerates as a USB device (correct behavior) but then doesn't re-enumerate as a USB camera (wrong behavior)
- https://www.infineon.com/dgdl/Infineon-AN76405_-EZ-USB_FX3_FX3S_boot_options-ApplicationNotes-v12_00-EN.pdf?fileId=8ac78c8c7cdc391c017d0739984f5e27&utm_source=cypress&utm_medium=referral&utm_campaign=202110_globe_en_all_integration-application_note
- Could be because PCB is enumrating as a USB 2.0 device, as per Section 6.1 of AN76405: I2C EEPROM boot with USB fallback: "In case of USB boot, the bootloader supports only USB 2.0. USB 3.0 is not supported." This might be a problem.
- Met with Zhongmin to test the dev board firmware in Professor Gruev's Biosensors Lab
- Dev board camera shows absolutely no IR sensitivity...

## 11/17
- Met with Professor Gruev, he explained our dev board lens might have an IR cut filter
- Helped us remove the filter, showed us simple IR sensitivity test using iPhone Face ID IR blaster showing up in dev board sensor
- Figuring out image sensor register configurations for our sensor
- Research and guesses (might be wrong):
- Register configuration
- Set R0x3152=0xA114 to configure the internal settings
- Set R0x304A=0x0070 to start the internal settings
- Wait 150k EXTCLK periods
- Configure PLL, output, and image settings to desired values, and wait 1ms for PLL to lock
- Set R0x301A[2]=1
- Enable the serial (MIPI or HiSPi) interface by setting “parallel_en” (R0x301A[7]) to “0” and “smia_serial_dis” (R0x301A[12]) to “1”
- R0x31AE to 0x0204
- R0x31AC to 0x0808
- Check image sensor data sheet page 28 “serial configuration”
- <img width="525" alt="Screenshot 2023-12-07 at 2 07 29 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/7017a539-bd6f-43b0-b540-e4b68e5fa87e">
- Table 27/28 on page 24 of image sensor data sheet

## 11/24
- Since PCB is enumerating as a USB 2.0 device, we tried flashing it with USB 2.0 firmware. It worked, we verified the results with the dev board
- <img width="203" alt="Screenshot 2023-12-07 at 2 08 18 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/41d0b50c-8702-47ac-ab06-cceed5ba4130">
- ^ Expected pink and green pattern

## 11/25
- Isha designed dev board enclosure that has a thread compatible with C mount lens
- <img width="695" alt="Screenshot 2023-12-07 at 2 09 10 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/b12c7150-9041-46c6-a9f9-b20468f0e022">
- Need to get this printed ASAP

## 11/28
- Tested 3D printed enclosure in biosensors lab, able to 'see' the fluorophore - IR sensitivity confirmed!
- <img width="166" alt="Screenshot 2023-12-07 at 2 10 10 PM" src="https://github.com/JasonDJung/ECE-445-NOTEBOOK/assets/23287143/474e1001-ceaa-4616-bb99-f5a2932e74ba">

## 11/29
- Final demo went well

## 11/30
- Prototype dev board enclosure didn't print correctly, getting it remeasured, redesigned, and reprinted

## 12/02 onwards
- Working on final presentation and report, practice runs, etc.

# 12/05
- Final presentation went well
- Submitted final report
- Recorded extra credit video
- Submitted video
- CAD enclosure now fits correctly, ready to hand over to Professor Gruev
