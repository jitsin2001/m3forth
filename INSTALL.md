# INSTALLATION

## ARM toolchain
Get the ARM toolchain (this is GCC with utilities for ARM), e.g. [here](https://launchpad.net/gcc-arm-embedded). It's not needed if you don't want to debug your apps.
Unpack it to any folder, e.g. \~/arm. Add this to **\~/.bashrc**:
```bash
if [ -d "$HOME/arm/bin" ] ; then
    PATH="$HOME/arm/bin:$PATH"
fi
```
Log off, and log in. The toolchain is enabled.

## ST-link
Get the **st-link** to flash the controller. Download it [here](https://github.com/texane/stlink/), unpack, then compile it:
```bash
$ ./autogen.sh
$ ./configure
$ make
```
Make **/etc/modprobe.d/usb-storage** file:
```bash
options usb-storage quirks=483:3744:i
```
Reload **usb-storage** kernel module
```bash
sudo modprobe -r usb-storage
sudo modprobe usb-storage
```

## qEMU
Get **qEMU** for ARM to debug your programs without a real device. Install **qemu-system-arm** package using your package manager.

## libelf
Get **libelf1** library for elf-files production. In most cases you should just install **libelf1** package.

## libdwarf
Get **libdwarf1** library for debug symbols generation. In most cases you should just install **libdwarf1** package.  For 64-bit Linux install 32-bit package!

## ddd
Get **ddd** (data display debugger). Install **ddd** package.

## openocd
Get **openocd** if you want to get USB connection to your device via semihosting and program in Forth on you device directly!. You can get it [here](http://sourceforge.net/projects/openocd). Unpack and compile:
```bash
./configure
make
sudo make install
```
## test
To test your installation go to **examples/tester** and run:
```bash
make test
```
