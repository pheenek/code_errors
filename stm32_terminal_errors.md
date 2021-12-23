
# Errors:

## 1. embedded:startup.tcl:60: Error: Can't find openocd.cfg
Don't forget the '-f' command option for specifying the configuration file

	openocd -f <config-file-name>
	
## 2. arm-none-eabi-gdb error while loading shared libraries libncurses.so.5
Libncurses is an API that provides support for text-based UIs, used in arm-none-eabi-gdb. The amd-64 version provides support for x86-64 OS.
Make sure that you have the correct version of libncurses for your PC. Try:

	sudo apt-get install libncurses5:amd64
	
## 3. HardFault while debugging
Ensure that the correct linker script and startup file are being used while compiling.

## 4. arm-none-eabi-gdb: timed out while waiting for target halted
Set the reset to occur internally over the SWD channel with no pins used. Use the command:

	reset_config none separate
