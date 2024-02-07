# Unit-1
**Operating System**: An operating system is a program that acts as an interface between the user and the computer hardware and controls the execution of all kinds of programs.
## Services
An Operating System provides services to both the users and to the programs. It provides programs, an environment to execute. It provides users, services to execute the programs in a convenient manner.\
**Types**:
- User interface
	1. Graphical User Interface(GUI)
	2. Command Line Interface(CLI)
- Program execution
- I/O operations
- File System manipulation
- Communication
- Error Detection
- Resource Allocation
- Protection
## Objectives
1. Convenience
2. Efficiency
3. Ability to evolve
## Structure
1. Simple
2. Layered
#### Simple Structure
Application program\
	|							| \
System Program\
	|							| \
Device Drivers\
	|							|\
BIOS Device Drivers
## Operations
Modern operating systems are Interrupt driven. If there are no processes to execute, no I/O devices to service, and no users to whom to respond, an operating system will sit quietly, waiting for something to happen. Events are almost always signaled by the occurrence of an interrupt or trap.
#### Dual-mode Operation
To ensure proper operation, we must protect the operating system and all other programs and their data from any malfunctioning program. Protection is needed for any shared resource. The approach taken is to provide hardware support to allow us to differentiate among various modes of executions.
1. User Mode
2. Kernel Mode

## System Calls
System calls provide an interface to the services made available by an operating system.\
Types
1. Process Control
2. File Manipulation
3. Device Manipulation
4. Information Maintenance
5. Communication
#### Process Control
A running program needs to be able to halt its execution either normally (end) or abnormally (abort). If a system call is made to terminate the currently running program abnormally, or if the program runs into a problem and causes an error trap, a dump of memory is sometimes taken and an error message generated and it can be examined with a debugger\
**System calls**:
- end, abort
- load, execute
- create process, terminate process
- get process attributes, set process attributes
- wait for time
- wait event, signal event
- allocate and free memory
#### File Management
- create file, delete file  
- open, close file  
- read, write, reposition  
- get and set file attributes
#### Device management
- request device, release device  
- read, write, reposition  
- get device attributes, set device attributes
### Information Maintenance
- get time or date, set time or date  
- get system data, set system data  
- get and set process, file, or device attributes
#### Communication
There are two common models of interprocess communications:
1. Message passing model
2. shared –memory model.

System calls:
- create, delete communication connection 
- send, receive messages
- transfer status information  
- attach and detach remote devices
# Unit-2
**Process**: A program in execution is called as process
## Process States
- New
- Ready
- Run
- Block / wait
- Completion / Termination
## Process Control Block(PCB)
- Process ID
- Process state
- Process priority
- Pointer
- Program counter
- CPU Registers
- I/O information
- Accounting information
## Scheduling
- FCFS
- SJF
- SRTF
- RR
## Critical Section Problem
Critical Section is the part of a program which tries to access shared resources. That resource may be any resource in a computer like a memory location, Data structure, CPU or any IO device.
- Bound buffer
- Dining philosopher
- Read writer problem
# Unit-3 
## Paging
Main memory is divided into a number of equal-size blocks, are called frames. Each process is divided into a number of equal-size block of the same length as frames, are called Pages. A process is loaded by loading all of its pages into available frames
## Segmentation
Segmentation is a memory-management scheme that supports user view of memory.
## Virtual Memory
Virtual memory is a technique that allows the execution of processes that may not be completely in memory. Only part of the program needs to be in memory for execution. It means that Logical address space can be much larger than physical address space. Virtual memory allows processes to easily share files and address spaces, and it provides an efficient mechanism for process creation.
# Unit-4
**FILE**: A file is a named collection of related information that is recorded on secondary storage
## File Attributes
1. Name
2. Identifier
3. Type
4. Size
5. Protection
6. Location
7. Time, Date and User Identification
## File Operations
A file is an abstract data type .To define a file properly, we need to consider the operations that can be performed on files. The operating system can provide system calls to create, write, read, reposition, delete, and truncate files.
1. Creating a file
2. Writing a file
3. Reading a file
4. Repositioning within a file
5. Deleting a file
6. Truncating a file
## File Types
File type refers to the ability of the operating system to distinguish different types of file such as text files, source files and binary files etc. Many operating systems support many types of files. Operating system like MS-DOS and UNIX have the following types of files
## File Structure
File System provide efficient access to the disk by allowing data to be stored, located and retrieved in a convenient way. A file System must be able to store the file, locate the file and retrieve the file.
Application program\
			|\
Logical File System\
			|\
File Organisation Module\
			|\
Basic File System\
			|\
I/O Control\
			|\
Devices
## File Access Methods
Files store information. When it is used, this information must be accessed and read into computer memory. The information in the file can be accessed in several ways. Some systems provide only one access method for files. While others support many access methods, and choosing the right one for a particular application is a major design problem.
1. Sequential Access
2. Direct Access 
3. Other Access
## Directories
The directory can be viewed as a symbol table that translates file names into their directory entries.
1. Single-level Directory
2. Two-level Directory
3. Tree-Structured Directory
4. Acyclic-Graph Directory
## File System Mounting
The basic idea behind mounting file systems is to combine multiple file systems into one large tree structure. The mount procedure is straightforward. The operating system is given the name of the device and the mount point—the location within the file structure where the file system is to be attached.
## File Sharing
1. Multiple Users
2. Remote File Systems
3. Client-Server Mode
4. Distributed Information System
## Mass Storage System
Systems designed to store enormous volumes of data are referred to as mass storage devices. Massive storage devices are sometimes used interchangeably with peripheral storage, which is the management of bigger volumes of data that are larger than the native storage capability of a computer or device.\
The basic idea of Mass Storage is to create a Data Backup or Data Recovery System.
1. Magnetic Disks
2. Solid State Drives
3. Magnetic Tapes

# Unit-5
## Dead Locks
A Deadlock is a situation where each of the computer process waits for a resource which is being assigned to some another process.
### Conditions
1. Mutual Exclusion
2. Hold and wait
3. No preemption
4. Circular wait
## Handling Deadlock
1. Deadlock Ignorance
2. Deadlock Prevention
3. Deadlock Avoidance
4. Deadlock Detection and Recovery
## Access Matrix
The Access Matrix is a security model for a computer system's protection state. It is described as a matrix. An access matrix is used to specify the permissions of each process running in the domain for each object. The rows of the matrix represent domains, whereas the columns represent objects. Every matrix cell reflects a set of access rights granted to domain processes, i.e., each entry **(i, j)** describes the set of operations that a domain **Di** process may invoke on object **Oj.**