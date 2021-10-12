
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
	

## 4. Undefined reference to C functions in Arduino
- That's honestly the only description I could find for this error so far.
- The issue manifests as a linking error, with the following error at compilation:
	<pre><code>
	/tmp/ccRK4E5M.ltrans0.ltrans.o: In function `global constructors keyed to 65535_0_fingerprint_touch_driver.c.o.4497':
	</code></pre>
	
- It seems like it's been a while since I've mixed C code with C++ code. I had forgotten a small but crucial part to calling C code in C++ code:
	<pre><code>
	#ifdef __cplusplus
		extern "C" {
	#endif
	</code></pre>
	
- This presents a name-mangling problem since we're using a C++ compiler to compile the C code
- I hope for the sake of my sanity, I don't forget this again
