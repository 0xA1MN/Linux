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



## Working with the Linux Shell

**# Shell** is a program that functions as a user interface, command-line interpreter, and programing (scripting) language. Let’s take a brief look at each of these entities.

Linux provides two types of user interfaces : CLI & GUI



**# Configuring the Shell**

The shell configuration files set up the user environment (/etc/profile and ~/.bash_profile) and regulate how the shell operates (/etc/bashrc and ~/.bashrc).

* **process** is single instance of a program that operates in its own memory space. The operating system assigns a unique process ID (PID) each time a program is started. This PID is used to control and track resources assigned to the program.

* **Parent and Child Processes** When you log on a system, you are presented with a default login shell.
  This shell is a program (by default, bash) that allows you to execute additional programs. 

  When you execute a command such as ls, a sub-shell or child process is created. This means that a copy of the current process (parent) is created and a new instruction set is loaded into the new process (child) Once the command has executed, the child is killed and control reverts to the parent.

* **Variables** A variable is a memory location that is assigned a name and is used to store data. Variables are used to configure operating environments or to temporarily store program data. When a user logs off or the system is turned off, data stored in these memory locations are lost.

  * **Local Variables** A local variable only exists in the memory space of the shell in which it is created. This means if you create a variable in a parent process and then create a child process, the variable created in the parent will not be present in the child.

    The syntax for creating a local variable is `[variable_name]=[value]`.

    To view the contents of a variable, execute the command `echo $[variable_name]`.

    The `set` command will display a list of all the variables and functions that exist in the current process.

  * **Environmental or Global Variables** In order to copy a shell variable from the parent process to the child process, you need to assign an export attribute to the variable. When a parent spawns a child process, all variables with this attribute are copied to the child

    An environmental (or global) variable is any variable assigned an export attribute. To create a variable and assign an export attribute, execute the command `export [variable_name]=[value]`

    The command `env` will display a list of all environmental variables in the current shell. To determine if a specific variable has an export attribute, 

    execute the command `env | grep [variable_name]`.

* **Aliases**  is a command shortcut  

  set alias `alias [alias_name]='[command]'`

  unset alias `unalias [alias_name]='[command]'`

  *note : on logout aliases which define by above way are deleted to make alias permanent you must add it to `~/.bachrc`*

  

**# Bash Configuration Files**

`/etc/profile` & `/etc/bashrc `  system (global) configuration files that are applied to all applicable users.

`~/.bash_profile` & `~/.bashrc` & `~/.bash.logout` Files located in the user’s home directory (~/<user_name>) contain user-specific configuration information. Settings in these files override the `/etc` configuration file settings.

* **`/etc/profile`**

  The file `/etc/profile` is a generic file only read when a user logs on to the system or executes a command that forces a logon (such as su -).
  When a login shell is run, the bash shell program searches for configuration files in the following order:
  `~/.bash_profile || ~/.bash_login || ~/.profile`

  Once one of those configuration files is found the remaining files are ignored. This file is used to set up the environment for any user whose default shell is either the bourne, korn, or bash shell. The file /etc/profile is read when a user logs on.

  *In /etc/profile you will find the following:*
  **HOSTNAME** variable is set to the system’s
  **HISTCONTROL** History environmental variable that determines if bash will store command lines that begin with spaces or are duplicates.
  **HISTSIZE** History environmental variable that shows the number of commands stored by the history facility in memory.
  **umask** The value of umask determines what permissions will be denied when a file is created.

* **`/etc/bashrc`**

  contains commands that affect how the bash shell runs for all users whose default shell is bash. This file is read when called by a command found in ~/.bashrc. This configuration file contains system-
  wide configuration elements such as Aliases, Functions, Shell configuration options and PS1 prompt configuration

  *The letters rc stand for “run command.” rc (run command) files contain startup configuration information that determines how an application will operate.* 

* **`~/.bash_profile`**
  read after the file /etc/profile only when the user logs on to the system and if a user’s default shell is bash. The file .bash_profile is used to *customize the bash environment* for a user. The file
  contains variables used to configure the user’s working environment (such as time zone, locale, and editor).

* **`~/.bashrc`**
  The file ~/.bashrc is found in the user’s home directory and is used to customize how the bash shell runs. The ~/.bashrc file contains aliases, functions or shell parameters. ~/.bashrc is executed each time a process is started. This file would contain user specific: Aliases, Functions, Shell configuration options and PS1 prompt configuration

* **`/etc/profile.d`**
  The files in the directory /etc/profile.d contain configuration information for specific programs and are read automatically during the login process. The file /etc/profile (for bourne, korn, and bash users) contains a statement that reads all the files in /etc/profile.d with a suffix of .sh (for example, vim.sh). The file csh.login (for C shell users) contains a statement that reads all the files in /etc/profile.d with the suffix .csh (for example, vim.csh).

**The source Command** Configuration changes are not active until they are stored in memory. To
place changes in memory, you must execute the commands in the configuration file. 

The command `source [filename]` or  `[filename]` will execute the commands in a configuration file.
The file ~/.bash_profile is only read when the user logs on. Changes to a user’s .bash_profile would not be read until the user’s next logon. The source command source ~/.bash_profile or . ~/.bash_profile would make those configuration changes available immediately.