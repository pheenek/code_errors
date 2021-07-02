
# Errors encountered in avr

## 1. Undefined behaviour with UDRIE (USART Data Register Empty Interrupt)
	- The USART continuously tranmits the buffer

	### Solution:
	- The UDRE flag is set by default.
	- Set the UDRIE bit only when you're ready to begin transmission
	- Disable the UDRIE bit when done transmitting

## 2. To add native floating point number support
	- Add the compiler/linker options
	
	CFLAGS += -Wl,-u,vfscanf,-lscanf_flt,-u,vfprintf,-lprintf_flt
	
