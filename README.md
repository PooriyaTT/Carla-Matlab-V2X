# Carla-Matlab-V2X
*Accurate and robust logical driving behavior based on V2I communication for Connected &amp; Autonomous Transport (CAT) at XL business park*                                                                

Carla is a software program designed for researching autonomous driving that is available for free use and modification. Its interface is robust and enables the development, training, and validation of autonomous driving systems. On the other hand, MATLAB, which is widely utilized, particularly by engineers, requires no introduction. Its numerous features facilitate rapid product development. Therefore, in this work a combination of these two software was used to create V2I application.

Requirments
---
Software Requirements:

•	Operating System: Ubuntu 20.04.5 LTS.

•	CARLA Simulator: The CARLA 0.9.13 version of the simulator was used in this project. This version of the simulator provides a stable and reliable environment for simulating autonomous driving scenarios.

•	Python: Python 3.8.10 was used as the programming language for the CARLA simulator. This version of Python provides a robust and flexible environment for developing and testing autonomous driving algorithms.

•	Unreal Engine: Unreal Engine 4.26.2 was used as the game engine for the CARLA simulator. This version of the engine provides high-quality graphics and physics simulation capabilities for creating realistic autonomous driving scenarios.

•	Roadrunner 2022b was used to create road network

•	MATLAB 2020b

Hardware Requirements:

•	Processor: Intel® Core™ i7-11800H (2.4 GHz base clock, up to 5.0 GHz max turbo frequency, 8 cores, 16 threads)

•	Graphics Card: NVIDIA® GeForce® RTX 3070 (8 GB GDDR6 memory)

•	Memory: 32 GB DDR4-3200 SDRAM (2 x 16 GB)

•	Storage: 1 TB PCIe® NVMe™ M.2 SSD

Software  requirements 
---

CARLA requires many different kinds of software to run. Some are built during the CARLA build process itself, such as Boost.Python. Others are binaries that should be installed before starting the build (cmake, clang, different versions of Python, etc.). To install these requirements, run the following commands:
```
sudo apt-get update &&
sudo apt-get install wget software-properties-common &&
sudo add-apt-repository ppa:ubuntu-toolchain-r/test &&
wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key|sudo apt-key add - &&
sudo apt-add-repository "deb http://apt.llvm.org/xenial/ llvm-toolchain-xenial-8 main" &&
sudo apt-get update
```

To avoid compatibility issues between Unreal Engine and the CARLA dependencies, use the same compiler version and C++ runtime library to compile everything. The CARLA team uses clang-8 (or clang-10 in Ubuntu 20.04) and LLVM's libc++. Change the default clang version to compile Unreal Engine and the CARLA dependencies.

```
sudo apt-add-repository "deb http://apt.llvm.org/focal/ llvm-toolchain-focal main"
sudo apt-get install build-essential clang-10 lld-10 g++-7 cmake ninja-build libvulkan1 python python-dev python3-dev python3-pip libpng-dev libtiff5-dev libjpeg-dev tzdata sed curl unzip autoconf libtool rsync libxml2-dev git
sudo update-alternatives --install /usr/bin/clang++ clang++ /usr/lib/llvm-10/bin/clang++ 180 &&
sudo update-alternatives --install /usr/bin/clang clang /usr/lib/llvm-10/bin/clang 180
```

Starting with CARLA 0.9.12, users have the option to install the CARLA Python API using pip or pip3. Version 20.3 or higher is required. To check if you have a suitable version, run the following command:

```
pip3 -V
```

If you need to upgrade:
```
pip3 install --upgrade pip
```

You must install the following Python dependencies:
```
pip install --user setuptools &&
pip3 install --user -Iv setuptools==47.3.1 &&
pip install --user distro &&
pip3 install --user distro &&
pip install --user wheel &&
pip3 install --user wheel auditwheel
```

Unreal engine Installation
---
Starting with version 0.9.12, CARLA uses a modified fork of Unreal Engine 4.26. This fork contains patches specific to CARLA.

Be aware that to download this fork of Unreal Engine, you need to have a GitHub account linked to Unreal Engine's account. If you don't have this set up, please follow the following steps.

![un](https://user-images.githubusercontent.com/115306756/220687313-a664fbe5-458d-43ab-aaa3-fa43e5e8242e.jpg)

When you follow the steps as mentioned above you need to get a personal token for cloning the Unreal engine which will be your password requested in the terminal during executing the following code which is the first step of installing unreal engine.

1. Clone the content for CARLA's fork of Unreal Engine 4.26 to your local computer:
```
git clone --depth 1 -b carla https://github.com/CarlaUnreal/UnrealEngine.git ~/UnrealEngine_4.26
```
At this stage you are propmpet to use your username and password (your user name is your email which you use for Github and Unreal engine during the previous steps and for Password following steps are required)


![git2](https://user-images.githubusercontent.com/115306756/220688510-e358ce5f-1a8e-4824-bb00-78427bd05054.jpg)

after clicking on generating the token you will se a code which will be your persoanl token and it should be coppied and pasted to the terminal to start cloning the unreal engine.

2. Navigate into the directory where you cloned the repository:
```
 cd ~/UnrealEngine_4.26
```
3. Make the build. This may take an hour or two depending on your system.
```
./Setup.sh && ./GenerateProjectFiles.sh && make
```
4. Open the Editor to check that Unreal Engine has been installed properly.
```
 cd ~/UnrealEngine_4.26/Engine/Binaries/Linux && ./UE4Editor
```
At this stage you should be able to have Unreal Engine up and running.

Installing CARLA
---

Downloading aria2 with ```sudo apt-get install aria2 ```will speed up the following commands.

1.Clone CARLA using the following command:

```git clone https://github.com/carla-simulator/carla```

2.You will need to download the latest assets to work with the current version of CARLA. We provide a script to automate this process. To use the script, run the following command in the CARLA root folder:

```./Update.sh```
![ca](https://user-images.githubusercontent.com/115306756/220690846-57562383-9c9a-4a73-bfd1-9c3d6b241017.jpg)

3.Set Unreal Engine environment variable: For CARLA to find the correct installation of Unreal Engine, we need to set the CARLA environment variable.

   1. Open ~/.bashrc or ./profile with the following code: ```  gedit ~/.bashrc``` or ```  gedit ~/.profile```
   2. Add the following line to the bottom of the file: ``` export UE4_ROOT=~/UnrealEngine_4.26  ``` 
   3. Save the file and reset the terminal.
