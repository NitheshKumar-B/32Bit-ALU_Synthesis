# 32Bit-ALU_Synthesis

## Aim:

Synthesize 32 Bit ALU design using Constraints and analyse area and Power reports.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

## Program:
 alu 32 bit:
```
  module alu_32bit_case(y, a, b, f);
  input [31:0] a;
  input [31:0] b;
  input [2:0] f;
  output reg [31:0] y;

  always @(*) begin
    case(f)
      3'b000: y = a & b;       // AND
      3'b001: y = a | b;       // OR
      3'b010: y = ~(a & b);    // NAND
      3'b011: y = ~(a | b);    // NOR
      3'b100: y = a + b;       // ADD
      3'b101: y = a - b;       // SUB
      3'b110: y = a * b;       // MUL
      default: y = 32'bx;      // Undefined
    endcase
  end

endmodule
```
 alu.tcl

 ```
read_libs /cadence/install/FOUNDRY-01/digital/90nm/dig/lib/slow.lib
read_hdl alu32bit.v
elaborate
syn_generic
report_area
syn_map
report_area
syn_opt
report_area 
report_area > alu_area.txt
report_power > alu_power.txt
report_timing > alu_timing.txt
report_gates > alu_gates.rpt
write_hdl > alu_netlist.v
gui_show

```


### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

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

![Screenshot 2025-05-19 160103](https://github.com/user-attachments/assets/eafef6d1-ee06-4f5b-827f-bab702927d2d)


#### Area report:

![Screenshot 2025-05-19 160348](https://github.com/user-attachments/assets/cade5d56-7130-41a1-8c78-cc628cfc3e83)

#### Power Report:

![Screenshot 2025-05-19 160435](https://github.com/user-attachments/assets/805df2c4-220f-47a8-90b2-2779ae95b746)


#### Gates Report:

![Screenshot 2025-05-19 160420](https://github.com/user-attachments/assets/6a4da0d1-630a-46b2-81b5-e566af05f684)

#### Timing Report:

![Screenshot 2025-05-19 163712](https://github.com/user-attachments/assets/c98b70c4-bcd0-46ed-8b05-844e3b8edebf)



#### Result: 

The generic netlist of 32 bit ALU  has been created, and area, power reports have been tabulated and generated using Genus.
