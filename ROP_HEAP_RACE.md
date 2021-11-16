# Return-to-libc Attack
    • NX (W XOR X) makes it impossible to inject one’s code and execute it.
        – No memory regions that are writeable and executeable
    • Idea : Reuse existing code
        – “Fortunately” libc loaded at a constant address
        – Divert control flow of exploited program into libc code
        – “Load” parameters on the stack
        – No code injection required: Jump to a known address
    • exec(), system(), printf()
    • For example:
        – Exec(“/bin/sh”)
    
    Overwrite return address withaddress of libc function
    • setup fake return address and argument(s)
    • ret will “call” libc function
    No injected code!

# Return-Oriented Programming (ROP)
    ROP: Approach
        • Most directly inspired by Borrowed code chunks [Krahmer 2005]
            – Find short sequences of instructions that allow to
                perform some given operations
            – Termed Gadgets
            – “Chain” them together using “ret”
        • JOP attack = use jmp instead of ret

        • A Turing complete set of gadgets allows to perform arbitrary computation\
            – Exploits are not straight-line limited
            – Showed to work on most architectures
            – Equivalent to having a virtual machine/interpreter
        • Calls no functions at all
            – can’t be defeated by removing functions like system()
            – Must know the memory map (no ASLR)
            – Need to find interesting gadgets and to chain them in a given order
        • Specific compilers (e.g. ROPC)
            – Automation techniques to find those sequences of code

    ROP: consequences & protection
        • Malicious code detection cannot be limited to executable memory regions
            – Return oriented rootkits / malicious code…
            – Even non executable memories need to be verified
        • ROP defeated by ASLR
            – chaining returns needs to know addresses in advance
        • Blind ROP
            – It is possible to learn where are the gadgets, brute force and monitor side effects
            – Stack learning overwrite a byte at a time and bruteforce it.

          
# HEAP BUFFER OVERFLOWS
    • The heap is the pool of memory used for dynamic allocations at runtime
        – malloc() grabs memory on the heap
        – free() releases memory on the heap
    • Blocks of data are stored in a doubly linked list

    • Detection is simple:
        – Test if ( hdr->prev-> next == hdr) otherwise an attack is underway!
        – canaries

# Heap Overflow Exploitation
    • Direct attacks: modify function pointer
        – Simple overflow to the pointer location
    • Often indirect attacks on the stack return address
        – Fill headers with the address of the return address on the stack
        – The next malloc/free operation will modify the return address at will
    • Heap spraying:
        – Exploits contiguous chunk placement (e.g., browser, PDF, Flash)
        – Fill up an entire chunk with NOP sled + payload and spray it repeatedly into the heap
    • Can be very complex
        – Need to predict heap layout, control program state
        – Otherwise lead program in a state where it is exploitable

# Software exploitation: the bigger perspective
    • Software Fault Injection
        – Software built for one purpose, but attacker misuses the software for another purpose
        – Notably through specifically crafted inputs
        – Any Turing machine can be exploited
    • Hardware Fault Injection
        – Don’t forget that software runs within hardware
        – Perturbating the execution environment during code execution (laser, power supply glitch, clock glitch)
        – Cosmic/Gamma rays lead to random errors (bit flips)
        – Particular memory access patterns lead to bit errors in DRAM

# Race Conditions
    • Parallel execution of tasks
        – multi-process or multi-threaded environment
        – multi-user
        – tasks can interact with each other
    • Three properties are necessary for a race condition to exist:
        – Concurrency: There must be at least two control flows executing concurrently.
        – Shared Object: A shared race object must be accessed by both of the concurrent flows.
        – State Change: At least one of the control flows must alter the state of the object of a race
    • Results of tasks depend on the relative timing of events
        – Non-deterministic behavior

# Race Conditions: Basics
    • Programmer views a set of operations as atomic
        – In reality, atomicity is not enforced
        – Scheduler can interrupt a process at any time
        – Even more likely if there is a blocking system call
    • Attacker can take advantage of this discrepancy
    • Race condition vulnerabilities typically arise when:
        – checking for a given privilege, and
        – exercising that privilege
# Race conditions are eliminated by making conflicting operations mutually exclusive 

# TOC(T)TOU: Time-Of-Check- (To) -Time-Of-Use
    • Check – Establish some precondition (invariant), e.g., access permission
    • Use – Operate on the object assuming that the invariant is still valid
    • Can occur in any concurrent system:
        – shared memory (or address space)
        – file system
        – signals

# Races on temporary files
    • Similar issues as with regular files
        – commonly opened in /tmp or /var/tmp
        – creating files in /tmp requires no special permissions
        – often guessable file name
    • A possible attack:
        – guess the tmp file name: "/tmp/tmp0001"
        – ln -s /etc/target /tmp/tmp0001
        – victim program will create file /etc/target for you, when it tries to create the temporary file!
        – if first guess doesn't work, try 1 million times

# Window of Vulnerability
    • Window of vulnerability can be very short
        – race condition problems are difficult to find with testing
        – difficult to reproduce and debug
    • Myths about race conditions
        – "races are hard to exploit”
        – "races cannot be exploited reliably"
        – "only 1 chance in 10000 that the attack will work!"
    • Attackers can often find ways to beat the odds!
        – Repeated attempts
        – Attacker can try to slow down the victim machine/process to improve the odds (high load, computational complexity)
        – Attacker can run the attack many times in parallel to increase
        the probability that the attacking process will be scheduled by
        the processor at the right moment

# Slow file lookups
# Making It Slower: File System Maze

# Prevention and Detection
    • Prevention: many solutions depending on actual race
        – OS specific solutions: ID or filename related
        – Forking: delegate operations to separate process with EUID (effective UID)
        – Locking: suppress race, but slows down process
        – Hardness amplification: Reduce success probability of attacker (k-races, pseudo-atomic transactions)
    • Detection:
        – Static analysis with pattern matching
        – Static analysis with model checking (MOPS, RacerX,rccjava)
        – Dynamic Analysis (Eraser)
