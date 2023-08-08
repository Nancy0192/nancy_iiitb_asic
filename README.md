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
- Cloning Of Github folder
- Simulation - Using Iverilog and GTKWave
- Synthesis - Using Yosys


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
The following github repository contains all collaterals for RTL Design and Synthesis Workshop using Sky130 PDK's.
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

