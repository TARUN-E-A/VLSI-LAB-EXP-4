**4.SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS**

**AIM:**
 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

**APPARATUS REQUIRED:**

Xilinx 14.7

Spartan6 FPGA
  
**PROCEDURE:**

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.


**SR FLIPFLOP:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

**VERILOG CODE:**

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

**OUTPUT:**

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/9a86ffd4-3f27-4c49-bee0-58ff38566d5e)

**JK FLIPFLOP:**

**LOGIC DIAAGRAM:**

![image](https://github.com/karanpro06/VLSI-LAB-EXP-4/assets/119782103/61ba7f5a-accd-496d-a65b-ebef34301d75)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

**VERILOG CODE:**

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

**OUTPUT:**

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/f19e8aee-627e-460f-8886-b07ea643c3fd)

**T FLIPFLOP:**

**LOGIC DIAGRA:**

![image](https://github.com/karanpro06/VLSI-LAB-EXP-4/assets/119782103/43dc6827-07e1-4e92-8e8a-ecc22ce0d6a3)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

**Verilog Code:**

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

**Verilog Code:**

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

**Output:**

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/751c1757-d9a8-4d9e-bce4-cac85e275bf6)

**COUNTER:**

**Updown Counter:**

**Logic Diagram:**

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/dd12585a-157f-4b6f-a0c3-b421bb52434c)

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

**Verilog Code:**

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

**Output:**

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/fedfede5-4ad6-46a1-a0ad-b90ae15eac1c)


**Mod-10 Counter:**

**Logic Diagram:**

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/3a4a4da2-7488-411d-8ea5-2e57c4fd942f)

**Verilog Code:**

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

**Output:**

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/c287bf47-4b86-40c1-b833-0b27feb602ec)

**Ripple Carry Counter:**

**Logic Diagram:**

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/129b1a22-407f-4f38-adff-b4dbf3595eb7)

![image](https://github.com/Dhinesh0024/VLSI-LAB-EXP-4/assets/160568927/fecad9d3-7f49-4c98-91f4-443803a60e37)



**Verilog Code:**

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

**Output:**

![image](https://github.com/TARUN-E-A/VLSI-LAB-EXP-4/assets/163630871/96dfc3fe-3ed9-42b9-85db-aa1a821bc9fa)


**RESULT:**

 Hence SR, JK, T, D - FLIPFLOP, COUNTER DESIGN are simulated and synthesised using Xilinx ISE.


