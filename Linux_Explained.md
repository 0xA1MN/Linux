##  Linux Operating System Structure

* **Hardware layer** Responsible for interacting with system hardware.
* **Kernel** The kernel layer is the core of the operating system. It
  provides the system with process, memory, and task management.
  The kernel also connects applications to system hardware. The
  kernel is divided into the following components:
  * **System Call Interface** The System Call Interface (SCI)
    provides a connection between user space and kernel space.
  * **Process management** Responsible for creating, stopping, and
    communicating with system processes.
  * **Memory management** Responsible for memory allocation,
    virtual memory, and paging.
  * **Virtual File System** Provides an abstraction layer for multiple
    filesystem types.
  * **Network stack** Provides protocols used in network
    communications.
  * **Device drivers** Software used to communicate with hardware.
  * **Architecture-dependent code** System code specific to the type
    of processor.

* **Shell** Application and user environment and interface.

* **Operating system software** Used to manage the operating system.

* **Application software** Editors and other user applications.

  

**Kernel**

The kernel layer is the core of the operating system. Most Linux
distributions use a monolithic kernel. Some (GNU) use a microkernel.
To understand the difference between a *monolithic and microkernel*, you
must understand the terms *user space and kernel space*. Kernel processes
execute in memory reserved for kernel processes (kernel space). User
processes execute in memory reserved for user applications (user space).
Separating user and kernel space protects kernel processes.

* **Monolithic Kernel**
  A monolithic kernel executes in kernel space. Monolithic kernels are made
  up of modules that perform specific functions. These modules may be
  dynamically loaded or unloaded.
* **Microkernel**
  A microkernel uses a small kernel executing in kernel space to manage
  memory, multitasking, and interprocess communication. Most other kernel
  functions are built in to “servers” that execute in user space.



## Using the vi Text Editor

`vi <filename> Or vim <filename>`

**vi uses five different operating modes ** 

- Command mode

  Pressing the ESC key once places you in command mode. The command
  mode allows you to issue local editing commands. Local commands would
  be used to add or modify a character, word, single line, or multiple lines.

- Command-line mode

  Pressing ESC : places you in command-line mode. Commands issued in
  command-line mode are global commands; they affect the entire document.
  Examples of global commands are write, search, and search and replace.

- Insert

  Insert mode inserts text to the left of the cursor. ESC i (lowercase i) inserts
  text immediately to the left of the cursor, and ESC I (uppercase I) inserts text
  at the left margin.

- Append

  Append mode adds text to the right of the cursor. ESC a (lowercase a)
  appends text immediately after the cursor, and ESC A (uppercase A) appends
  text at the end of the current line.

- Open

  The open mode is used to open a line above or below the current cursor
  position and places the editor in insert mode and the cursor at the left
  margin. ESC o (lowercase o) opens a line below the current cursor position,
  and ESC O (uppercase O) opens a line above the current cursor position.



**Shortcuts**

| Command          | Action                                                       |
| :--------------: | ------------------------------------------------------------ |
| ESC-dw           | Deletes the word that comes immediately after the cursor, including the space following the word. |
| ESC-d$           | Deletes from the insertion point to the end of the line.     |
| ESC-dd           | Deletes the entire current line.                             |
| ESC-p            | Inserts deleted text before or below the current cursor location. |
| ESC-P            | Inserts deleted text after or above the current cursor location. |
| ESC-u            | Undoes the last action. |
| ESC-U            | Undoes all changes made on the current line. |
| ESC-D            | Deletes the rest of the current line from the cursor position. |
| ESC-yy           | Copies the line in which the cursor is located to the buffer. |
| ESC-a            | Appends after cursor. |
| ESC-A            | Appends after line. |
| ESC-C            | Changes to the end of the line. |
| ESC-cc           | Changes the whole line. |
| ESC-ZZ           | Saves the current file and ends vi. |
| ESC-h            | Moves the cursor left one character. |
| ESC-j            | Moves the cursor down one line. |
| ESC-k            | Moves the cursor up one line. |
| ESC-l            | Moves the cursor right one character. |
| ESC-0            | Moves the cursor to the start of the current line. |
| ESC-:w           | Writes the current file to disk. |
| ESC-:exit        | Writes the current file to disk and then closes vi. |
| ESC-:wq          | Also writes the current file to disk and closes vi. |
| ESC -:q          | Closes vi without saving the current file. |
| ESC-:q!          | Closes vi without saving the current file, even if the file has been modified. |
| ESC-:w!          | Overwrites the current file. |
| ESC-:e!          | Forgets changes since the last write. |
| CTRL-G           | displays a status line at the bottom of the interface. |
| /search [string] | searches from the current cursor position to the bottom of the document for the specified string. |
| ?search [string] | searches from the current cursor position to the top of the document for the specified string. |  

From within command mode, you can enter a colon (:) to switch to command-line mode.