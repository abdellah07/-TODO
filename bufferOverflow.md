# Classifying vulnerabilities
    • Memory corruption (safety)
        – Buffer Overflow
        – Integer Overflow
        – Stack Overflow
        – Use after free/ Double free
        – Null pointer dereference

    • Exploiting memory corruption to control program
        – Format string attacks
        – Stack buffer overflow (or stack-based buffer overflow)
        – Heap buffer overflow (or heap-based buffer overflow)
        – Overflowing on non “control-data” memory
    • Resulting attacks
        – Code injection on the stack (e.g., shellcodes)
        – Code reuse techniques (Return-to-libc, Return-Oriented
        Programming, Jump-Oriented Programming

# Buffer Overflows: usual suspects
    – gets(), strcpy(), …
    – memcpy()
    – zero-sized malloc()s … …
    
# Preventing Buffer Overflows
    • Safe usage of copy primitives using libc methods
        – For instance, limit amount of data to copy
        – strncpy(tmp_buff, src, sizeof(tmp_buf))

    • Compiler extension if array length can becomputed

# Integer overFlows
    • Unsigned ints
        – 32 bits: range from 0 to 2^32-1 (4,294,967,295)
        – Overflow: 4,294,967,295 + 1 = 0
    • Signed ints
        – 32 bits: range from − (2^31) to 2^31 − 1 (2,147,483,647)
        – Overflow: 2,147,483,647+2 = -2,147,483,648
    • Some languages (Java, Ada) throw exceptions, many don't


# stack overflow 
    • Stack Overflows can be caused by:
        – Recursive calls
        – Reentrant interrupts
        – Allocations on the stack
            • Large
            • Controlled by the attacker
            • Alloca(), char array[function_parameter]

    • This should never happen ?
    • Detection : guard page (Unix)
        – Problem when allocation is too large
    • the stack pointer can “jump over” the guard page
    • Prevention: Not so easy
        – Abstract interpretation [Regehr05]
    • Works as long as control flow can be determined statically
        – Forbid / bound recursion
        – Forbid / limit allocation on the stack
    • Problem with micro-controllers
        – No MMU (Memory Management Unit)

# Stack Buffer Overflow / Overrun
    • A special case of buffer overflow
        – Exploitation of existing vulnerability in order to modify control flow
    • The overflowed buffer is allocated on the
        stack, typically corrupts return address
    • First wide-scale exploitation: Morris’ worm
    (1989) in Unix’s fingerd

# Consequences of Buffer Overflow
    Overwriting return address with some random address can point to :
        • Invalid instruction
        • Non-existing address
        • Access violation
        • Attacker’s code Malicious code to gain access


# More on Modifying return address
    • Not always easy to know the exact address
    • Trampolines :
        – jmp %esp at a fixed address
    • NOP sled
        – A long sequence of NOP
        – Followed by the shellcode
        – Jumping anywhere in there leads to the shellcode

# Exploiting Stack Buffer Overflows
    • Corrupting the Control Flow
    • Corrupting the Program State (other stack frames)


# protection 
    Protections: Canaries
        • Objective : Detect unexpected modifications of values on the stack (e.g., return address)
        • Inserting a known value on the stack
            – the “canary”
        • Compiler extension - inserts code that:
            – Adds a random value after the return address
            – Checks canary value before using return address
        • Limitations
            – Canaries can be guessed or obtained
        through memory leaks
            – Canary copy needs to be stored in secure place that might also be corrupted

        

        Protections: Non Executable Memories (Writable XOR Executable / NX)
            – OS splits memory regions – no region is both writable and executable
            • Defeated by Return-to-libc attacks / Return Oriented programming

        
        Protections: ASLR (Address Space Layout Randomization)
            • Randomizes base addresses of memory segments
                – Addresses change at every execution
            • Randomize start or base address of:
                – Program code
                – Libraries code
                – Heap/Stack/Data regions

            • Objectives:
                – Difficult to guess the stack address in the memory.
                – Difficult to guess %ebp address and address of the malicious code 
            
            • Limitations
                – Memory leaks used to learn memory layout
                – Address space / system limitations (e.g., page boundaries) may allow brute- force probes