`globalThis` is a global object in JavaScript that provides access to the global scope. It is available in both browser and Node.js environments, allowing you to define and access global variables and functions.

<hr />

**History of Nodejs**

Node.js was created by Ryan Dahl in 2009. It is built on the V8 JavaScript engine, which is also used by Google Chrome. Node.js allows developers to use JavaScript for server-side programming, enabling the creation of scalable and high-performance applications.

**io.js** was a fork of Node.js that emerged in 2014, focusing on faster releases and new features. In 2015, io.js merged back into the Node.js project, leading to the current version of Node.js.

In 2019, Node.js was officially adopted by the _OpenJS Foundation_, which is part of the Linux Foundation. This move aimed to ensure the long-term sustainability and growth of the Node.js project.

<hr />

**Basic Shell Commands**

- `echo` command used in the terminal is a command-line utility that outputs the strings it is being passed as arguments. It is commonly used to display messages or to write text to files.

- To print the variables in terminal, you can use the `echo` command followed by the variable name. For example, if you have a variable named `myVar`, you can print it in the terminal using:

```bash
echo $myVar
```

adding two variables in the terminal can be done using the `echo` command as well. For example, if you have two variables `var1` and `var2`, you can add them and print the result like this:

```bash
var1=5
var2=10
echo $((var1 + var2))
```

- `pwd` command is used to print the current working directory in the terminal. It displays the full path of the directory you are currently in.

- `whoami` command is used to display the username of the current user logged into the terminal. It shows the name of the user who is currently executing commands in the shell.

- `cd` command is used to change the current directory in the terminal. It allows you to navigate to different directories in the file system. For example, to change to a directory named `myFolder`, you would use:

```bash
cd myFolder
```

- `ls` command is used to list the files and directories in the current directory. It provides a view of the contents of the directory you are currently in. You can use it like this:

- `mkdir` command is used to create a new directory in the terminal. It allows you to create a folder with a specified name. For example, to create a directory named `newFolder`, you would use:

```bash
mkdir newFolder
```

- `rm` command is used to remove files or directories in the terminal. It allows you to delete files or folders. For example, to remove a file named `file.txt`, you would use:

```bash
rm file.txt
```

- `rmdir` command is used to remove empty directories in the terminal. It allows you to delete a directory only if it is empty. For example, to remove an empty directory named `emptyFolder`, you would use:

```bash
rmdir emptyFolder
```

- `cp` command is used to copy files or directories in the terminal. It allows you to create a duplicate of a file or folder. For example, to copy a file named `source.txt` to a new file named `destination.txt`, you would use:

```bash
cp source.txt destination.txt
```

- `mv` command is used to move or rename files and directories in the terminal. It allows you to change the location of a file or folder or rename it. For example, to move a file named `file.txt` to a directory named `myFolder`, you would use:

```bash
mv file.txt myFolder/
```

<br />
<br />

**PS1 and PS2 in bash**

`PS1` and `PS2` are environment variables in the shell that define the appearance of the command prompt. `PS1` is the primary prompt string, which is displayed when the shell is ready to accept a command. It can include various escape sequences to display information like the username, hostname, current directory, etc.

`PS2` is the secondary prompt string, which is displayed when a command spans multiple lines. It is typically used to indicate that the shell is waiting for more input.

<hr />
