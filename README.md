# RTL-Design with verilog using Sky130 Technology
![alt text](Verilog-flyer.png)
## ***Brief Intro To Course***
This is a Five-Day workshop is  on RTL Design using verilog with SKY130 Technology which is organised by [VLSI System Design VSD](https://www.vlsisystemdesign.com/).Main agenda of this Five-Day workshop is on  Synthesis of verilog code into a predictable logic in silicon which is Gate-level netlist.As every verilog code can't be synthesizable and Even if does  it may result in different logic depending on the coding styles used.On Day-1 of the workshop I was introduced with Installation and Logical verification using iverilog.And Basic Translation of Verilog code in Gate-Level netlist using Yosys.  


## **INDEX**
- [RTL Design Synthesis using Sky130 Technology](https://github.com/Jayanth-sharma/RTL-design-synthesis-using-sky130--vsd#rtl-design-with-verilog-using-sky130-technology)<br/>
      -[Brief Intro To Course](https://github.com/Jayanth-sharma/RTL-design-synthesis-using-sky130--vsd#brief-intro-to-course)
   
   
   
   


# DAY1 : Introduction To Verilog RTL Design and Synthesis.

On the first day of the We preformed tool set-up.And analysed the basic flow of Simulator and Synthesiers.We also analysed the translated Gate-level netlist with Different Flavours of Standard cell types with  Constraints  of  mainly focusing  on Timing in Circuits  taking  Set-up and Hold-time into Consideration.And correlating the Performance of Cells with  wide width and narrow width to drive the Capacitors.And tried out Synthesis of a Good mux as well as Checked the Logical Funtionality in Iverilog and Gtkwave.<br/>

# Part1 :Introduction to Open-source Simulator iverilog

## Introduction to iverilog,Design and testbench
### Simulation:
- It is technique for applying different input stimulus to the design at different times to check if the RTL code behaves in an intended way.Usually using a Simulation Software(Simulator).In our case we are dealing with Digital design which is modelled using HDL (hardware description language) like VHDL,Verilog,System Verilog.And for high-level synthesis languages too such as C/C++,SystemC etc.
### Simulator:
- A Simulator is a tool which is used for checking a funtionality of Design..<br />
- Icarus Verilog (iverilog) : It is a verilog simulation and synthesis tool. It operates as a compiler, compiling source code written in Verilog (IEEE-1364) into some target format.Icarus Verilog is an open source Verilog compiler that supports the IEEE-1364 Verilog HDL including IEEE1364-2005 plus.<br/>


### RTL Design :
-RTL design is the implementation of a specs.RTL design is checked  for adherence to the spec by the design.The tool used for Simulating the design is a Simulator.<br />
- Design is the actual verilog code or a set of verilog codes which has intented functionality to meet with the required specfication.<br/>
-  RTL Design – Stands for Register Transfer Level. It provides an abstraction of the digital circuit using:<br/>
   -i.   Combinational logic<br/>
   -ii.  Registers<br/>
   -iii. Modules (IP’s or Soft Macros)<br/>

### Test-Bench:
- It is the Setup to apply stimulus(Test_Vectors) to Design to check it's Functionality.Here the Logical functionality is verified.

### How Simulator Works:
- Simulator looks for the changes on Inputs Signals
- Upon changes to input the Output is evaluated
     If there is no change in input,no change in output.

## Test-Bench:
<p align="center">
    <img src="" />
</p>
## iVerilog Designflow
<p align="center">
    <img src="" />
</p>

# Design iverilog and Testbench



# Introduction to Yosys.
yosys<br/>
### .lib Function
> Why Diffrent Versions of Cells?

>Setup_time:
  <p align="center">
    <img src="" />
</p>

>Hold time:
<p align="center">
    <img src="" />
</p>
# Lab on Yosys

