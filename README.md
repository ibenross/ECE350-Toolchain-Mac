# ECE350 ToolChain Installation for Mac
## Quick Start
To run, double click on the setup.command file. Installation takes ~5 minutes to complete and may require your password to install some components. The script installs the following:
- Xcode Command Line Tools
- Homebrew
- OpenOCD
- USB FTDI Drivers
- Icarus Verilog 
- GTKWave
If you wish to install the software yourself, follow the instructions below.

## Manual Installation
### Installing Homebrew
Installing Homebrew will also install the Xcode Command Line Tools. You can install them using this process or install them manually yourself.
1. In a termianl window, enter
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

### Installing Command Line Tools
1. Install Xcode (install from the AppStore)
2. from Xcode -> Preferences -> Downloads

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;or

1. In a terminal window, enter

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`xcode-select --install`

### Installing GTKWave
1. Copy the gtkwave.app folder to your applications folder
2. Right click and select open

### Installing OpenOCD
`brew install --HEAD openocd`
#### Test that it works 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`openocd --version`

Output should look as follows, with your installation date
```
Open On-Chip Debugger  v0.10.0-esp32-20200526-6-g4c41a632 (2020-06-22-18:14)
Licensed under GNU GPL v2
For bug reports, read
	http://openocd.org/doc/doxygen/bugs.html
```
The repository includes files necessary to use OpenOCD as well as a python wrapper to expedite the programming process.

### Installing USB Drivers
1. Download the Drivers for Mac OSX 10.4 Tiger or later [here](https://www.ftdichip.com/Drivers/D2XX/MacOSX/D2XX1.4.16.dmg)
2. Open the dmg file and open a terminal at the D2XX folder by 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Right Clicking -> New Terminal at Folder
  
3. If the directory /usr/local/lib directory doesnt exist, use

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`sudo mkdir /usr/local/lib`

4. If the directory /usr/local/include directory doesnt exist, use

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`sudo mkdir /usr/local/include`

5. Copy the following files into the directories you just created and create a link so OpenOCD can find them
```
sudo cp libftd2xx.1.4.16.dylib /usr/local/lib/
sudo cp ftd2xx.h /usr/local/include/ftd2xx.h
sudo cp WinTypes.h /usr/local/include/WinTypes.h
sudo ln -sf /usr/local/lib/libftd2xx.1.4.16.dylib /usr/local/lib/
```
