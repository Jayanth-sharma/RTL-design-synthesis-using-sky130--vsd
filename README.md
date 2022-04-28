# RTL-Design with verilog using Sky130 Technology
![alt text](Verilog-flyer.png)
## ***Brief Intro To Course***
This is a Five-Day workshop is  on RTL Design using verilog with SKY130 Technology which is organised by [VLSI System Design VSD](https://www.vlsisystemdesign.com/).Main agenda of this Five-Day workshop is on  Synthesis of verilog code into a predictable logic in silicon which is Gate-level netlist.As every verilog code can't be synthesizable and Even if does  it may result in different logic depending on the coding styles used.On Day-1 of the workshop I was introduced with Installation and Design verification using iverilog.And Basic Translation of Verilog code in Gate-Level netlist using Yosys.  


## **INDEX**
- [RTL Design Synthesis using Sky130 Technology](https://github.com/Jayanth-sharma/RTL-design-synthesis-using-sky130--vsd#rtl-design-with-verilog-using-sky130-technology)<br/>
      -[Brief Intro To Course](https://github.com/Jayanth-sharma/RTL-design-synthesis-using-sky130--vsd#brief-intro-to-course)
   
   
   
   
   
   

# DAY1 : Introduction To Verilog RTL Design and Synthesis.
On Day1 <br/>

# Part1 :Introduction to Open-source Simulator iverilog

## Introduction to iverilog,Design and testbench
### Simulator:
- A Simulator is a tool which is used for checking a Design.RTL design is the implementation of a specs.RTL design is checked for adherence to the spec by the design.The   tool used for Simulating the design is a Simulator.<br />

### Design :
- Design is the actual verilog code or a set of verilog codes which has intented functionality to meet with the required specfication.

### Test-Bench:
- It is the Setup to apply stimulus(Test_Vectors) to Design to check it's Functionality.

### How Simulator Works:
- Simulator looks for the changes on Inputs Signals
- Upon changes to input the Output is evaluated
     If there is no change in input,no change in output.
-Simulator is looking for change in the values of input.
## Test-Bench:
<p align="center">
    <img src="" />
</p>
## iVerilog Designflow
<p align="center">
    <img src="" />
</p>

# Part2:Labs Using iverilog and Testbench



# Part3 : Introduction to Yosys.
