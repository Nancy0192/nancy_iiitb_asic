# Tapeout Process <br>
This repository illustrates the whole process required during a tapeout.

## Overview

**Day 0 - Installation Of Required Softwares**
- Install all the required softwares for vsd design
     - [Yosys](#yosys)
     - [Iverilog](#iverilog)
     - [GTKWave](#gtkwave)
     - [Ngspice](#ngspice)
     - [OpenSTA](#opensta)
     - [Magic](#magic)
     - [OpenLane](#openlane)
  
**Day 1 - Introduction Of Verilog RTL Design and Synthesis**
- [Cloning Of Github folder](#cloning-of-github-folder)
- [Simulation - Using Iverilog and GTKWave](#simulation---using-iverilog-and-gtkwave)
- [Synthesis - Using Yosys](#synthesis---using-yosys)

**Day 2 - Timing libs, hierarchical vs flat synthesis and efficient flop coding styles**
- Introduction to Timing.libs
- Hierarchical vs Flat Synthesis
- Various Flop Coding Styles and Optimization

**Day 3 - Combinational and Sequential Optimizations**
- Optimization
- Lab Session On Combinational Logic Optimization
- Lab Session On Sequential Logic Optimization

**Day 4 - GLS, Blocking vs Non-blocking and Synthesis-Simulation mismatch**
- GLS
- Labs on GLS and Synthesis-Simulation Mismatch
- Labs on Synthesis-Simulation Mismatch for blocking statement.

**Day 5 - If, Case, For loop and For Generate**
- If, Case, For loop and Generate For loop
- Lab session 

## Day 0
## Yosys
<details><summary>Steps For Installation</summary>

  ```
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys-master
$ sudo apt install make (If make is not installed please install it)
$ sudo apt-get install build-essential clang bison flex
  libreadline-dev gawk tcl-dev libffi-dev git
  graphviz xdot pkg-config python3 libboost-system-dev
  libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make
$ sudo make install
```
 

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/d8619c01-0665-442b-96f9-45a0c2f68685)

</details>

## Iverilog

<details> <summary>Steps For Installation</summary>

 ```
   $ sudo apt-get install iverilog
```
 
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/d72c451e-f951-458e-bfae-0a46b7505299)
</details>


## GTKWave
<details> <summary>Steps For Installation</summary>

```
  $ sudo apt update
  $ sudo apt install gtkwave
```


![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/0dec3ee9-fd93-45d5-a678-fc778af882b5)

</details>


## Ngspice
<details> <summary>Steps For Installation</summary>

```
$ sudo apt-get install build-essential
$ sudo apt-get install libxaw7-dev
$ tar -zxvf ngspice-40.tar.gz
$ cd ngspice-40
$ mkdir release
$ cd release
$ ../configure  --with-x --with-readline=yes --disable-debug
$ make
$ sudo make install
```
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/7e3bf22f-1830-4002-8fa7-8986d08acd47)

</details>


 ## OpenSTA
<details> <summary>Steps For Installation</summary>

```
$ sudo apt-get install cmake clang gcctcl swig bison flex
$ git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
$ cd OpenSTA
$ mkdir build
$ cd build
$ cmake ..
$ make
```
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/123f7c62-e5d1-4046-8e5b-03a32a070d4b)

</details>


## Magic
<details> <summary>Steps For Installation</summary>

```
$ sudo apt-get install m4
$ sudo apt-get install tcsh
$ sudo apt-get install csh
$ sudo apt-get install libx11-dev
$ sudo apt-get install tcl-dev tk-dev
$ sudo apt-get install libcairo2-dev
$ sudo apt-get install mesa-common-dev libglu1-mesa-dev
$ sudo apt-get install libncurses-dev
$ git clone https://github.com/RTimothyEdwards/magic
$ cd magic
$ ./configure
$ make
$ sudo make install
```
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/694592f3-8e63-4329-8b74-8f12dcf30179)
</details>


## OpenLane
<details> <summary>Steps For Installation</summary>

```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt install -y build-essential python3 python3-venv python3-pip make git
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
$ echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee      /etc/apt/sources.list.d/docker.list > /dev/null
$ sudo apt update
$ sudo apt install docker-ce docker-ce-cli containerd.io
$ sudo docker run hello-world
$ sudo groupadd docker
$ sudo usermod -aG docker $USER
$ sudo reboot
```
After reboot, you can check for installation using following command:

```
$ sudo docker run hello-world
```
</details>


## Day 1 - Introduction Of Verilog RTL Design and Synthesis

In today's Lab, we will learn how to simulate the verilog code as well as synthesize it to create a netlist using the yosys software.

## Cloning Of Github Folder
The following github repository contains all collaterals for RTL Design and Synthesis using Sky130 PDK's.
<details> <summary>Steps For Cloning</summary>

```
$ git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```
</details>

## Simulation - Using Iverilog and GTKWave

Simulation or simulation program in Verilog helps to test the logic design using simulation models to represent the logic circuits that interface to the design. A set of simulation models is a testbench.
In this particular repository, we will be using iverilog to compile the verilog code and gtkwave to view the waveforms.

<details><summary>Verilog Code Required For Simulation</summary>
<br>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/24a335bf-f30b-4438-b430-f4969057b9fd)

<br>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/e0e90514-d140-489b-8cba-83080d44a6a3)


</details>

<details> <summary>Steps For Simulation</summary>
     
```
$ iverilog good_mux.v tb_good_mux.v
$ ./a.out
$ gtkwave tb_good_mux.vcd
```
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/1ad48477-b6e1-477f-95ce-18de38f2fa25)

</details>

## Synthesis - Using Yosys
Synthesis is the process of developing a physical system using the abstract descriptions of predefined building blocks such as flipflops, latches and logic gates. It creates a gate-level netlist from a model of a circuit described in Verilog. Yosys is a framework for Verilog RTL synthesis which will be used in this repository as synthesis tool.

<details> <summary>Steps For Synthesis</summary>
     Change the working directory to be the one in which we have all the verilog files as per https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git  repository.
     
     
     $ cd /home/nancy/Documents/ASIC/VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files

Open the yosys on terminal and follow the below commands
```
$ yosys
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> read_verilog good_mux.v
yosys> synth -top good_mux
```
After running synth command, you will see the following data on the terminal
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/1f876869-f417-4d50-b313-af4794ea59b9)

Now we will generate the netlist and view it using the following command
```
yosys> abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
yosys> show
```

The following netlist will be created 

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/8097d156-a5d3-42db-b6ff-7fd42c93ee8f)

You can also write the netlist using the following command and also view it
```


yosys> write_verilog -noattr good_mux_netlist.v
yosys> !gvim good_mux_netlist.v
```
</details>

## Day 2
In today's lab we will go through the timing library and understand the concept of hierarchical and flat synthesis. We will also understand the various flop coding styles and how to optimize that.

## Introduction to Timimg.libs
In this repository we have been using sky130_fd_sc_hd__tt_025C_1v80.lib file which contains PVT parameters i.e. Process, Voltage and Temperature parameters. It also contains the technology that we are using i.e. CMOS.
The name of the library also defines some of the parameters i.e. tt means typical process, 025C defines the temperature and v0 defines the voltage.
The file contains different version of same logic gate either they have different area or speed which can be used according to the circuit.
The following image shows the different version of and gate modules:


## Hierarchical vs Flat Synthesis

### Hierarchical Synthesis
In hierarchical synthesis, we have a top module in which sub-modules are instantiated and are designed or synthesized independently before combining with the top module.
We have taken a top module named as multiple_module.v in which we have instantiated two sub-modules as shown below
```
module sub_module2 (input a, input b, output y);
   assign y = a | b;
endmodule

module sub_module1 (input a, input b, output y);
   assign y = a&b;
endmodule


module multiple_modules (input a, input b, input c , output y);
   wire net1;
   sub_module1 u1(.a(a),.b(b),.y(net1));  //net1 = a&b
   sub_module2 u2(.a(net1),.b(c),.y(y));  //y = net1|c ,ie y = a&b + c;
endmodule
```
Now we will syhthesize the same using following commands:

```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
read_verilog 
read_verilog multiple_modules.v 
synth -top multiple_modules
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
show multiple_modules
write_verilog -noattr multiple_modules_net.v
!gvim multiple_modules_net.v 
```

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/c7030e92-e3f8-438d-aafd-348d5a8bb1d4)


### Flat Synthesis
In the flat synthesis hierarchies are flattened out and directly instantiates gates here.
We have taken the same code of multiple modulesand ran the following commands to flatten it :
```
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
read_verilog 
read_verilog multiple_modules.v 
synth -top multiple_modules
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
flatten
show
write_verilog -noattr multiple_modules_net.v
!gvim multiple_modules_net.v
```

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/4587aa84-0b51-4a2f-be11-1be209ac2903)

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/79282610-d31c-46e7-b8d9-e0dabd48bf86)


## Various Flop Coding Styles and Optimization
### Need Of Flip Flop
Flip-flops are the quintessential edge-triggered logic. Along with the fact that they have memory, this makes them the gate-keeper component that can block when there is no clock edge, sample signals on the clock edge, and preserve the output signal away from a clock edge. Flip-flops allow the the clock control the flow of signals from one component to the next.

**General Steps For Simulation**

```
$ iverilog <rtl_code.v> <tb_rtl_code.v>
$ ./a.out
$ gtkwave <vcd_file>
```

**General Steps For Synthesis**

```
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib  
$ read_verilog <module_name.v> 
$ synth -top <top_module_name>
$ dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr <netlist_name.v>
$ !gvim <netlist_name.v>
```

## Flip Flop Simulation And Synthesis
### D-FF With Synchronous Reset
<details><summary>Simulation</summary>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/bfda4266-6730-4b80-bc10-f42f7dbd93e3)

	
</details>

<details><summary>Synthesis</summary>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/fae2d642-5f06-4ee3-8d82-0c8482407455)

</details>

### D-FF With Asynchronous Reset

<details><summary>Simulation</summary>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/04c423b6-29b3-40d9-bbe6-9dbc0a5bf271)

</details>

<details><summary>Synthesis</summary>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/2e5f9c91-9cf8-46e9-9682-8e7f55c3fd32)

 
</details>

### D-FF With Asynchronous Set

<details><summary>Simulation</summary>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/82773a98-a6f1-4153-8d6d-d1c27ff504cc)

	
</details>

<details><summary>Synthesis</summary>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/6a93055f-84ef-42bf-800c-a816bc49e363)

 
</details>


### D-FF With Asynchronous and Synchronous Reset
<details><summary>Simulation</summary>

 ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/f2c634c4-174b-49ac-9ab5-c97c9bc9c56c)

</details>

<details><summary>Synthesis</summary>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/765cf848-a7b5-4ecf-bea0-c4e0f976d02e)

	
</details>

## Optimization



## Day 3

## Optimization
As we know that we have two types of logic design in digital either Combinational or sequential, we will go through both of them and understand how to optimize them
<details> <summary>Combinational Logic Optimization</summary>
We can optimize the combinational logic in following ways:
     
- Decreasing the area and power of the logic to get the most optimized design.  
 - Constant Propagation: We can propagate the constant values down the logic to get a more optimized design.
 - Boolean Logic Optimization: We can simplify the boolean expression to get a more optimized logic.
</details>

<details> <summary>Sequential Logic Optimization</summary>
We have the following ways to optiize sequential logic:
     
- Sequential Constant Propagation: Just like combinational circuits we can propagate the constant values down the logic.
- State Optimization: In state optimization, we can reduce the unused state.
- Cloning: Cloning refers to repicate the part of circuit so as to optimize the sequential logic design.+
- Retiming: Retiming optimizes the circuit by moving the registers in the circuits without affecting the functionality of the circuit.

</details>

## Lab Session On Combinational Logic Synthesis
This lab session focuses on optimizing the code by constant propagation. 
We will be using opt_clean to optimize the code as it will remove the unwanted cells and wires.

Example 1 : 
We have a verilog code for mux as shown below 
```
module opt_check (input a , input b , output y);
 assign y = a?b:0;
endmodule

```


<details><summary>Steps To Optimize:</summary>
     
```
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog opt_check.v
$ synth -top opt_check
$ opt_clean -purge
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr opt_check_net.v
$ !gvim opt_check_net.v
```

</details>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/6e428b8b-420a-4bb3-a2fc-476dbc515e30)
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/1f22b18f-02c5-4a3c-b20f-2b52ca944941)


Example 2:
We have a verilog code as shown below:
```
module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule

```

<details><summary>Steps To Optimize:</summary>
     
```
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog opt_check2.v
$ synth -top opt_check2
$ opt_clean -purge
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr opt_check2_net.v
$ !gvim opt_check2_net.v
```
</details>


![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/aeb8bbc0-6889-45ae-a87e-0646690d7a26)
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/c224542a-19c3-49cb-bfb4-51206aff8de6)


Example 3 : 
We have a verilog code as shown below: 
```
module opt_check3 (input a , input b, input c , output y);
	assign y = a?(c?b:0):0;
endmodule
```

<details><summary>Steps To Optimize:</summary>

```
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog opt_check3.v
$ synth -top opt_check3
$ opt_clean -purge
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr opt_check3_net.v
$ !gvim opt_check3_net.v
```


</details>


![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/e671d533-5f31-4a32-9d29-43dee8f6db02)
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/da7297d7-d9d0-4553-9e87-f3469fd582d7)


## Lab Session On Sequential Logic Optimization

This lab will introduce us to the ways by which we can optimize the sequential logic designs.

Example 1:
<details><summary>Steps to optimize:</summary>
```
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog dff_const1.v 
$ dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr dff_const1_net.v
$ !gvim dff_const1_net.v
```
</details>


![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/f3581087-1e27-454c-a7fa-ed2dfa6fd465)
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/751cf198-968b-4848-ad75-4b84359b72db)


Example 2:
<details><summary>Steps:</summary>
```
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog dff_const2.v 
$ synth -top dff_const2
$ dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr dff_const2_net.v
$ !gvim dff_const2_net.v
```
</details>


![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/4399f401-c706-40b8-83fb-5441b0141f97)


Example 3 :
<details><summary>Steps:</summary>

```
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog dff_const3.v 
$ synth -top dff_const3
$ dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr dff_const3_net.v
$ !gvim dff_const3_net.v
```
	
</details>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/79e348d4-26c0-4c39-b83e-beabcaee8889)
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/47211527-8c91-4dce-9f29-785d95f04f38)


# Optimization Of Unused States
Any logic which is not having direct connection with the primary output are optimized. In a circuit we can have one or more primary output and any logic which does not have any relation with primary output are optimized as shown below:

Example: 
For the verilog code shown below we don't need two bits and it will be optimized.
```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = count[0];

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```

<details><summary>Steps:</summary>
	
```
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog counter_opt.v 
$ synth -top counter_opt
$ dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr counter_opt_net.v
$ !gvim counter_opt_net.v

```

</details>

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/d3bc0b01-5adb-485c-aafa-19521bd5bd16)
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/1c2cc626-3fb9-4d8f-a36b-2b6a0b4bdef6)

Now we will compare the design when we are using all three bits of the counter. Copy and edit the code as below
Verilog Code:
```
module counter_opt (input clk , input reset , output q);
reg [2:0] count;
assign q = (count[3:0] == 3'b100);

always @(posedge clk ,posedge reset)
begin
	if(reset)
		count <= 3'b000;
	else
		count <= count + 1;
end

endmodule
```

<details><summary>Steps To Optimize:</summary> 
'''
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog counter_opt2.v 
$ synth -top counter_opt2
$ dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr counter_opt2_net.v
$ !gvim counter_opt2_net.v
```

</details>




## Day 4 - GLS, Blocking vs Non-blocking and Synthesis-Simulation mismatch

## Gate Level Synthesis(GLS)
- **What is GLS?**
     - Running the testbench with netlist as Design Under Test.
     - Netist is logically same as RTL Code.

- **Why GLS?**
     - To verify the logical correctness of design after synthesis.
     - To ensure the timing of the design is met using delay annotation.
 
  ## Synthesis- Simulation Mismatch
  - **How Synthesis-Simulation Mismatch happen?**
      - Missing senstivity list
      - Blocking vs Non blocking assignment
      - Non standard verilog coding

 ## Blocking and Non- blocking Statements
  It affects the code only when we are using it in always block
- Blocking Statements:
  - Represented by "=".
  - Executes the statement in which the order is written.
- Non-Blocking Statements:
   - Reprsented by "<="
   - Executes all the RHS when always block is entered and assigned to LHS.
   - Parallel execution.
 
  ## Labs on GLS and Synthesis-Simulation Mismatch

  **Example 1:** <br>
  We have a verilog code for mux using the ternary operator. We will first simulate it and observe its behaviour.
  <details><summary>Steps For Simulation</summary>

  ```
  $ iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
  $ ./a.out
  $ gtkwave tb_ternary_operator_mux.vcd
  ```

  The verilog code and RTL simulation is shown below:

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/58ee5195-e9b7-444c-9a52-099ed0a66a0a)

</details>

  Now we will invoke yosys and create a netlist as shown below
  <details><summary>Steps For creating A Netlist</summary>
	  
```
$ yosys
$ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog ternary_operator_mux.v 
$ synth -top ternary_operator_mux
$ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
$ show
$ write_verilog -noattr ternary_operator_mux_net.v
$ !gvim ternary_operator_mux_net.v
 ```

 ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/a655fdfc-f149-49d4-bb6c-a11822cf5f5d)

  </details>
  
   Now we will do the gate level synthesis (GLS) as shown below:

   <details><summary>Steps To Do GLS:</summary>

   ```
   $ iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux.v tb_ternary_operator_mux.v
   $ ./a.out
   $ gtkwave tb_ternary_operator_mux.vcd
  ```

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/7c590ccd-93cf-4d88-a832-cc5161116b9c)


   </details>

   In this example there is no mismatch in Synthesis and simulation.

  **Example 2:** <br>
   In this example we have a mux created using the if-else condition, we will then compare the synthesis and simulation results.

  <details><summary>Steps For Simulation</summary>

  ```
  $ iverilog bad_mux.v tb_bad_mux.v
  $ ./a.out
  $ gtkwave tb_bad_mux.vcd
```

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/7aacf0cd-6c47-4085-822f-7295a4a93da2)



  </details>

  Now we will do the gate level synthesis (GLS) as shown below:

  <details><summary>Steps For Creating a Netlist</summary>
	  
  ```
  $ yosys
  $ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
  $ read_verilog bad_mux.v
  $ synth -top bad_mux
  $ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
  $ show
  $ write_verilog -noattr bad_mux_net.v
  $ !gvim bad_mux_net.v
  ```

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/1e7e59bc-d7f3-406d-a63e-4d851d175ada)

  
</details>


Now we will do the gate level synthesis (GLS) as shown below:

   <details><summary>Steps To Do GLS:</summary>

   ```
   $ iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v
   $ ./a.out
   $ gtkwave tb_bad_mux.vcd
  ```

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/aad98179-8b2e-429e-b2aa-bb7db62978ff)


</details>


## Labs on Synthesis-Simulation Mismatch for blocking statement

Verilog Code:

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

    
 <details><summary>RTL Simulation:</summary>


Steps:

    ```
    $ iverilog blocking_caveat.v tb_blocking_caveat.v
    $ ./a.out
    $ gtkwave tb_blocking_caveat.vcd 
    ```

    
 ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/b7d972f3-aabd-4e6e-935a-9258eddf4287)
    

</details>

 <details><summary>GLS:</summary>
    
 Steps:
    
    ```
    $ yosys
    $ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    $ read_verilog blocking_caveat.v
    $ synth -top blocking_caveat
    $ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
    $ show
    $ write_verilog -noattr blocking_caveat_net.v
    $ !gvim blocking_caveat_net.v
    $ exit
    $ iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
    $ ./a.out
    $ gtkwave tb_blocking_caveat.vcd
    ```

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/65322439-b972-454c-b3bb-bb0200b9fae7)


</details>

## Day 5 - If, Case, For loop and For Generate
## If Statements
- It is mainly used to create priority logic.
- Syntax:
  ```
   if (condition)
       begin
       // Code to be executed if the condition is true
       end
   else
       begin
       // Code to be executed if the condition is false
       end
  ```
 - **Precautions with "If"** <br>
     Due to incomplete if statements i.e. when we use "if" without "else" statements, it inferes latches which affects the working of code. But there are some      conditions where we require latches like counters.
- **Lab Session On Incomplete IF Statement:** <br>

Example 1: <br>

<details><summary>Verilog Code</summary>
	   
```
    module incomp_if (input i0 , input i1 , input i2 , output reg y);
    always @ (*)
    begin
	if(i0)
		y <= i1;
    end
    endmodule
 ```
	    
</details>

<details><summary>RTL Simulation</summary>
    
Steps:
```
    $ iverilog incomp_if.v tb_incomp_if.v 
    $ ./a.out
    $ gtkwave tb_incomp_if.vcd
 ```

 ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/feb4562e-c152-4e00-8b8e-97c5254cdc92)

	    
</details>

<details><summary>Synthesis</summary>

Steps:
 ```
    $ yosys
    $ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    $ read_verilog incomp_if.v
    $ synth -top incomp_if
    $ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
    $ show
    $ write_verilog -noattr incomp_if_net.v
    $ !gvim incomp_if_net.v
  ```

 ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/5cbfc724-d0c9-44b3-9279-54c17736c2e7)


	    
 </details>

 Example 2:
 
 <details><summary>Verilog Code</summary>
	   
```
   module incomp_if2 (input i0 , input i1 , input i2 , input i3, output reg y);
   always @ (*)
   begin
	if(i0)
		y <= i1;
	else if (i2)
		y <= i3;

   end
   endmodule
 ```
	    
</details>

<details><summary>RTL Simulation</summary>
    
Steps:
```
    $ iverilog incomp_if2.v tb_incomp_if2.v 
    $ ./a.out
    $ gtkwave tb_incomp_if2.vcd
 ```

 ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/85e7afc4-926d-494d-8862-2d891268c008)

</details>

<details><summary>Synthesis</summary>

Steps:
 ```
    $ yosys
    $ read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    $ read_verilog incomp_if.v
    $ synth -top incomp_if
    $ abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
    $ show
    $ write_verilog -noattr incomp_if_net.v
    $ !gvim incomp_if_net.v
  ```

![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/f82ea0b2-50a8-4adb-a963-403a69ee0006)

</details>

## Case Statements
- It is used in "always" block.
- Variable which is used in case statement shoul be a reg.
- Syntax:
  ```
   case(choice)
     choice1: begin
     --------
     --------
     end
     choice2: begin
     --------
     --------
     end
     default: <statements>
   endcase
  ```
- **Precautions with "Case"** <br>
    - Incomplete case also inferes latches and to avoid that we should use default statement in case.
    - Partial Assignments: If some of the outputs are not assigned any value in some of the segments of case then it inferes latches which can affect the working of code.
    - We should not have overlapping cases as unlike "If" statements no priority is given to any condition hence it will check all the cases even if it matches the one condition, which in return gives unpredictable outputs.

- **Lab Session On Incomplete Case Statement:** <br>

     Example 1: <br>
     <details><summary>Simulation</summary>

     ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/4f3a3718-21ce-4141-8f6d-52cae8acf394)

	     
     </details>

     <details><summary>Synthesis</summary>
	     
     ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/7174e9a0-7e49-4978-98fb-e984f1af0845)

     ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/e51e1436-4244-429a-a3c6-5feba5044881)

	     
     </details>

- **Lab Session On Complete Case Statement:** <br>
     Example 1: <br>
     <details><summary>Simulation</summary>

     ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/85a54b4c-9d7b-4ba6-a2eb-bf83d8113c30)


     </details>
     
     <details><summary>Synthesis</summary>

     ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/ad466c3e-00f9-428c-ab3e-63ecb8231813)

     ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/b6205c1a-ab02-4dd9-9993-1974249e815b)


     </details>

- **Lab Session On Partial Complete Case Statement:** <br>
    Example 1:<br>
    <details><summary>Simulation</summary>

    ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/dfac7c70-171d-4b7d-aea0-7ae79cf60e78)

  </details>

  <details><summary>Synthesis</summary>

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/15b7eb44-dedc-4bbd-ab6a-89fdc41bca74)

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/9d1ff067-01f5-4737-9c93-69ecdca158dc)
	  
  </details>
  


  


    
      
## For Loop:
- It is used in "always" block.
- It is used for evaluating expression multiple times.
- Syntax:
  ```
  for (<initiaization>, <condition>, <update>)begin
   \\ expression to be evaluated
  end
  ```
- **Lab Session**
  
   Example 1
  <details><summary>Simulation</summary>

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/3e8837e7-c108-49e3-be22-a3734bb10f3a)

	  
  </details>

  <details><summary>Synthesis</summary>

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/6e38b8da-e195-4cb4-a5df-cf9b351baaae)

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/5b71e649-bc36-4f76-97ab-3a2b3e1a649a)

  </details>

  Example 2<br>

  <details><summary>Simulation</summary>

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/6f017f11-b86f-4d45-8e1b-db8437f1a181)

  </details>

  <details><summary>Synthesis</summary>
	  
  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/7b4d7b81-838c-400a-8d27-fa6a9835ddae)

  ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/3e33a8bc-c0fc-4f2f-9ae7-510999056df9)


	  
  </details>



  


## Generate For Loop:
- It is used outside the "always" block.
- It is used for instantiating hardware multiple times.
- Syntax:
  ```
  genvar k;
  generate 
      for (k = 0; k < 4; k++) begin
         \\ statements to be executed
         end
     end
  endgenerate
  ```
- **Lab Session**

   Example 1
   <details><summary>Simulation</summary>
   
    ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/34929b7e-929a-42d6-824d-046b027a7324)

	   
   </details>

   <details><summary>Synthesis</summary>
   
    ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/145ea72e-601d-48bf-89f2-e19f88aac76d)

    ![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/c90c697e-9948-475e-835d-191e71ea74bf)


	   
   </details>

 
  


    
