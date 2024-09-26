Aim:
To design and simulate a seven-segment display driver using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment. The objective is to implement the logic that converts a 4-bit binary input into the corresponding 7-segment display output for the digits 0 to 9.

Apparatus Required
Vivado 2023.1
Computer system with a suitable operating system.

Procedure:

1)Launch Vivado 2023.1:

2)Open Vivado and create a new project.
Design the Verilog Code:

3)Write the Verilog code for the seven-segment display, defining the logic that maps a 4-bit binary input to the corresponding segments (a to g) of the display.
Create the Testbench:

4)Write a testbench to simulate the seven-segment display behavior. The testbench should apply various 4-bit input values and monitor the corresponding output on the seven-segment display.
Add the Verilog Files:

5)Add both the design module and the testbench in the Vivado project.
Run Simulation:

6)Run the behavioral simulation to verify the output. Ensure the seven-segment display behaves correctly for binary inputs 0000 to 1001 (decimal 0 to 9).
Observe the Waveforms:

7)Analyze the output waveforms in the simulation window, and verify that the correct segments light up for each digit.
Save and Document Results:

8)Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.

Diagram
![image](https://github.com/user-attachments/assets/d7ecb419-906e-4e3b-9b82-f86ced4f364a)


Verilog Code for Seven-Segment Display

// seven_segment_display.v
```
module bcd_behaviuoral(bcd,seg);
input [3:0]bcd;
output reg[6:0]seg;
always @ (bcd)
case(bcd)
     0:seg = 6'b0000001;
     1:seg = 6'b1001111;
     2:seg = 6'b0010010;
     3:seg = 6'b0000110;
     4:seg = 6'b1001100;
     5:seg = 6'b0100100;
     6:seg = 6'b0100000;
     7:seg = 6'b0001111;
     8:seg = 6'b0000000;
     9:seg = 6'b0000100;
default : seg=6'b1111111;
endcase
endmodule
```
           


Testbench for Seven-Segment Display:

// seven_segment_display_tb.v
`timescale 1ns / 1ps
```
module testbench;
  reg [3:0] bcd;        
  wire [6:0] seg;       

  
  bcd_behaviuoral uut (
    .bcd(bcd), 
    .seg(seg)
  );

  
  initial begin
    $monitor("Time=%0t | BCD=%b | 7-Segment Output=%b", $time, bcd, seg);

    
    bcd = 0; #10;
    bcd = 1; #10;
    bcd = 2; #10;
    bcd = 3; #10;
    bcd = 4; #10;
    bcd = 5; #10;
    bcd = 6; #10;
    bcd = 7; #10;
    bcd = 8; #10;
    bcd = 9; #10;

    
    bcd = 4'b1010; #10; 
    bcd = 4'b1111; #10;

    
    $finish;
  end
endmodule
```
OUTPUT:
![Screenshot 2024-09-26 164606](https://github.com/user-attachments/assets/f883f0b3-d686-4946-8c96-9bb4ec6e3336)




CONCLUSION:
In this experiment, a seven-segment display driver was successfully designed and simulated using Verilog HDL. The simulation results confirmed that the display correctly represented the digits 0 to 9 based on the 4-bit binary input. The testbench effectively verified the functionality of the seven-segment display by applying various input combinations and observing the corresponding segment outputs. This experiment highlights how Verilog HDL can be used to control hardware components like a seven-segment display in digital systems.
