# advanced-linux-commands

## File permissions and Access Rights

Understanding file permissions and ownership in Linux is important because it lets you control who can access or change files and folders, helping keep your system secure. 

Now let’s look at some key commands and concepts you need to know

## Numeric Representation of Permissions

In Linux, permissions are shown with numbers. Each type of permission—**no permission, read, write, and execute**—has a numeric value: 
- **no permission = 0**, 
- **read = 4**, 
- **write = 2**, 
- **execute = 1**.

These values are combined to represent the permissions for each user class. Let's consider a few examples.

**Permissions Represented by 7**

4 (read) + 2 (write) + 1 (execute) = 7
Symbolic: rwx
Meaning: Read, write, and execute permissions are all granted.
Example Context: A script file that the owner needs to read, modify, and execute.

**Permissions Represented by 5**

4 (read) + 1 (execute) = 5
Symbolic: r-x
Meaning: Read and execute permissions are granted, but write permission is not.
Example Context: A shared library or a command tool that users can execute and read but not modify.

**Permissions Represented by 6**

4 (read) + 2 (write) = 6
Symbolic: rw-
Meaning: Read and write permissions are granted, but execute permission is not.
Example Context: A text file that the owner can read and edit, but not run as a program.

## Shorthand Representation of Permissions

In addition to the numeric method of displaying permissions, Linux also employs a shorthand or symbolic approach to represent file permissions.

## Understanding User Classes from a Permissions Perspective.

Before exploring shorthand permissions, it’s essential to grasp the concept of "user classes" in the context of Linux permissions. These user classes are categories that Linux recognizes when determining who can perform specific actions on a file. There are three primary classes:
- **Owner**: The individual who created the file, often referred to as the "user."
- **Group**: A collection of users who share certain permissions for the file.
- **Others**: Anyone else with access to the computer who doesn’t fall into the first two categories.

## The Role of Hyphens (-) in Permission Representation

When discussing permissions, you might notice hyphens (-) being mentioned. In the context of Linux file permissions, a hyphen doesn’t represent a user class. Instead, it is used in the symbolic representation of permissions to indicate the absence of a permission.

Let’s explore some practical examples. Open your Linux terminal and execute the command **ls -ltr**

