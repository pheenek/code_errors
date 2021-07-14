
# Errors encountered in avr

## 1. Undefined behaviour with UDRIE (USART Data Register Empty Interrupt)
- The USART continuously tranmits the buffer contents

### Solution:
- The UDRE flag is set by default.
- Set the UDRIE bit only when you're ready to begin transmission
- Disable the UDRIE bit when done transmitting

## 2. To add native floating point number support
- Add the compiler/linker options

### Solution
	CFLAGS += -Wl,-u,vfscanf,-lscanf_flt,-u,vfprintf,-lprintf_flt
	
## 3. Compilation error when using assembly:
	relocation truncated to fit: R_AVR_7_PCREL against 'no symbol'
	
### Solution
- Apparently the assembly commands have a limitation for the number of words they can skip over.
- For the branch commands, it's 64 words, while an rjmp command (relative jump) can do up to 1k words.
- The solution is to stick within the limits for the number of words that the command can skip over
	
