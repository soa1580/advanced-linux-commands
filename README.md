# advanced-linux-commands
File permissions and Access Rights

Understanding file permissions and ownership in Linux is important because it lets you control who can access or change files and folders, helping keep your system secure. 

Now let’s look at some key commands and concepts you need to know

In Linux, permissions are shown with numbers. Each type of permission—no permission, read, write, and execute—has a numeric value: 
no permission = 0, 
read = 4, 
write = 2, 
execute = 1.

These values are combined to represent the permissions for each user class. Let's consider a few examples.

Permissions Represented by 7

4 (read) + 2 (write) + 1 (execute) = 7
Symbolic: rwx
Meaning: Read, write, and execute permissions are all granted.
Example Context: A script file that the owner needs to read, modify, and execute.

Permissions Represented by 5

4 (read) + 1 (execute) = 5
Symbolic: r-x
Meaning: Read and execute permissions are granted, but write permission is not.
Example Context: A shared library or a command tool that users can execute and read but not modify.

Permissions Represented by 6

4 (read) + 2 (write) = 6
Symbolic: rw-
Meaning: Read and write permissions are granted, but execute permission is not.
Example Context: A text file that the owner can read and edit, but not run as a program.

## Shorthand Representation of Permissions
