# EXP 5: 32 Bit ALU-Synthesize the Gate Level Netlist and tabulate Area and Power reports.

## Aim:

Synthesize 32 Bit ALU design using Constraints and analyse area and Power reports.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

•	The .v File must contain the following commands

```
module alu_32bit_case(y,a,b,f);
input [31:0]a;
input [31:0]b;
input [2:0]f;
output reg [31:0]y;
always@(*)
begin
case(f)
3'b000:y=a&b; //AND Operation
3'b001:y=a|b; //OR Operation
3'b010:y=~(a&b); //NAND Operation
3'b011:y=~(a|b); //NOR Operation
3'b100:y=a^b; //XOR Operation
3'b101:y=~(a^b); //XNOR Operation
3'b110:y=~a; //NOT of a
3'b111:y=~b; //NOT of b
endcase
end
endmodule
```

•	The Run.tcl File must contain the following commands:

```
read_libs /cadence/install/FOUNDRY-01/digital/90nm/dig/lib/slow.lib
read_hdl alu_32bit.v
elaborate
 
syn_generic
report_area
syn_map
report_area
syn_opt
report_area 

report_area > alu_32bit_area.txt
report_power > alu_32bit_power.txt
report_area > alu_32bit_cell.txt
report_gates > alu_32bit_gates.txt

write_hdl > alu_32bit_netlist.v

gui_show

```

### Step 2 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :

![Screenshot 2024-11-11 114128](https://github.com/user-attachments/assets/f90bbed8-9e36-424d-9a55-71017db7e040)

#### Area report:

![Screenshot 2024-11-11 114213](https://github.com/user-attachments/assets/37825374-08b3-4ee5-92f6-cadab1205db1)

#### Power Report:

![Screenshot 2024-11-11 114228](https://github.com/user-attachments/assets/d8eaa884-bc8a-4a6d-a455-1bbb79d496bb)

#### Result: 

The generic netlist of 32 bit ALU  has been created, and area, power reports have been tabulated and generated using Genus.
