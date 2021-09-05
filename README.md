# Verilog-RS232-Synch-UART-RS232-Debugger-and-PC-host-RS232-Hex-editor
Verilog RS232 Synch-UART &amp; RS232 Debugger and PC host RS232 Hex-editor.

This is a Verilog core which contains a PC compatible high speed Synchronous RS-232 UART and RS232 debugger server and real-time PC client software hex-editor with 4 utility 8 bit input ports and 4 utility 8 bit output ports.

The Verilog source is well documented in code.  See the original project page from Nov 25, 2019 here:
https://www.eevblog.com/forum/fpga/verilog-rs232-uart-and-rs232-debugger-source-code-and-educational-tutorial/

There are 3 pieces:

1) The ' SYNC_RS232_UART.v ' : A synchronizing RS232 transceiver.  The 'synchronizing' transmitter with the receiver is crucial when interfacing with a PC as high speed full duplex communication require that the bit and word timing of serial data coming into the PC matches the clock and phase of the data the PC may be transmitting out at the same time.  Many simple example Verilog RS232 UARTs arent capable of this.  Read attached source code and see attached illustration to show you an example setup where my transmitter aligns itself to a received RS232 serial signal with a slightly different baud rate.


2) The ' RS232_Debugger.v ' : A Verilog module which uses the SYNC_RS232_UART.v, has an RS232 RXD input and TXD output.  It also has a memory address output and 8 bit memory data input and output with a memory read request and memory write enable.  This module also provides a reset output, 4 utility 8 bit output ports and 4 utility 8 bit input ports.  Once again, everything is documented in the available 'RS232_Debugger.v' source code and I'm here to answer questions.


3) The ' RS232_Debugger.exe ' Viewer / HEX editor software.  (For now, I haven't included the source code for this one, give me a week to clean it up first, though, it is fully functional.)  The software offers real-time viewing and editing of the user configured memory size set in the RS232_Debugger.v's memory address size parameter while also continuously displaying the values of the 4 utility 8 bit input ports as well as being able to set the values of the 4 utility 8 bit output ports.  When the RS232 com port is closed, the RS232_Debugger.exe functions as a stand alone HEX / ASCII file editor which can edit up to 1 megabyte files.


The Verilog code was written using pure synchronous logic.  No fancy async-reset/presets, no S/R, J-K flipflops.  These examples should easily integrate into any vendor's FPGAs EDA tool platform.  If anyone out there has success, let us know.
