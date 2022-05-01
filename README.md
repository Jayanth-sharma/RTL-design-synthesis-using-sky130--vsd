# RTL-Design with verilog using Sky130 Technology
![alt text](Verilog-flyer.png)
## ***Brief Intro To Course***
This is a Five-Day workshop is  on RTL Design using verilog with SKY130 Technology which is organised by [VLSI System Design VSD](https://www.vlsisystemdesign.com/).Main agenda of this Five-Day workshop is on  Synthesis of verilog code into a predictable logic in silicon which is Gate-level netlist.As every verilog code can't be synthesizable and Even if does  it may result in different logic depending on the coding styles used.On Day-1 of the workshop I was introduced with Installation and Logical verification using iverilog.And Basic Translation of Verilog code in Gate-Level netlist using Yosys.  

# **TOOLS :**
  
# **INDEX**
- [RTL Design Synthesis using Sky130 Technology](https://github.com/Jayanth-sharma/RTL-design-synthesis-using-sky130--vsd#rtl-design-with-verilog-using-sky130-technology)<br/>
       - [Brief Intro To Course](https://github.com/Jayanth-sharma/RTL-design-synthesis-using-sky130--vsd#brief-intro-to-course)
   
   
   
   


# DAY1 : Introduction To Verilog RTL Design and Synthesis.

On the first day of the We preformed tool set-up.And analysed the basic flow of Simulator and Synthesiers.We also analysed the translated Gate-level netlist with Different Flavours of Standard cell types with  Constraints  of  mainly focusing  on Timing in Circuits  taking  Set-up and Hold-time into Consideration.And correlating the Performance of Cells with  wide width and narrow width to drive the Capacitors.And tried out Synthesis of a Good mux as well as Checked the Logical Funtionality in Iverilog and Gtkwave.<br/>

# Introduction to Open-source Simulator iverilog:


## Introduction to iverilog,Design and testbench

### Simulation:
- It is technique for applying different input stimulus to the design at different times to check if the RTL code behaves in an intended way.Usually using a Simulation Software(Simulator).In our case we are dealing with Digital design which is modelled using HDL (hardware description language) like VHDL,Verilog,System Verilog.And for high-level synthesis languages too such as C/C++,SystemC etc.
### Simulator:
- A Simulator is a tool which is used for checking a funtionality of Design.The simulator used here is "iverilog". <br />
- Icarus Verilog (iverilog) : It is a verilog simulation and synthesis tool. It operates as a compiler, compiling source code written in Verilog (IEEE-1364) into some target format.Icarus Verilog is an open source Verilog compiler that supports the IEEE-1364 Verilog HDL including IEEE1364-2005 plus.<br/>


### RTL Design :
-RTL design is the implementation of a specs.RTL design is checked  for adherence to the spec by the design.The tool used for Simulating the design is a Simulator.<br />
- Design is the actual verilog code or a set of verilog codes which has intented functionality to meet with the required specfication.<br/>
- RTL Design – Stands for Register Transfer Level. It provides an abstraction of the digital circuit using:<br/>
   -i.   Combinational logic<br/>
   -ii.  Registers<br/>
   -iii. Modules (IP’s or Soft Macros)<br/>

### Test-Bench:
- It is the Setup to apply stimulus(Test_Vectors) to Design to check it's Functionality.Here the Logical functionality is verified.

### How Simulator Works:
- Simulator continouly monitor for the changes on Inputs Signals
- Upon changes to input the Output is evaluated
     If there is no change in input,no change in output.
- Simulator dumps the change to the ouput to a file accoridng to the change in input.


# Design iverilog and Testbench
- The RTL design written in verilog code has some primary inputs and primary outputs. It may have one or more primary inputs and one or more corresponding primary       outputs.
- We need to give stimulus to all the primary inputs and need to observe the primary outputs. Thus we need stimulus generator at the input and stimulus observer at the   output.
- For giving stimulus we write the test bench, for that the design(module) is instantiated in the test bench, then stimulus is applied.
- It is important to note that the test bench doesn't have any primary input and primary output.
## iVerilog Designflow
- The iverilog file takes two inputs:
- RTL Design
- Test-Bench
- As Shown Below: 
       <p
	align="center">
    <img src="Intro/Gtkwave_Flow.jpg" />
    </p>
- The iverilog simulator dumps .vcd(value change dump) which can be viewed using gtkwave <br/>
- Here is a Blockdiagram representation of test-bench:
  <p align="">
    <img src="" />
</p>


### Iverilog Set-up and Simulation
- open terminal and create a root directory to work-in
- Here are the commands to Get started

```
   mkdir vlsi
   cd vlsi
   mkdir vsdflow
   git clone  https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
   
   ```
- Now to Check the Content Enter

   ```
      cd vlsi
      cd vsdflow
      ls 
      cd sky130RTLDesignAndSynthesisWorkshop
      ls -ltr
      cd my_lib
      ls
      cd lib   :This file contain the  Sky130 Standard Cell library
      cd ..
      cd verilog_model :Content of verilog models
      
   ```
    <p align="center">
    <img src="" />
</p>
- Now check the Verilog files which contains the RTL and Test-Bench files 

   ```
      cd sky130RTLDesignAndSynthesisworkshop
      ls
      cd verilog_files
   ```
 <p align="center">
    <img src="" />
</p>

###  Simulation Using iverilog. <br/>
- i.  RTL file and Test-bench files are passed with iverilog simulator.Intially  "a.out" file is outputed <br/>

```
iverilog good_mux.v tb_good_mux.v

```
- ii. Now to get the .vcd file <br/>

```
./a.out

```
 <p align="center">
    <img src="" />
</p>
- iii.To view the waveform for logical verification run the .vcd file with gtkwave <br/>

``` 
 gtkwave tb_good_mux.vcd
 
 ```

<p align="center">
    <img src="" />
</p>

# Introduction to Yosys.
- Yosys:
- This is a framework for RTL synthesis tools. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms for various application   domains.Which converts a RTL design to Gate-level Netlist.<br/>
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
## Lab on Yosys

# Day2: Timming lib,Hierarchical vs Flat Synthesis and Efficient Flop Coding Styles 

# Introduction to Timing.lib
- The Standard cell library
-  <p align="center">
    <img src="" />
</p> 

 ```
 gvim Sky130_fd_scSky130_fd_sc_hd_tt_025C_1v80.lib  
 
 ```
 
 Defaults
  <p align="center">
    <img src="" />
</p>
- To search individual  Standard cells in library use the following Commands.

```

:syn off     //to turn off the syntax
:se nu     //To show numbers
:/cell     //search for "cell"
:g//       //list all

```
here are a few cells:
 <p align="center">
    <img src="" />
</p>

- Here is a small comparsion of a typical  standard cell
  <p align="center">
    <img src="" />
</p>

# Hierarchical vs flat:
## Hierarchical Synthesis With Multiple Modules:

### synth -top 

- Here is an Verilog Code to Check Synthesis of Multiple Modules.

 ```

 module sub_module2 (input a, input b, output y);
	assign y = a | b;
 endmodule

 module sub_module1 (input a, input b, output y);
	assign y = a&b;
 endmodule


 module multiple_modules (input a, input b, input c , output y);
	wire net1;
	sub_module1 u1(.a(a),.b(b),.y(net1));  
	sub_module2 u2(.a(net1),.b(c),.y(y));  
 endmodule

 ```
- Now Lets Synthesis:
 
  
  ```
 
  4.25. Printing statistics.

  === multiple_modules ===

   Number of wires:                  5
   Number of wire bits:              5
   Number of public wires:           5
   Number of public wire bits:       5
   Number of memories:               0
   Number of memory bits:            0
   Number of processes:              0
   Number of cells:                  2
     sub_module1                     1
     sub_module2                     1

  === sub_module1 ===

   Number of wires:                  3
   Number of wire bits:              3
   Number of public wires:           3
   Number of public wire bits:       3
   Number of memories:               0
   Number of memory bits:            0
   Number of processes:              0
   Number of cells:                  1
     $_AND_                          1

  === sub_module2 ===

   Number of wires:                  3
   Number of wire bits:              3
   Number of public wires:           3
   Number of public wire bits:       3
   Number of memories:               0
   Number of memory bits:            0
   Number of processes:              0
   Number of cells:                  1
     $_OR_                           1

  === design hierarchy ===

   multiple_modules                  1
     sub_module1                     1
     sub_module2                     1

   Number of wires:                 11
   Number of wire bits:             11
   Number of public wires:          11
   Number of public wire bits:      11
   Number of memories:               0
   Number of memory bits:            0
   Number of processes:              0
   Number of cells:                  2
     $_AND_                          1
     $_OR_                           1
  
  ```
  
  
  ## Netlist of Multiple Models With hierarchical synthesis :
  
  ```

   /* Generated by Yosys 0.7 (git sha1 61f6811, gcc 6.2.0-11ubuntu1 -O2 -fdebug-prefix-map=/build/yosys-OIL3SR/yosys-0.7=. -fstack-protector-strong -fPIC -Os) */
  
  module multiple_modules(a, b, c, y);
  input a;
  input b;
  input c;
  wire net1;
  output y;
  sub_module1 u1 (
    .a(a),
    .b(b),
    .y(net1)
  );
  sub_module2 u2 (
    .a(net1),
    .b(c),
    .y(y)
  );
  endmodule

  module sub_module1(a, b, y);
  wire _0_;
  wire _1_;
  wire _2_;
  input a;
  input b;
  output y;
  sky130_fd_sc_hd__and2_2 _3_ (
    .A(_0_),
    .B(_1_),
    .X(_2_)
   );
   assign _0_ = b;
   assign _1_ = a;
   assign y = _2_;
   endmodule

   module sub_module2(a, b, y);
   wire _0_;
   wire _1_;
   wire _2_;
   wire _3_;
   wire _4_;
   input a;
   input b;
   output y;
   sky130_fd_sc_hd__clkinv_1 _5_ (
    .A(_0_),
    .Y(_3_)
   );
   sky130_fd_sc_hd__clkinv_1 _6_ (
    .A(_1_),
    .Y(_4_)
   );
   sky130_fd_sc_hd__nand2_1 _7_ (
    .A(_3_),
    .B(_4_),
    .Y(_2_)
   );
   assign _0_ = b;
   assign _1_ = a;
   assign y = _2_;
   endmodule
  

  ``` 
  <p align="center">
    <img src="" />
</p>

### Excercise with .lib

# Flatten Synthesis:


 ```
 /* Generated by Yosys 0.9+4081 (git sha1 862e84eb, gcc 7.5.0-3ubuntu1~18.04 -fPIC -Os) */

(* top =  1  *)
(* src = "multiple_modules.v:10.1-14.10" *)
module multiple_modules(a, b, c, y);
  (* src = "multiple_modules.v:12.14-12.38|multiple_modules.v:5.27-5.28" *)
  wire _0_;
  (* src = "multiple_modules.v:12.14-12.38|multiple_modules.v:5.36-5.37" *)
  wire _1_;
  (* src = "multiple_modules.v:12.14-12.38|multiple_modules.v:5.46-5.47" *)
  wire _2_;
  (* src = "multiple_modules.v:13.14-13.38|multiple_modules.v:1.27-1.28" *)
  wire _3_;
  (* src = "multiple_modules.v:13.14-13.38|multiple_modules.v:1.36-1.37" *)
  wire _4_;
  (* src = "multiple_modules.v:13.14-13.38|multiple_modules.v:1.46-1.47" *)
  wire _5_;
  (* src = "multiple_modules.v:10.32-10.33" *)
  input a;
  (* src = "multiple_modules.v:10.41-10.42" *)
  input b;
  (* src = "multiple_modules.v:10.50-10.51" *)
  input c;
  (* src = "multiple_modules.v:11.7-11.11" *)
  wire net1;
  (* hdlname = "u1 a" *)
  (* src = "multiple_modules.v:12.14-12.38|multiple_modules.v:5.27-5.28" *)
  wire \u1.a ;
  (* hdlname = "u1 b" *)
  (* src = "multiple_modules.v:12.14-12.38|multiple_modules.v:5.36-5.37" *)
  wire \u1.b ;
  (* hdlname = "u1 y" *)
  (* src = "multiple_modules.v:12.14-12.38|multiple_modules.v:5.46-5.47" *)
  wire \u1.y ;
  (* hdlname = "u2 a" *)
  (* src = "multiple_modules.v:13.14-13.38|multiple_modules.v:1.27-1.28" *)
  wire \u2.a ;
  (* hdlname = "u2 b" *)
  (* src = "multiple_modules.v:13.14-13.38|multiple_modules.v:1.36-1.37" *)
  wire \u2.b ;
  (* hdlname = "u2 y" *)
  (* src = "multiple_modules.v:13.14-13.38|multiple_modules.v:1.46-1.47" *)
  wire \u2.y ;
  (* src = "multiple_modules.v:10.61-10.62" *)
  output y;
  sky130_fd_sc_hd__and2_0 _6_ (
    .A(_1_),
    .B(_0_),
    .X(_2_)
  );
  sky130_fd_sc_hd__lpflow_inputiso1p_1 _7_ (
    .A(_4_),
    .SLEEP(_3_),
    .X(_5_)
  );
  assign _4_ = \u2.b ;
  assign _3_ = \u2.a ;
  assign \u2.y  = _5_;
  assign \u2.a  = net1;
  assign \u2.b  = c;
  assign y = \u2.y ;
  assign _1_ = \u1.b ;
  assign _0_ = \u1.a ;
  assign \u1.y  = _2_;
  assign \u1.a  = a;
  assign \u1.b  = b;
  assign net1 = \u1.y ;
endmodule

 
 ```


<p align="center">
    <img src="" />
</p>

## Sub-Module Level Synthesis:


## Sub-Module use-Cases:
  
  
  
# Flop Coding Styles and Optimisations:


## Optimisation:
- Netlist Mul2:
  ```
  write_verilog mult_2.v  :dumps mul2
  !gvim mul2
  
  ```
  ```
  
  /* Generated by Yosys 0.9+4081 (git sha1 862e84eb, gcc 7.5.0-3ubuntu1~18.04 -fPIC -Os) */

  (* top =  1  *)
  (* src = "mult_2.v:1.1-3.10" *)
  module mul2(a, y);
  (* src = "mult_2.v:1.26-1.27" *)
  input [2:0] a;
  (* src = "mult_2.v:1.42-1.43" *)
  output [3:0] y;
   assign y = { a, 1'h0 };
   endmodule

  ```
  ```
  /* Generated by Yosys 0.7 (git sha1 61f6811, gcc 6.2.0-11ubuntu1 -O2 -fdebug-prefix-map=/build/yosys-OIL3SR/yosys-0.7=. -fstack-protector-strong -fPIC -Os) */

  module mul2(a, y);
  input [2:0] a;
  output [3:0] y;
  assign y = { a, 1'b0 };
  endmodule

  ```
 - Mult8 
   ```
   /* Generated by Yosys 0.9+4081 (git sha1 862e84eb, gcc 7.5.0-3ubuntu1~18.04 -fPIC -Os) */

   (* top =  1  *)
   (* src = "mult_2.v:1.1-3.10" *)
   module mul2(a, y);
   (* src = "mult_2.v:1.26-1.27" *)
   input [2:0] a;
   (* src = "mult_2.v:1.42-1.43" *)
   output [3:0] y;
   assign y = { a, 1'h0 };
   endmodule

   ```
  
   ```
   /* Generated by Yosys 0.9+4081 (git sha1 862e84eb, gcc 7.5.0-3ubuntu1~18.04 -fPIC -Os) */

   module mult8(a, y);
     input [2:0] a;
     output [5:0] y;
     assign y = { a, a }; 
   endmodule
  
   ```
# Day 3:Combinational And Synthesis Optimisation:
## Intro To  Optimisation:
## Combinational  Logic Optimisation : 
 -  opt_check.v
 
    ```
    module opt_check (input a , input b , output y);
	assign y = a?b:0;
    endmodule 
      ```
 - The following command Removes the unused Wires:
    
    ``` 
    opt_clean -purge
    
    ```
  
    
##  Excerise:
-  opt_check4:

### Multiple_modules_opt In Hier vS flat:
-  UnderExcerise
   Here are the verilog_files associated with Mutliple Modules for Optimisation:
   ![excerise_multiple_opt](https://user-images.githubusercontent.com/53760504/166091041-d8bad134-6bcf-4710-b72d-c26a4dfbe513.jpg)
    
-  Verilog Code For Multiptle_modules_opt:
- 
   ```
   module sub_module1(input a , input b , output y);
   assign y = a & b;
   endmodule


   module sub_module2(input a , input b , output y);
   assign y = a^b;
   endmodule


   module multiple_module_opt(input a , input b , input c , input d , output y);
   wire n1,n2,n3;

   sub_module1 U1 (.a(a) , .b(1'b1) , .y(n1));
      sub_module2 U2 (.a(n1), .b(1'b0) , .y(n2));
      sub_module2 U3 (.a(b), .b(d) , .y(n3));

     assign y = c | (b & n1); 


     endmodule
     
   ```
   Synthesis Report:
   
   ```
   3.25. Printing statistics.

    === sub_module1 ===

    Number of wires:                  3
    Number of wire bits:              3
    Number of public wires:           3
    Number of public wire bits:       3
    Number of memories:               0
    Number of memory bits:            0
    Number of processes:              0
    Number of cells:                  1
      $_AND_                          1

    === multiple_module_opt ===

    Number of wires:                  7
    Number of wire bits:              7
    Number of public wires:           6
    Number of public wire bits:       6
    Number of memories:               0
    Number of memory bits:            0
    Number of processes:              0
    Number of cells:                  3
      $_AND_                          1
      $_OR_                           1
      sub_module1                     1
 
    === design hierarchy ===

    multiple_module_opt               1
      sub_module1                     1

    Number of wires:                 10
    Number of wire bits:             10
    Number of public wires:           9
    Number of public wire bits:       9
    Number of memories:               0
    Number of memory bits:            0
    Number of processes:              0
    Number of cells:                  3
      $_AND_                          2
      $_OR_                           1

   ```
-  With opt_clean -purge vs without:
   With Clean:
   
    ![multiple_modules_opt_show](https://user-images.githubusercontent.com/53760504/166092021-b8880722-74ac-444b-ad00-9d7897fb9e47.jpg)
   Without clean:
   ![without_opt_clean](https://user-images.githubusercontent.com/53760504/166092037-c700d3dc-e57b-4dcf-b7f0-05471266bbc9.jpg)
- Multiple_module_opt2 hier vs Flatten:
- Similarly Hier with Multiple_module_opt2
  
  ![Multiple_module2_opt_hier](https://user-images.githubusercontent.com/53760504/166092623-13b703c0-ea37-4151-ab9b-286ffb2a9f1e.jpg)
- Flatten multiple_module_opt2:
    <p align="center">
    <img src="https://user-images.githubusercontent.com/53760504/166092729-13fb7a58-42b9-409b-86d9-0c6d9a88137f.jpg" />
  </p>
  <p align="center">
    <img src="https://user-images.githubusercontent.com/53760504/166092814-be440471-4f4a-4d99-879f-c9d174098eb0.jpg" />
 </p>
   

## Seqential Logic Optimisation:
## Sequential Optimisation
- dff_const1.v 
  ```
  module dff_const1(input clk, input reset, output reg q);   
   always @(posedge clk, posedge reset) 
   begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
    end

    endmodule
   //td_dff_const1
   module dff_const1(input clk, input reset, output reg q);
   always @(posedge clk, posedge reset)
   begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
   end
 
   endmodule
  ```
### Optimisation On Yosys:
-  For optimisation:
-  Don't  forgot to add 
   ```
   dfflibmap  ./my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
   ```
   
## Seqential Logic Optimisation For Used Inputs:



### Experiment:
- Now Let's assign count(q) of the counter as follows:

#  Day 4:GLS,Blocking Vs Non-Blocking and Synthesis Mismatch:
## Gate-Level-Simulation Concepts Flow Using Iverilog:

   ![GLS_flowchart](https://user-images.githubusercontent.com/53760504/166114194-4eb24562-e700-465a-b244-4194b88511c6.jpg)

### Gate Level Simulation:
-  In GLS the Synthesized netlist is Simulated to Verify  the  logical correctness of the Design.Running the Test bench with Design Under Test.
-  Netlist is logically same as RTL programme  except the representation of design is more Technology centric to pass the design lower abstraction layer with      neccessary  optimisations done with Available Standard Cells,PVT(eco) corners.By keeping Set of input and Output the same of RTL abstractions. 
    -  Same Test Bench can be Used 
-   Also Ensuring timing of design is met.For which GLS needs a be run with Design Annotation.
-   
## GLS Synthesis Simulation Mismatch:
- Simulator works with the concept of activity.
- Missing Sensitivety List
   ```
    module ternary_operator_mux (input i0 , input i1 , input sel , output y);
	assign y = sel?i1:i0;
	endmodule
   ```
   ```
   module bad_mux (input i0 , input i1 , input sel , output reg y);
   always @ (sel)
   begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
    end
   endmodule
   ```
   ```module good_mux (input i0 , input i1 , input sel , output reg y);
      always @ (*)
      begin
	if(sel)
		y <= i1;
	else 
		y <= i0;
        end
      endmodule
   ```
  
 

## Blocking And Non-Blocking Statements:
  ```
   module blocking_caveat (input a , input b , input  c, output reg d); 
   reg x;     
   always @ (*)
   begin
	d = x & c;
	x = a | b;
   end   
   endmodule

 ```
 # Day 5: If,Case,For loop and For Generate:
 ## 


# Acknowledgements:
- [Kunalghosh(Co-founder-VlSI System Design)](https://github.com/kunalg123)
- [Shon Taware (Teaching Assistant)](https://github.com/ShonTaware)
 



