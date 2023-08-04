# Tapeout Process 
## Day 0

<details><summary>Install all the required softwares for vsd design</summary>
  1. Yosys
   2. Iverilog<br>
      3. GTKWave<br>
      4. Ngspice<br>
      5. OpenSTA<br>
6. Magic<br>
7. OpenLane<br>
</details>

## Day 0
<details> <summary><strong>Installation Of Yosys</strong></summary>
<br>
 
Steps:
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


<details> <summary><strong>Installation Of Iverilog</strong></summary>
<br>
Steps:

 ```
   $ sudo apt-get install iverilog
```
 
![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/d72c451e-f951-458e-bfae-0a46b7505299)
</details>

<details> <summary><strong>Installation Of GTKWave</strong></summary>
<br>
 Steps: 

```
  $ sudo apt update

  $ sudo apt install gtkwave
```


![image](https://github.com/Nancy0192/nancy_iiitb_asic/assets/140998633/0dec3ee9-fd93-45d5-a678-fc778af882b5)

</details>



<details> <summary><strong>Installation Of Ngspice</strong></summary>
<br>
Steps:

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

 
<details> <summary><strong>Installation Of OpenSTA</strong></summary>
<br>
Steps:

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


<details> <summary><strong>Installation Of Magic</strong></summary>
<br>
Steps:

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

<details> <summary><strong>Installation Of OpenLane</strong></summary>
<br>
Steps:

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


