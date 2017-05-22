# EDAF15
## Memory
The memory is used to store data and instructions. Computer memory is the storage space in the computer, where data is to be processed and instructions required for processing are stored. The memory is divided into large number of small parts called cells. Each location or cell has a unique address. 
Inline-style: 
![](https://github.com/Dsek-LTH/Courses/blob/master/EDAF15/mem.jpg)
Above is the "memory triangle", it shows the relation between diffrent kinds of memory in the computer. 
### Volatile & nonvolatile memory.
Volatile memory is memory which resets (loses all allocated memory) when the power is turned off. Cache and RAM are examples of volatile memory. 
### Registers
In computer architecture, a processor register is a quickly accessible location available to a computer's central processing unit (CPU). Registers usually consist of a small amount of fast storage, although some registers have specific hardware functions, and may be read-only or write-only. Registers are typically addressed by mechanisms other than main memory, but may in some cases be assigned a memory address.

### Cache
Cache memory is a very high speed semiconductor memory which can speed up the CPU. It acts as a buffer between the CPU and the main memory. It is used to hold those parts of data and program which are most frequently used by the CPU. The parts of data and programs are transferred from the disk to cache memory by the operating system, from where the CPU can access them.

#### Mapping
Just as bookshelves come in different shapes and sizes, caches can also take on a variety of forms 
and capacities. But no matter how large or small they are, caches fall into one of three categories: 
direct mapped, n-way set associative, and fully associative.
##### Direct
A cache block can only go in one index in the cache. It makes a cache block very easy to find, but it‛s not very flexible about where to put the blocks. This memory layout has some drawbacks, it will write over the information in a cache block if the sougth after address isn't in the cache (if cache miss) and this might result in more cache misses. 

##### Assosiative 
No index is needed, since a cache block can go anywhere in the cache. Every tag must be compared when finding a block in the cache, but block placement is very flexible. becuase every tag needs to be campared to find the cache block we will need as much comparators as number of tags. Which will result in much transistorspace being #waisted". Also note that it is more likely to get a hit in a fully asslsiative chahe. 
##### N-way Set-Assosiative. 
The cache is made up of sets that can fit N-blocks each. The index is now used to find the set, and the tag helps find the block within the set.
##### Way of thinkning about the different cache mappings. 
The direct mapped cache is just a 1-way set associative cache, and a fully associative cache of m blocks is an m-way set associative cache!
##### Cache miss
A cache miss is when we try to find a memory block in the cache but we don't find it. This will result in the need of fetching that memory block from the hard drive which will take A LOT of time in compareson and the possibility of cache blocks being overwritten depending on the cache mapping. 

### RAM
Random-access memory (RAM) is a form of computer data storage which stores frequently used program instructions to increase the general speed of a system. A random-access memory device allows data items to be read or written in almost the same amount of time irrespective of the physical location of data inside the memory.
### Primary memory
Secondary storage (also known as external memory or auxiliary storage), differs from primary storage in that it is not directly accessible by the CPU. The computer usually uses its input/output channels to access secondary storage and transfers the desired data using intermediate area in primary storage. Secondary storage does not lose the data when the device is powered down—it is non-volatile. Per unit, it is typically also two orders of magnitude less expensive than primary storage. Modern computer systems typically have two orders of magnitude more secondary storage than primary storage and data are kept for a longer time there.

## Pipelineing & RISC-processor
RISC - Reduce Instructions Set computing.
Pipelineing is a technique that implements a form of parallelism called instruction-level parallelism within a single processor. It therefore allows faster CPU throughput (the number of instructions that can be executed in a unit of time) than would otherwise be possible at a given clock rate. The basic instruction cycle is broken up into a series called a pipeline. Rather than processing each instruction sequentially (finishing one instruction before starting the next), each instruction is split up into a sequence of dependent steps so different steps can be executed in parallel and instructions can be processed concurrently (starting one instruction before finishing the previous one).
The seps vary by the computer architecture but the RISC looks like this:
* Instruction fetch
* Instruction decode and register fetch
* Execute
* Memory access
* Register write back

The ideal speedup from a pipeline is equal to the number of stages in the pipeline but due to misspredictions and stalls the speedup is less than the number of stages in the pipeline. 
### Branch prediction
Pipelined processors use speculative computing to be more efficient. This means that they will need to guess the outcome of a branch. This can be done with the help of a Branch History Table, where the results of the last branches are stored. Without this optimization, instructions following the branch cannot be loaded until the outcome has been determined.
In the case of the branch prediction being wrong the pipeline stalls and it has to restart from the point of the miss prediction.

## C-programming
C-programming differs a little from java in a sense. The main difference is that in C we need to allocate and deallocate all memory by our self. In java this is done by the java viritual machine. This makes the code more agile but less effective. 

### Memory allocation
Memmory in C may be allocated in several ways:
* malloc - allocates memory on the process heap. Memory allocated using malloc will remain on the heap until it is freed using free.
* calloc - allocates the specified number of bytes and initializes them to zero in the heap. This function is very slow and i would use it with caution. 
* realloc - reallocates memory from a given position and size to a new position (If needed) and changes the size of the allocated space. 
* alloca - allocates memory within the current function's stack frame. Memory allocated using alloca will be removed from the stack when the current function returns. alloca is limited to small allocations. There is no need to free said memory becuase it only exist in the curret stack frame.  
* free - frees allocated space. 

#### Stack
The stack is the memory set aside as scratch space for a thread of execution. When a function is called, a block is reserved on the top of the stack for local variables and some bookkeeping data. When that function returns, the block becomes unused and can be used the next time a function is called. The stack is always reserved in a LIFO (last in first out) order; the most recently reserved block is always the next block to be freed. This makes it really simple to keep track of the stack; freeing a block from the stack is nothing more than adjusting one pointer. The stack is placed in the computers RAM memory.

#### Heap
The heap is memory set aside for dynamic allocation. Unlike the stack, there's no enforced pattern to the allocation and deallocation of blocks from the heap; you can allocate a block at any time and free it at any time. This makes it much more complex to keep track of which parts of the heap are allocated or free at any given time. The heap is stored in the computers RAM memory.

### Temporal and Spatial locality
For best performance we need to take advantage of how objects are placed in the memory and when they are being accessed in the execution sequence. 
#### Temporal locality
Temporal locality is focused on time, instructions close in time has a temporal locality. 

#### Spatial locality
Objects are close to each other in memory.

### Pointers
The idea of a pointer is very simple to explain and to get a sens of what it does. It points to a memory space in the computer. I can't stress this enough, it points to a memory space NOT a object like an int or struct. This makes pointers very agile. The pointer is always pointing to a memory space and if you want to use information stored at the memoryspace you need to use the * operator. 

#### * and & operators
The * operator is called the Value at operator. It returns the value stored at the pointers address. 
The & operator is called the Address operator. It returns the address of a stored value. 

##### Example of * and & operators
```c
int i = 5;
int *p = &i;
printf("%p", &i); //Prints the address of variable i
*p = 10;
printf("%d", *p); // Prints the value stored at the address p
```
Note: in the code above we have changed the value of the variable i aswell. 

#### Pointer aritmetics
A very nice feature of pointer movement in C is that the compliler knows how much to move the pointer to the next element.
```c
int *ptr;
int arr[30] = {1,2,3,....,29};
ptr = arr;
for(int i = 0; i<30; i++){
	printf("%d \n",*ptr);
	ptr++;
}
```
This will move the pointer 2 bytes to the left and not the one byte to the left which one may think. This works thanks to pointer aritmetics and the C-compiler.  

### Bitwise Operators 
#### & operator
Binary AND Operator copies a bit to the result if it exists in both operands. 

| a |b | output |
| ------------- |:-------------:| -----:|
| 0| 0| 0 |
| 0| 1 |   0 |
| 1| 1 |    1 |

#### ^ operator
Binary XOR Operator copies the bit if it is set in one operand but not both. 

| a |b | output |
| ------------- |:-------------:| -----:|
| 0| 0| 0|
| 0| 1 |   1 |
| 1| 1 |    0 |

#### | operator
Binary OR Operator copies a bit if it exists in either operand.

| a |b | output |
| ------------- |:-------------:| -----:|
| 0| 0|  0|
| 0| 1 |   1 |
| 1| 1 |    1 |

#### ~ operand
Binary Ones Complement Operator is unary and has the effect of 'flipping' bits.

|  | output |
| ------------- |-----:|
| a | 101100|
| ~a| 010011|

#### <<-operand
Binary Left Shift Operator. The left operands value is moved left by the number of bits specified by the right operand.

|  | output |
| ------------- |-----:|
| a | 101100|
| a<<1| 011000|

#### >> operand
Binary Right Shift Operator. The left operands value is moved right by the number of bits specified by the right operand.

|  | output |
| ------------- |-----:|
| a | 101100|
| a>>1| 010110|

#### Compiler optimization
The C compiler can change the way the program execute to increase the speed of the program, one way of it doing this is loop optimization.
Loop optimization is the process of increasing execution speed and reducing the overheads associated with loops. It plays an important role in improving cache performance and making effective use of parallel processing capabilities. Most execution time of a scientific program is spent on loops.

The compiler can optimize a lot but it is not allowed to change the order of elements in a struct. To minimize the struct size, you need to arrange the fields such that the alignment padding is minimized.

### Tools

#### Valgrind (Memcheck)
Is a generic framework for creating dynamic analysis tools such as checkers and profilers.
Memcheck is the default tool for valgrind. The problems Memcheck can detect and warn about include the following:
* Use of uninitialized memory
* Reading/writing memory after it has been free'd
* Reading/writing off the end of malloc'd blocks
* Memory leaks
The price of this is lost performance. Programs running under Memcheck usually run from twenty to thirty times slower than running outside Valgrind and use more memory.

#### Cachegrind
Is a a cache profiler, it will show the cache miss rate among other useful data. Cachegrind is a part of valgrind. 

#### Massif
Measures the amount of heap memory different parts of a program allocates. Is used valgrind to generate data just like cachegrind. 

#### OProfile 
Is a system-wide statistical profiling tool for Linux. Oprofile can count the number of times certain events happen such as: clock cycles, executed instructions cache misses. Can be presented at source code level or instruction level. Advantages over gcov/gprof are that it does not need special flags and should be used with the highest level of optimization. A disadvantage is that to change what it should count, the user must have root privileges on the machine.

#### gcov
Counts exact execution counts for each source line as well as branch frequencies (taken/non-taken). Needs special flags for the compilation and affects compiler optimization.

#### gprof
Execution times are shown for the different functions and the number of times each function is called and by which function. Needs special flags for the compilation and affects compiler optimization.
