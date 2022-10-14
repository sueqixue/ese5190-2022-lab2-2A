# ese5190-2022-lab2-2A

## Part II - Setup

### 1. Machine details

Details | My PC
:---: | :---:
Device | Alienware x15 R1
OS| Windows 11 Home
Processor | 11th Gen Intel(R) Core(TM) i7-11800H @2.3GHz
System | 64-bit operating system, x64-based processor


### 2. Toolchain

To install the toolchain to build, I followed the tutorial of **9.2. Building on MS Windows** in [Getting-started-with-pico.pdf](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf).  
Besides, I also downloaded **the Visual Studio 2022** from the Microsoft Store on my PC.

#### 2.1 Download the executable installers
Tools | State
:---: | :---:
[Arm GNU](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/downloads) | Need to download
[CMake](https://cmake.org/download/) | Need to download
[Build Tools for Visual Studio 2022](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022) | Need to download
[Python 3.10](https://www.python.org/downloads/windows/) | Already exist
[Git](https://git-scm.com/download/win) | Already exist

##### 2.1.1 Installing Arm GNU Toolchain
1. Run the GNU executable installer.  
2. Tick the box `Show Readme`.
3. Tick the box `Launch gccvar.bat`.
4. Tick the box `Add path to environmnet variable`.
5. Tick the box `Add registry information`.
6. Choose to install GNU on C:\.


##### 2.1.2 Installing CMake
1. Run the CMake executable installer.  
2. Tick the circle `Add CMake to the system PATH for all users`.

