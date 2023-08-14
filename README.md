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
- Combinational Logic Optimization
- Sequential Logic Optimization

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
This lab session focuses on optimizing the code for a mux to an and gate by constant propagation. 
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
```


</details>


![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/e671d533-5f31-4a32-9d29-43dee8f6db02)
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/da7297d7-d9d0-4553-9e87-f3469fd582d7)





