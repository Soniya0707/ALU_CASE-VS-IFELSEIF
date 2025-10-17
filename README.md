# Exp 4 Comparative Study of 32-Bit ALU Implementations Using Case and If-Else Constructs
module alu_32bit_case(y,a,b,f); 
input [31:0]a;
input [31:0]b;
input [2:0]f; 
output reg [31:0]y; 
always@(*)
begin 
case(f)
3'b000:y=a&b;	//AND Operation
3'b001:y=a|b;	//OR Operation
3'b010:y=~(a&b);//NAND Operation
3'b011:y=~(a|b);//NOR Operation
3'b100:y=a+b;	//Addition
3'b101:y=a-b;	//Subtraction
3'b110:y=a*b;   //Multiply
3'b111:y=a^b;	// XOR Operation
default:y=32'bx;
endcase 
end 
endmodule
## Aim: 
Write a Verilog code for 32 32-bit ALU supporting four logical and four arithmetic operations, use case statement and if statement for ALU behavioral modeling. 

To verify the Functionality using Test Bench 

Synthesize and compare the results using if and case statements 

Identify Critical Path and constraints

## Tool Required: 
 Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim) 

 Synthesis: Genus 

## Design Information and Block Diagram: 
The ALU will take in two 32-bit values and a control line. An Arithmetic unit does the following tasks like addition, subtraction, multiplication and logical operations. As the input is given in 32-bit, we get a 32-bit output. The arithmetic will show only one output at a time, so a selector is necessary to select one of the operators. 

 <img width="668" height="344" alt="image" src="https://github.com/user-attachments/assets/b5f95c0d-1fd6-4c3c-9a35-11eb9c86cba3" />

#### Figure No 1: Block Diagram of 32 Bit ALU 

## Creating a Workspace:
Create a folder in your name (Note: Give the folder name without any spaces) and create a new sub-directory named Exp4 or alu_bl_model for the design. Then, open a terminal from the Sub-Directory.

## Creating Source Codes
In the Terminal window, type gedit <filename>.v (ex: gedit alu_case.v).

A Blank Document opens up into which the following source code can be typed.

(Note: File name should be with HDL Extension)

To verify the Functionality using the Test Bench

#### Source Code – Using Case Statement :
(Include program here)

Use the Save option or Ctrl+S to save the code, or click on the save option from the top-right corner and close the text file.

#### Creating a Test Bench:
Similarly, create your test bench using gedit <filename_tb>.v to open a new blank document (alu_case_tb.v).

#### Test Bench :
(Include test bench program here)

Use the Save option or Ctrl+S to save the code, or click on the save option from the top-right corner and close the text file.

#### Source Code - Using If Statement :
(Include program here)

#### Test Bench :
(Include program here)

Functional Simulation for each design

Invoke the cadence environment by typing the commands below

tcsh (Invokes C-Shell)

source /cadence/install/cshrc (mention the path of the tools)

(The path of cshrc could vary depending on the installation destination)

After this, you can see the window like below

To Launch the Simulation tool

•linux:/> nclaunch -new& // “-new” option is used for invoking NCVERILOG for the first time for any design

or

•linux:/> nclaunch& // On subsequent calls to NCVERILOG

It will invoke the nclaunch window for functional simulation. We can compile, elaborate and simulate it using Multiple Steps.

Setting Multi-step simulation

Select Multiple Step and then select “Create cds.lib File” as shown in the figure below

Click the .cds.lib file and save the file by clicking on the Save option

Fcds.lib file Creation

Save .lib file and select the correct option for cds.lib file format based on the HDL Language and Libraries used.

Select “Don’t include any libraries (verilog design)” from “New cds.lib file” and click on “OK” as in the figure below.

We are simulating a verilog design without using any libraries

Click “OK” in the “nclaunch: Open Design Directory” window, as shown in the figure below

<img width="1920" height="1080" alt="Screenshot (283)" src="https://github.com/user-attachments/assets/4cef3f4b-2ba5-4f86-97ba-8ed82e4d131c" />


#### Fig 2: Selection of Don’t include any libraries
An ‘NCLaunch window’ appears as shown in the figure below

Left side, you can see the HDL files. The right side of the window has Worklib and snapshots directories listed.

Worklib is the directory where all the compiled codes are stored, while Snapshot will have the output of elaboration, which in turn goes for simulation.

To perform the function simulation, the following three steps are involved: Compilation, Elaboration and Simulation.

<img width="1920" height="1080" alt="Screenshot (284)" src="https://github.com/user-attachments/assets/9abaa2ee-4eec-45b2-a13b-63414369c62a" />


#### Fig 3: Nclaunch Window

#### Step 1: Compilation:
– Process to check the correct Verilog language syntax and usage

Inputs: Supplied are Verilog design and test bench codes

Outputs: Compiled database created in mapped library if successful, generates report else error reported in log file

#####  Steps for compilation:
	Create work/library directory (most of the latest simulation tools creates automatically)
 
	Map the work to library created (most of the latest simulation tools creates automatically)
 
 Run the compile command with compile options
 
i.e Cadence IES command for compile: ncverilog +access+rwc -compile filename.v

Left side select the file and in Tools: launch verilog compiler with current selection will get enable. Click it to compile the code

Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation

#### Fig 4: Compiled database in WorkLib
After compilation, it will come under worklib. You can see on the right side window

select the test bench and compile it. It will come under Worklib. Under Worklib, you can see the module and test bench.

The cds.lib file is an ASCII text file. It defines which libraries are accessible and where they are located. It contains statements that map logical library names to their physical directory paths. For this Design, you will define a library called “worklib”

![WhatsApp Image 2025-10-04 at 08 58 43_6d10abab](https://github.com/user-attachments/assets/225087ec-d523-4218-a564-9b09bb8dcd0c)



<img width="1920" height="1080" alt="Screenshot (288)" src="https://github.com/user-attachments/assets/eb26c34c-d30f-4e7d-b514-c9b5af3fcb6b" />


#### Step 2: Elaboration:
To check the port connections in a hierarchical design

Inputs: Top-level design/test bench Verilog codes

Outputs: Elaborate database updated in the mapped library if successful, generates a report, else error reported in the log file

#####  Steps for elaboration

– Run the elaboration command with elaborate options

1.It builds the module hierarchy

2. Binds modules to module instances
   
3.Computes parameter values

4. Checks for hierarchical name conflicts
   
5.It also establishes net connectivity and prepares all of this for simulation

After elaboration, the file will come under snapshot. Select the test bench and simulate it.

#### Fig 5: Elaboration Launch Option

![WhatsApp Image 2025-10-04 at 08 58 14_80393a2b](https://github.com/user-attachments/assets/5208be44-f376-437f-9a03-585315016cf2)



<img width="1920" height="1080" alt="Screenshot (289)" src="https://github.com/user-attachments/assets/6c218d2e-0786-4351-bca9-c13df02f8888" />


#### Step 3: Simulation:
– Simulate with the given test vectors over a period of time to observe the output behaviour.

Inputs: Compiled and Elaborated top-level module name

Outputs: Simulation log file, waveforms for debugging

Simulations allow dumping design and test bench signals into a waveform

Steps for simulation – Run the simulation command with simulator options


![WhatsApp Image 2025-10-04 at 09 02 38_5159f3e7](https://github.com/user-attachments/assets/aa71c00c-9f3e-440f-be9e-fc1a969cfa0d)


<img width="1920" height="1080" alt="Screenshot (290)" src="https://github.com/user-attachments/assets/851e69c9-0d19-4021-9e8a-1c7091a39d45" />


#### Fig 6: Design Browser window for simulation

![WhatsApp Image 2025-10-04 at 09 08 40_f8c29f4d](https://github.com/user-attachments/assets/3be9615a-4225-4542-b241-078847654488)



<img width="1920" height="1080" alt="Screenshot (286)" src="https://github.com/user-attachments/assets/8d2938c3-7dd7-4ada-9842-edc0b73fc7c4" />


#### Fig 7: Simulation Waveform Window

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

![WhatsApp Image 2025-10-04 at 09 31 02_3dc579f5](https://github.com/user-attachments/assets/984e9512-9609-4ebd-aefa-e986bbf672a0)


<img width="1920" height="1080" alt="Screenshot (287)" src="https://github.com/user-attachments/assets/8c7e6fff-d509-4e1b-ab4d-670b1ec88bd3" />

##### Performing Synthesis

##### Synthesize Design

Run the synthesis Process one time for each code and make sure the output File names are changed accordingly

The Liberty files are present in the library path,

• The Available technology nodes are 180nm,90nm and 45nm.

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist. Or use source run.tcl command in the terminal window to view the netlist, and a log file will be created in the working folder.

#### Fig 8: Synthesis RTL Schematic using case and ifelseif construct

![WhatsApp Image 2025-10-04 at 09 39 06_96866646](https://github.com/user-attachments/assets/8656b8c6-5622-4a9b-97da-f45d7b3f298f)


<img width="1920" height="1080" alt="Screenshot (292)" src="https://github.com/user-attachments/assets/5db3ca5d-acdf-4eaa-bc6c-4eb27d5eb6e7" />


#### Fig 9: Area report of case and ifelseif construct

![WhatsApp Image 2025-10-04 at 09 41 49_fbe31f12](https://github.com/user-attachments/assets/6ed954ec-0fdc-42b5-9b43-23c54ce1537f)

<img width="1920" height="1080" alt="Screenshot (294)" src="https://github.com/user-attachments/assets/a3f79bae-f4fa-428e-8a80-91aa5acb66d9" />

#### Fig 10: Power Report of case and ifelseif construct

![WhatsApp Image 2025-10-04 at 09 43 00_f34e4460](https://github.com/user-attachments/assets/a202c08e-2a4a-4a99-8cd7-204f4426bf07)

<img width="1920" height="1080" alt="Screenshot (295)" src="https://github.com/user-attachments/assets/11e96a89-2c7f-42d0-8c67-3080bdfff344" />


#### Fig 11: Timing Report of case and ifelseif construct

![WhatsApp Image 2025-10-04 at 09 46 33_374a5958](https://github.com/user-attachments/assets/c602d3c9-fbca-4fac-a706-2b8e961e3ef5)

<img width="1920" height="1080" alt="Screenshot (296)" src="https://github.com/user-attachments/assets/e37452e7-0ee2-4c96-87ec-bcf89de4421f" />


#### Fig 12: Tabulate Area,Power and Timing Report Comparision of ALU using case and ifelseif construct

![WhatsApp Image 2025-10-17 at 22 05 48_850bbeea](https://github.com/user-attachments/assets/905eed01-7a20-411a-9fdb-f064fdd9b1ea)

## Result
The 32-bit ALU implemented using behavioural case statements and if–elseif constructs was successfully verified under Incisive (ncvlog/ncsim) for all tested vectors. Both implementations were functionally correct and synthesizable. Synthesis using Cadence Genus generated gate-level netlists along with area, timing, and power reports.
A comparative analysis revealed that the case-statement-based ALU resulted in slightly lower area and better timing performance, while the if–elseif-based ALU exhibited higher logic complexity and marginally increased delay due to sequential decision evaluation. Both designs, however, produced identical functional outputs.
