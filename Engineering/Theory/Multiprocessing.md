# Multiprocessing
- **Process**: An instance of the Python interpreter has at least one thread called the *MainThread*
	- Each process is in fact one instance of the Python interpreter that executes Python instructions (Python byte-code), which is a slightly lower level than the code you type into your Python program
- **Thread**: A thread of execution within a Python process, such as the *MainThread* or a new thread
- A process in Python can represented as an instance of the **`multiprocessing.Process`** class
	- Once a process is started, the Python runtime will interface with the underlying operating system and request that a new native process be created
	- The **`multiprocessing.Process`** instance then provides a Python-based reference to this underlying native process
## Life-Cycle of a Process
- A new process is a process that has been constructed and configured by creating an instance of the **`multiprocessing.Process`** class
	- A new process can transition to a running process by calling the **`start`** method
		- This also creates and starts the main thread for the process that actually executes code in the process
- A running process may **block** in many ways if its main thread is blocked, such as reading or writing from a file or a socket or by waiting on a concurrency primitive such as a semaphore or a lock
	- After blocking, the process will run again
- Finally, a process may terminate once it has finished executing its code or by raising an error or exception
- A process cannot terminate until:
	- All non-daemon threads have terminated, including the main thread
	- All non-daemon child processes have terminated, including the main process
## Process Types
### Parent Process
- A parent process is a process that is capable of starting child processes
	- Typically, we would not refer to a process as a parent process until it has created one or more child processes
- A parent process may also be a child process
- In Python, the first process created when we run our program is called the **MainProcess**
	- It is also a parent process and may be called the main parent process
### Child Process
- A child process is a process that was created by another process (rather than by the operating system directly)
	- May also be called a subprocess
	- The creation and management of **all** processes is handled by the underlying operating system
- It may also be an adult process (have its own child processes)
- There are three main techniques used to create a child process, referred to as process start methods
	- Fork
	- Spawn
	- Fork server
- Depending on the start technique used, the child process may or may not inherit properties of the parent process
	- For example, a forked process may inherit a copy of the global variables from the parent process
- A child process may become orphaned if the parent process that created it is terminated