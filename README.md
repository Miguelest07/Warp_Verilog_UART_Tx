# Warp_Verilog_UART_Tx
Here I describe the steps required to implement Warp Verilog development with PSoC 5LP

Materials needed:

- CY8CKIT-059 PSoC 5LP Prototyping kit
- USB TTL converter

# First step: create a new project

The next steps are the bread-and-butter because is the process of creation a PSoC project.
File > New > Project...
Select the target kit as our kit PSoC 5LP, select blank schematic and name the workspace.

![OFF](https://github.com/Miguelest07/STM32F1_ADXL345_DigitalFilter/blob/main/Images/1.PNG)

Click finish.

# Second step: create a new component

On the left side of the creator there are some sections where the main project is being developed, the section source is the place where you can find the API files which use the microcontroller. Those are automatically generated so we do not need to worry about it.

2

Click on components and right click on the Project section, then add a new component

3

Select between two options, you can start with empty symbol or a predefined by the wizard and then you must name the component you want to create.

4

You can use the Symbol Wizard because it only will fasten the process of building the block, an empty block starts with a blank sketch for full customizable blocks and the symbol wizard creates a generic the block but are quite the same.

5

In the Terminal name section add the pin names that the program will require. In this case I will introduce a clock input signal which will determine the baudrate in the UART block, then I added the Tx terminal.

6

Click Ok.

Now we have the component created. But I forgot to place the data bus which will determine the input data for the UART transmission. This can be done in the same page, just selecting the input pin button which is used to place manually pins into the block.

7

In that button you can determine the bit lenght, I want a data bus about 8 bits which will be displayed as a bus wire.

8

Click Ok and now we have created the block successfully!

# Third step: Generate the verilog file

Right click in any space of the symbol page and select the option “Generate Verilog”, click on generate in the tab displayed and now we have generated the verilog file!

# Fourth step: It is moment to code!

The autogeneration tool of PSoC creator generates the first draft of the Verilog file in such a way that you only need to implement the structures you need. In the section “your code goes here” you can start to code and implement any program it is capable of!

9

Using some theory in UART communication I implemented the next following code for sending a 8 bit data over UART any time the data changes its value. Entire code (UART_verilog_exaple.v)

10

Now save code. You can use the fast command Ctrl + S inside of the component section and in the source too.

# Last step: build the design and implement the block

Go to the top design and now we can see the block we have already created in the Default tab .

11

We can use the block and connect the required peripherals. 

In this example I am using a control register and an output pin to connect to the USB TTL converter and see the terminal. I used a 9.585 Khz clock to simulate a 9600 bits per second transmission due debugging conclusions.

12

Assign the pinout to the pin you want to connect the USB TTL converter and lets see the output.
For building the project click on build design.

13

If the code implemented fulfills the syntaxis of the Verilog file according to the Warp compliance and the technical refereces [1], everything should be ok.

14

For debuggin the UART transmitter I assigned two values to the status register

15

And were successfully transmitted over 9600 baud Serial communication.

16

17

