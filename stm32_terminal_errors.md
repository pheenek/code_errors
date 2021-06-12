
# Errors:

## 1. embedded:startup.tcl:60: Error: Can't find openocd.cfg
Don't forget the '-f' command option for specifying the configuration file

	openocd -f <config-file-name>
	
## 2. arm-none-eabi-gdb error while loading shared libraries libncurses.so.5
Make sure that you have the correct version of libncurses for your PC. Try:

	sudo apt-get install libncurses5:amd64
