# Warp_Verilog_UART_Tx
Here I describe the steps required to implement Warp Verilog development with PSoC 5LP

Materials needed:

- CY8CKIT-059 PSoC 5LP Prototyping kit
- USB TTL converter

# First step: create a new project

The next steps are the bread-and-butter because is the process of creation a PSoC project.
File > New > Project...
Select the target kit as our kit PSoC 5LP, select blank schematic and name the workspace.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/1.PNG)

Click finish.

# Second step: create a new component

On the left side of the creator there are some sections where the main project is being developed, the section source is the place where you can find the API files which use the microcontroller. Those are automatically generated so we do not need to worry about it.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/2.PNG)

Click on components and right click on the Project section, then add a new component

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/3.PNG)

Select between two options, you can start with empty symbol or a predefined by the wizard and then you must name the component you want to create.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/4.PNG)

You can use the Symbol Wizard because it only will fasten the process of building the block, an empty block starts with a blank sketch for full customizable blocks and the symbol wizard creates a generic the block but are quite the same.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/5.PNG)

In the Terminal name section add the pin names that the program will require. In this case I will introduce a clock input signal which will determine the baudrate in the UART block, then I added the Tx terminal.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/6.PNG)

Click Ok.

Now we have the component created. But I forgot to place the data bus which will determine the input data for the UART transmission. This can be done in the same page, just selecting the input pin button which is used to place manually pins into the block.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/7.PNG)

In that button you can determine the bit lenght, I want a data bus about 8 bits which will be displayed as a bus wire as D[7:0].

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/8.PNG)

Click Ok and now we have created the block successfully!

# Third step: Generate the verilog file

Right click in any space of the symbol page and select the option “Generate Verilog”, click on generate in the tab displayed and now we have generated the verilog file!

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/20.PNG)

# Fourth step: It is moment to code!

The autogeneration tool of PSoC creator generates the first draft of the Verilog file in such a way that you only need to implement the structures you need. In the section “your code goes here” you can start to code and implement any program it is capable of!

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/9.PNG)

Using some theory in UART communication I implemented the next following code for sending a 8 bit data over UART any time the data changes its value. Entire code (UART_verilog_exaple.v)

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/10.PNG)

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/11.PNG)

Now save code. You can use the fast command Ctrl + S inside of the component section and in the source too.

# Last step: build the design and implement the block

Go to the top design and now we can see the block we have already created in the Default tab .

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/12.PNG)

We can use the block and connect the required peripherals. 

In this example I am using a control register and an output pin to connect to the USB TTL converter and see the terminal. I used a 9.585 Khz clock to simulate a 9600 bits per second transmission due debugging conclusions.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/13.PNG)

Assign the pinout to the pin you want to connect the USB TTL converter and lets see the output.
For building the project click on build design.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/14.PNG)

If the code implemented fulfills the syntaxis of the Verilog file according to the Warp compliance and the technical refereces [1], everything should be ok.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/15.PNG)

For debuggin the UART transmitter I assigned two values to the status register

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/16.PNG)

And were successfully transmitted over 9600 baud Serial communication.

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/17.PNG)

It works flawlessly but there still things to improve. 

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/18.PNG)

![OFF](https://github.com/Miguelest07/Warp_Verilog_UART_Tx/blob/main/Images/19.PNG)

