[Reference](https://ryanstutorials.net/linuxtutorial/)
[Sheatsheet](https://ryanstutorials.net/linuxtutorial/cheatsheet.php)

# what is CLI?
The Command-Line-Interface allows us to accomplish and automate tasks on a computer without the use of a graphical user interface (GUI).

> The command line is an interesting beast 😈

<br>

# Why is terminal so powerful?
It gives the user a means of issuing commands directly to the computer without the drain on the computer's resources that a GUI brings. It is also a way of issuing powerful commands in order to do things which can not be done via a GUI.

Some tasks are best suited to a GUI, word processing and video editing are great examples. At the same time, some tasks are more suited to the command line, data manipulation (reporting) and file management are some good examples. Some tasks will be just as easy in either environment. 

<br>

# What is the Shell, Bash?
Within a terminal you have what is known as a shell. This is a part of the operating system that defines how the terminal will behave and looks after running (or executing) commands for you. There are various shells available but the most common one is called bash which stands for Bourne again shell.

> Use ```echo $SHELL``` command to display which shell you are using.

<br>
<br>

# Commands

### notes:
When you enter commands, they are actually stored in a history. You can traverse this history using the up and down arrow keys.

If you stuck in a command use < ```man 'command'``` > command.

<br>

```pwd:``` stands for Print Working Directory (It tells you what your current or present working directory is).

```ls [options] [location]:``` "ls -l /etc"

    The result will be like this for each file
        - First character indicates whether it is a normal file ( - ) or directory ( d )
        - Next 9 characters are permissions for the file or directory.
        - The next field is the number of blocks.
        - The next field is the owner of the file or directory.
        - The next field is the group the file or directory belongs to.
        - Following this is the file size.
        - Next up is the file modification time.
        - Finally we have the actual name of the file or directory.

```cd [path || location]:``` "change directory"
> If you run the command cd without any arguments then it will always take you back to your home directory.

> Typing out these paths can become tedious you may hit the Tab key on your keyboard at any time which will invoke an auto complete action. If nothing happens then that means there are several possibilities. If you hit Tab again it will show you those possibilities. You may then continue typing and hit Tab again and it will again try to auto complete for you.

<br>

## Paths

>### **Absolute paths** specify a location (file or directory) in relation to the root directory. You can identify them easily as they always begin with a forward slash ( / ).

>### **Relative paths** specify a location (file or directory) in relation to where we currently are in the system. They will not begin with a slash.

### **Root** directory. It is denoted by a single slash ( / ). It has subdirectories, they have subdirectories and so on. Files may reside in any of these directories.

- ```~``` (tilde) - This is a shortcut for your home directory. eg, if your home directory is */home/ryan* then you could refer to the directory Documents with the path */home/ryan/Documents* or *~/Documents*
- ```.``` (dot) - This is a reference to your current directory.
- ```..``` (dotdot)- This is a reference to the parent directory. You can use this several times in a path to keep going up the hierarchy. eg if you were in the path */home/ryan* you could run the command *ls ../../* and this would do a listing of the root directory.

<br>

## Files
#### Everything is a File
Everything is actually a file. A text file is a file, a directory is a file, your keyboard is a file (one that the system reads from only), your monitor is a file (one that the system writes to only) etc.

<br>

#### Linux is Case Sensitive
It is possible to have two or more files and directories with the same name but letters of different case.

<br>

#### Spaces in names
Spaces in file and directory names are perfectly valid but we need to be a little careful with them.
As you would remember, a space on the command line is how we seperate items. 🤨
 If you have file name like this "Hello world", then u can access it using:
    - Quotes 'Hello world'
    - Escape Characters Hello\ world

<br>

#### Hidden Files and Directories
If the file or directory's name begins with a ```.``` (full stop) then it is considered to be hidden.
 To make a file hidden name it (or rename it) with a ```.``` at the begining.
 To list the hidden files use ```ls -a```

<br>

```mkdir [options] [Directory]:``` Making a Directory.

```rmdir [options] [Directory]:``` Removing a Directory.

```rm [options] [file]:``` Removing a File (and non empty Directories).

```rm -r [file]:``` Removing non empty Directories.

```touch [options] [filename]:``` Creating a Block File.

```cp [options] [source] [destination]:``` Copying a File or Directory.

```mv [options] [source] [destination]:``` Moving a File or Directory.

>Normally ``` mv ``` will be used to move a file or directory into a new directory. it will also can rename it. Now if we specify the destination to be the same directory as the source, but with a different name, then we have effectively used mv to rename a file or directory. 

