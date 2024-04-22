SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  
PROCEDURE:
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

VERILOG CODE
# ENCODER:
```
module encoder(d,a,b,c);
input [7:0]d;
output a,b,c;
or(a,d[4],d[5],d[6],d[7]);
or(b,d[2],d[3],d[6],d[7]);
or(c,d[1],d[3],d[5],d[7]);
endmodule
```
# DECODER:
```
module decoder_8(a,b,c,y);
input a,b,c; 
output[7:0]y; 
and gl(y[0],(~a),(~b),(~c)); 
and g2(y[1],(~a),(~b),(c)); 
and g3(y[2],(~a),(b),(~c));
and g4(y[3],(~a),(b),(c));
and g5(y[4],(a),(~b),(~c));
and g6(y[5],(a), (~b), (c));
and g7(y[6], (a), (b), (~c)); 
and g8(y[7], (a), (b), (c));
endmodule
```
# MULTIPLEXER:
```
verilog code 
module mux(s,c,a);
input [2:0]s;
input [7:0]a;
wire [7:0]w;
output c;
and(w[0],a[0],~s[2],~s[1],~s[0]);
and(w[1],a[1],~s[2],~s[1],s[0]);
and(w[2],a[2],~s[2],s[1],~s[0]);
and(w[3],a[3],~s[2],s[1],s[0]);
and(w[4],a[4],s[2],~s[1],~s[0]);
and(w[5],a[5],s[2],~s[1],s[0]);
and(w[6],a[6],s[2],s[1],~s[0]);
and(w[7],a[7],s[2],s[1],s[0]);
or (c,w[0],w[1],w[2],w[3],w[4],w[5],w[6],w[7]);
endmodule
```
# DEMULTIPLEXER:
module demux_8(s,a,y);
input [2:0]s;
input a;
output [7:0]y;
and(y[0],a,~s[2],~s[1],~s[0]);
and(y[1],a,~s[2],~s[1],s[0]);
and(y[2],a,~s[2],s[1],~s[0]);
and(y[3],a,~s[2],s[1],s[0]);
and(y[4],a,s[2],~s[1],~s[0]);
and(y[5],a,s[2],~s[1],s[0]);
and(y[6],a,s[2],s[1],~s[0]);
and(y[7],a,s[2],s[1],s[0]);
endmodule
```
# MAGNITUDE COMPARATOR:
```
module magcomp(a,b,l,g,e);
input [3:0]a,b;
output reg l,g,e;
always @(*)
begin
if(a>b)
begin
     l=1'b0;
     g=1'b1;
     e=1'b0;
end
else if(a<b)
begin
     l=1'b1;
     g=1'b0;
     e=1'b0;
end
else
begin
     l=1'b0;
     g=1'b0;
     e=1'b1;
end
end
endmodule
```

OUTPUT WAVEFORM:
# ENCODER:

![image](https://github.com/sabarezz/VLSI-LAB-EXP-2/assets/165630121/8dee1ce5-687b-478c-b682-6059bfa8705d)



# DECODER:

![image](https://github.com/sabarezz/VLSI-LAB-EXP-2/assets/165630121/8c36c1b4-3a6e-4d09-8cce-4fe8ddb9ed33)


# MULTIPLEXER:

![image](https://github.com/sabarezz/VLSI-LAB-EXP-2/assets/165630121/70c0ff73-c1d1-4014-a9a0-8926b9c8a264)




# DEMULTIPLEXER:

![image](https://github.com/sabarezz/VLSI-LAB-EXP-2/assets/165630121/06bea170-162b-46b7-ba7b-1cd04bad8eba)



# MAGNITUDE COMPARATOR:

![image](https://github.com/sabarezz/VLSI-LAB-EXP-2/assets/165630121/85ba5c35-ed4a-47eb-9f77-71d8f8b85bf5)



RESULT
HENCE ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE is simulated and synthesised.

