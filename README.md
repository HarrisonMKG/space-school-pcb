## Description

The goal of this lab will be taking previous circuit theory and schematic knowledge and turning it into a PCB layout. The lab will be using the Electrical computer-aided design (ECAD) software [Altium](https://www.altium.com/)

![[Pasted image 20231102211420.png]]
## Pre-Lab

Download and install Altium designer (this is a pre-requisite and should be done BEFORE the lab). Since space school member are students of Queen's University they will be able to get a lisense for free from [Altium Education](https://www.altium.com/education/student-licenses)

## During Lab

Start a new project by doing `File>New>Project` and name it something generic eg. “my_tosat”
![[Pasted image 20231103165545.png]]
### Schematic - Searching for Parts 
In the new project select `Source Documenets> Sheet1` for your schematic view. You should be presented with the view as seen below:
![[Pasted image 20231103165515.png]]
![[Pasted image 20231103165208.png]]

Our circuit requires specific ICs in order to work correctly. Due to this, there are specific pin-out and sizing constraints we must follow in order to make sure the theoretical design matches the actual implementation. 

To help us adhere to these constraints within our design phase, we need to use the actual model of the component within Altium. We can find majority of the components we need for development within the "Manufacturer Part Search" on tool bar on the right hand side of the screen.
![[Pasted image 20231103112800.png]]
From here, we can search for a component, and then place it within our schematic.

For this example, we will search and place the following:
- tmp36 (Temperature Sensor)
- SparkFun Logic Level Converter - Bi-Directional (Logic Level Converter)

![[Pasted image 20231103113038.png]]
![[Pasted image 20231103112937.png]]
### Schematic - Importing Files
This project will need several component not normally found in Altium so we will need to import them. The files you need for this are present within this repository within the "resources" folder. These include:
- Arudino Nano Every(ABX00028.IntLib)
- SD Card Reader (MICROSD_SPI_OR_SDIO_CARD.IntLib)

Drag each of these files into Altium and a window below should pop up where you want to select "Import".
![[Pasted image 20231102211819.png]]
Now you should have access to the schematic and layout of the component you dragged into Altium. To view the schematic, open up the components section and on the right hand side and click the drop down menu and select your component. 

![[Pasted image 20231103103613.png]]
An item show show up and you can drag it into your schematic view.
![[Pasted image 20231103111511.png]]
Repeat the steps above for the SD Card reader.

### Schematic - Nomenclature
For better readiblity of the schematic, it is important to keep the names of your components relevant. To do this double click on the component to change properties of it's nomenclature. 

For this example, change:
- the name of "ABX00028" to something more readable like, “ARDUINO NANO EVERY” and change U? to U1
![[Pasted image 20231103113955.png]]
- Change BOB-12009 to something more readable like, “LOGIC LEVEL CONVERTER” and U? to U2
![[Pasted image 20231103114050.png]]

- Change "MICROSD_SPI_OR_SDIO_CARD" to "SD CARD" and U? to U3
![[Pasted image 20231103151920.png]]
- Change "TMP36GT9Z" to "TMP36" and change U? to U4
![[Pasted image 20231103152622.png]]

### Schematic - Wiring
Now it is time to create the actual electrical connections for the circuit. To create a wire press (Ctrl+W) and click where you would like to make a connection. To create grounds within the circuits select the ground icon on your tool bar.
![[Pasted image 20231103154919.png]]
Place this ground close to your Arduino Nano Every by clicking. Connect this ground symbol to the GND on the component by using a wire, this should look something like this:
![[Pasted image 20231103154850.png]]
Do this for all other components in the schematic.

Now, we want to have the same electrical functionality as the schematic below so copy how the pins are connected. **NOTE: Look at the LABEL of the pin not where it is on the schematic for the connection!** To do this we will copy the connections from our original schematic.
![[Pasted image 20231103152419.png]]

In addition to this, we also have the temperature sensor to connect. For this connect the following:

| TMP36 | Arduino Nano Every |
| ---- | ---- |
|  VOUT  |  A1 |
| +VS  | +5V |

The final product should look something like the image below:
![[Pasted image 20231103160511.png]]


### Layout - Transform Schematic into Layout
Now you are ready to take on the layout of the actual PCB. Update you PCB document, to do this click on `Design>Update PCB Document` in the tool bar
![[Pasted image 20231103161057.png]]
You will be greeted with this screen detailing your many errors.... Ignore them and press `Execute Changes`!
![[Pasted image 20231103161158.png]]
Now you will be met with the screen below showing the PCB and all the components you need to place on it. **Note: The TMP36 sensor is missing as it was added to the design later**
![[Pasted image 20231103161253.png]]
### Layout - Size of PCB
Press `1` to enter board planning mode. After we want to change the dimensions of the PCB so click `Design>Edit Board Shape`.  We will reshape the dimensions to be **X** by **Y**
![[Pasted image 20231103161522.png]]
### Layout - Routing
Press `2` to switch back to layout mode and move all the components to the center of the board. This can be seen below:
![[Pasted image 20231103163702.png]]
As you can see some of our nets cross so we will have to route our connections both on the top of the PCB and on the bottom to avoid these collisions.
![[Pasted image 20231103163756.png]]

First, we will route on the bottom layer so select it like so:
![[Pasted image 20231103163907.png]]
Now, hit `Ctrl+W` to begin routing your connections. Plan out what will go on the top and bottom to have the easiest time routing. Your bottom connections should look something like this.
![[Pasted image 20231103164033.png]]
Hit `ESC` to stop routing and switch from the bottom layer to the top.
![[Pasted image 20231103164109.png]]
Now route the rest of your connections like before **Note: If you have issues will collisions do no be afraid to go back to the bottom layer and reroute things.** This should look something like this:
![[Pasted image 20231103164252.png]]
With the temperature sensor the final product should look like this:
![[Pasted image 20231103164452.png]]
### Layout - Silkscreen
Now it is time to add your name(s) to the PCB! 

Select the `Top Overlay` layer
![[Pasted image 20231103164607.png]]
Now click on the text button to add you name and the name of your PCB
![[Pasted image 20231103164637.png]]
![[Pasted image 20231103164706.png]]
Now, we need to add branding to show off how cool the team is! Download the image provided in the repository of the QSET logo. Right Click and select `Place>Graphics` and select the QSET logo:
![[Pasted image 20231103164920.png]]
![[Pasted image 20231103164926.png]]
Tada, you now have a PCB that's final product should look something like below:
![[Pasted image 20231103164534.png]]
Press `3` for a cool 3D view look!
![[Pasted image 20231103165032.png]]
### Fabrication - Generate Gerber Files
Gerber files are what we need to give the manufacturer in order to make our PCB. To create a gerber files go to the PCB layout and then select `File>Fabrication Outputs>Gerber Files` and you will be greeted with this:
![[Pasted image 20231103170149.png]]
Hit `Ctrl+S` to save the file and then navigate to your project folder and find your folder named 'Project Outputs'. Right click on it Zip it:
