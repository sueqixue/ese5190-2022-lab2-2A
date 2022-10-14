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

To install the toolchain to build, follow the tutorial of **9.2. Building on MS Windows** in [Getting-started-with-pico.pdf](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf).  
Besides, download **the Visual Studio 2022** from the Microsoft Store if needed.

#### 2.1 Download Executable Installers
Tools | State
:---: | :---:
[Arm GNU](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/downloads) | Need to download
[CMake](https://cmake.org/download/) | Need to download
[Build Tools for Visual Studio 2022](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022) | Need to download
[Python 3.10](https://www.python.org/downloads/windows/) | Already exist
[Git](https://git-scm.com/download/win) | Already exist

#### 2.2 Installing
##### 2.2.1 Installing Arm GNU Toolchain
1. Run the GNU executable installer.  
2. Tick the box `Show Readme`.
3. Tick the box `Launch gccvar.bat`.
4. Tick the box `Add path to environmnet variable`.
5. Tick the box `Add registry information`.
6. Choose to install GNU on `C:\`.  
<img src="https://github.com/sueqixue/ese5190-2022-lab2-2A/blob/main/2.2.1.png" alt="GNU" width="400"/>

##### 2.2.2 Installing CMake
1. Run the CMake executable installer.  
2. Tick the circle `Add CMake to the system PATH for all users`.
<img src="https://github.com/sueqixue/ese5190-2022-lab2-2A/blob/main/2.2.2.png" alt="CMake" width="400"/>


##### 2.2.3 Installing Build Tools for Visual Studio 2022
1. Run the Build Tools executable installer.  
2. Tick the box `Desktop development with C++`.
3. Remember install the C++ build tools only.
<img src="https://github.com/sueqixue/ese5190-2022-lab2-2A/blob/main/2.2.3.png" alt="Build_tools" width="600"/>

### 3. Getthing the SDK and examples

Create a log for the examples. For me, I created the log in my **C:\Users\xue_q\Downloads** instead of the **C:\Users\xue_q\Document**. This is because my **Document** folder linked to my **OneDrive**, which has a defualt language of Chinese and I do not quite sure how to change that[^1]. 

Open the **Terminal** app on PC and run as follows:

```
C:\Users\xue_q\Downloads\lab2> git clone -b master https://github.com/raspberrypi/pico-sdk.git
C:\Users\xue_q\Downloads\lab2> cd pico-sdk
C:\Users\xue_q\Downloads\lab2\pico-sdk> git submodule update --init
C:\Users\xue_q\Downloads\lab2\pico-sdk> cd ..
C:\Users\xue_q\Downloads\lab2> git clone -b master https://github.com/raspberrypi/pico-examples.git
```

### 4. Building "Hello World" from the Command Line

#### 4.1 Set the Path to the SDK
Open the **Developer Command Prompt for VS 2022** by searching for it in the Windows search box and set the path to the SDK as follow:

```
C:\Users\xue_q\Downloads\lab2> setx PICO_SDK_PATH "..\..\pico-sdk" 
```

#### 4.2 Set the Environment Variables
Then, close the current **Developer Command Prompt** window and open a second **Developer Command Prompt** window and set the environment variables as follows:

```
C:\Users\xue_q\Downloads\lab2> cd pico-examples
C:\Users\xue_q\Downloads\lab2\pico-examples> mkdir build
C:\Users\xue_q\Downloads\lab2\pico-examples> cd build
C:\Users\xue_q\Downloads\lab2\pico-examples\build> cmake -G "NMake Makefiles" ..
C:\Users\xue_q\Downloads\lab2\pico-examples\build> nmake
```

The command line should look like this if build successfully:
<img src="https://github.com/sueqixue/ese5190-2022-lab2-2A/blob/main/4.2.jpg" alt="Build_right" width="600"/>

### 5. Run "Hello World" on the RP2040

#### 5.1 Plug in RP2040 and Check Ports
1. Plug only RP2040 using a micro-USB cable in without the sensor, hold down the `BOOTSEL` button to force it into USB Mass Storage Mode. 
2. Open **Device Manager** by searching for it in the Windows search box.
3. **Important:** Check the port hte RP2040 uses. In my case, it is COM6, which is differnet from the port RP2040 used during Lab1[^2]:
<img src="https://github.com/sueqixue/ese5190-2022-lab2-2A/blob/main/5.1.jpg" alt="PuTTy_setting" width="600"/>

#### 5.2 Run "Hello World"
Copy the C:\Users\xue_q\Downloads\lab2\pico-examples\build\hello_world\usb\hello-usb.uf2 file and paste it to the RP2040.  
Then, open the serial console and the code is running as follow:
<img src="https://github.com/sueqixue/ese5190-2022-lab2-2A/blob/main/5.2.jpg" alt="Run_right" width="600"/>

### 6. Quirks and Tips
[^1]: If the path of your build directory contains characters that CMake cannot recognize, such as Chinese characters, `cmake` in the following steps will fail. Thus, make sure no such characters involving the log.
[^2]: I first directly used my saved puTTy configuration and the serial console cannot connected to the device successfully. I did not know that the port occupied by the same external drive can change so I wasted some time on this. Thus, double check the port before open the serial console.
