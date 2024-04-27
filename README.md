## SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

## AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

## APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA
  
## PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.


## SR FLIPFLOP:

### Logic Diagram:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

### Verilog Code:

~~~
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
~~~

### Output:

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/9a86ffd4-3f27-4c49-bee0-58ff38566d5e)



## JK FLIPFLOP:

### Logic Diagram:
![image](https://github.com/karanpro06/VLSI-LAB-EXP-4/assets/119782103/61ba7f5a-accd-496d-a65b-ebef34301d75)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

### Verilog Code:

~~~
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
~~~

### Output:

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/f19e8aee-627e-460f-8886-b07ea643c3fd)


## T FLIPFLOP:

### Logic Diagram:
![image](https://github.com/karanpro06/VLSI-LAB-EXP-4/assets/119782103/43dc6827-07e1-4e92-8e8a-ecc22ce0d6a3)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

### Verilog Code:

~~~
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
~~~

### Output:

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/e6f917a8-5b45-4dca-8d28-2b8876a40367)


## D FLIPFLOP:

### Logic Diagram:
![image](https://github.com/karanpro06/VLSI-LAB-EXP-4/assets/119782103/8e827351-3ef8-4a51-9379-1e3baae4baae)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

### Verilog Code:

~~~
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
~~~

### Output:

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/751c1757-d9a8-4d9e-bce4-cac85e275bf6)

## COUNTER:

## Updown Counter:

### Logic Diagram:

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/dd12585a-157f-4b6f-a0c3-b421bb52434c)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

### Verilog Code:

~~~
module udc(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule
~~~

### Output:

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/fedfede5-4ad6-46a1-a0ad-b90ae15eac1c)


## Mod-10 Counter:

### Logic Diagram:

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/3a4a4da2-7488-411d-8ea5-2e57c4fd942f)


### Verilog Code:

~~~
module mod10(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
~~~

### Output:

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/c287bf47-4b86-40c1-b833-0b27feb602ec)

## Ripple Carry Counter:

### Logic Diagram:

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/129b1a22-407f-4f38-adff-b4dbf3595eb7)


![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/fecad9d3-7f49-4c98-91f4-443803a60e37)



### Verilog Code:

~~~
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule

module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always @(posedge clk or posedge rst)
begin
if (rst)
q=1'b0;
else 
q=d;
end
endmodule

module rcc(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tf1(q[0],clk,rst);
tff tf2(q[1],q[0],rst);
tff tf3(q[2],q[1],rst);
tff tf4(q[3],q[2],rst);
endmodule
~~~

### Output:

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/96dfc3fe-3ed9-42b9-85db-aa1a821bc9fa)


## RESULT:
 Hence SR, JK, T, D - FLIPFLOP, COUNTER DESIGN are simulated and synthesised using Xilinx ISE.


