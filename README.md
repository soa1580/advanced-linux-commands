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

![ls -latr](./img/1.ls-latr.png)

Let’s break it down to understand each part:

- In the output shown above, the first character can either be a “-” or a “d”, “d” indicates a directory while “-” indicates a regular file.

- The next three characters (rwx) display the owner’s permissions — r for read, w for write, and x for execute.

- If a permission isn’t given, a “-” appears in its place, (e.g., r-x means the read and execute permissions are allowed, but write is not.)

- The hyphen (-) separates the permissions for owner, group, and others.

- The next three characters after the owner’s permissions show the group’s permissions, following the same r, w, and x pattern.

- The last three characters show the permissions for others.

The order the user class is represented is as follows;

- The first hyphen **"-"** is the **user**

- The second hyphen **"-"** is the **group**

- The third hyphen **"-"** is **others**


## File Permission Commands

To manage file ownership and permissions in Linux, several commands are available.

## chmod Command
The chmod command is used to change file permissions. It allows you to use either symbolic or numeric values to assign permissions for the user, group, and others.

Let’s look at an example:
You can create an empty file using the 'touch' command

![script-sh](./img/2.touch.png)

Check the permission of the file

![perm-file](./img/3.ls-latr.script.png)

**What do you think the permission of the above output represent?**

Now lets update the permission so that all the user classes will have execute permission

![chmod-+x](./img/4.chmod-+X.png)

The above command uses the chmod command with the +x option to grant execute to the file script.sh, which adds the execute permission to the existing permissions for all the user classes.

So lets check what the file permission look like

![ls-latr_sh](./img/5.ls-2.png)

The same command can be executed to achieve the same result using the numbers approach.

![C.number-app](./img/6.chmod-755.png)


To give execute permission to all (user, group, and others), you need to add 1 to each of the three permission categories. This results in a numeric value of 755:

- (4 + 2 + 1) = 7 for the user (read, write, and execute)

- (4 + 1) = 5 for the group (read and execute)

- (4 + 1) = 5 for others (read and execute)


Now, let’s look at another example. Suppose the owner of a file currently has full permission to **note.txt**.

If you want to allow both the group and others to read, write, and execute the file, change its permission type to -rwxrwxrwx, which has a numeric value of 777.

![chmod-777](./img/7.note-txt.png)

Check the output

![ls-latr_note](./img/8.ls-note.png)

Notice the dash ('-') in the first position represent the file type and not a user class. It indicates that the entry is a regular file.

## Chown Command

It's allows you to change the ownership of files, directories, or symbolic links to a specified username or group.

The basic format is as follow; **chown [option] owner[:group] file(s)**

For instance, lets assume there is a user on the sever called "**john**", a group on the server called "**developers**" and you want the owner of '**filename.txt**' changed from "**ubuntu**" to "**john**" and to also ensure that any user in the developers group has the ownership of the file as well:

The command would look like below;

![chown](./img/9.chown.png)

As you can see from the above output that read 'Operation not permitted', so what I did was that I became a superuser to execute the task by simply type **sudo** as already taught before the chown command was invoked again and the new result was shown below;

![sudo](./img/9b.sudo-comm.png)

Check the output with ls -latr command on this file to then see the new changes.

![ls-latr_chown](./img/9c.ls-latr_filename.png)


## Superuser Privileges

In Linux, some important tasks need special permission called superuser or root access. However, it’s not safe to stay logged in as the root user all the time.
To perform such tasks safely, Linux provides a tool called sudo (which means “super user do”). It lets you run specific commands with temporary root permission.
You just need to type **'sudo'** before the command you want to run with admin rights.

If you want to fully switch to the root user, simply run: **'sudo -i'**

![root](./img/10.root_user.png)

## Superuser Privileges

In Linux, some important tasks need special permission called superuser or root access. However, it’s not safe to stay logged in as the root user all the time.

To perform such tasks safely, Linux provides a tool called sudo (which means “super user do”). It lets you run specific commands with temporary root permission.

You just need to type sudo before the command you want to run with admin rights.

If you want to fully switch to the root user, simply run 





