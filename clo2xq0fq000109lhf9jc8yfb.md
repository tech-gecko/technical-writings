---
title: "Shell Navigation"
datePublished: Mon Oct 23 2023 13:29:55 GMT+0000 (Coordinated Universal Time)
cuid: clo2xq0fq000109lhf9jc8yfb
slug: shell-navigation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697997720676/e3b1e43b-b04e-41f5-bb2f-fed2f1a90241.png
tags: linux, shell, linux-for-beginners, linux-commands, shell-navigation

---

In our last blog post, we introduced the concept of the shell. We explained to the smallest detail possible so that even readers who are not tech enthusiasts could be able to understand the concept.

Today, we are going to focus on shell navigation in terms of basic shell commands and file manipulation.

### Basic Shell Commands

The first three basic Linux commands we would be learning about are `pwd` (print working directory), `cd` (change directory) and `ls` (list all files and directories of the current directory).

**File System Organization**

Similar to Windows, Linux systems organize files in a ***hierarchical*** directory structure, forming a tree-like pattern of directories (known as folders in other systems). These directories can contain files and additional subdirectories. The primary directory at the top of this structure is called the ***root*** directory, from which various files and subdirectories extend, creating a chain of directories within directories.

Most graphical interfaces feature a file manager tool, allowing users to navigate and manipulate the file system. The visual representation of the file system often resembles a ***tree structure***.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698013101836/e6c50ef5-cc83-475f-94b2-ad3330b27fa6.png align="center")

A notable contrast between Windows and Unix-like operating systems, such as Linux, lies in the absence of drive letters in Linux. Unlike Windows, where drive letters represent separate file system trees for different devices, Linux maintains a unified tree structure. Different storage devices may be viewed as distinct branches within this single tree, but there is always just one overarching hierarchical structure.

### pwd

As the command line interface lacks the visual representation of the file system structure, an alternative method is needed to depict it. Imagine the file system tree as a maze, and envision ourselves within it. At any point, we find ourselves situated in a specific directory. Within this directory, we can observe its files, the route back to its parent directory, and the pathways leading to its subdirectories.

This particular directory where we are positioned is termed the ***working directory***. To identify the name of the working directory, we utilize the `pwd` command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698015053700/8fb3913d-3d27-4a2d-9408-ba02cc74c186.png align="center")

Upon initial login to our Linux system, the working directory is automatically configured to be our home directory, which serves as the designated location for storing our files. Typically, the home directory path follows the format /home/user\_name on many systems. However, it can be customized at the discretion of the system administrator to any other desired location.

To list the files in the working directory, we use the `ls` command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698015480996/f458c1fd-53b9-4751-ac4a-eacce341a033.png align="center")

### cd

To modify the current working directory within the maze-like file system, we employ the `cd` command. This involves typing `cd` followed by the ***pathname of the target working directory***. A pathname essentially represents the route taken along the branches of the tree to reach the desired directory. Pathnames can be expressed in two distinct manners: ***absolute pathnames*** or ***relative pathnames***. First, let's explore absolute pathnames.

An ***absolute pathname*** initiates from the root directory and meticulously follows each branch of the tree until reaching the desired directory or file, outlining the ***complete path***. Consider a directory within your system where the majority of programs are installed, identified by the pathname /usr/bin. In this context, starting from the root directory (indicated by the leading slash in the pathname), there exists a directory named "usr," within which resides another directory named "bin."

In practice, it looks like:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698016559816/847ea7a4-5389-446c-8a22-449349c6f225.png align="center")

Now, it becomes evident that the current working directory has been modified to /usr/bin, and this directory is brimming with files. Can you observe the alteration in the shell prompt? Typically, for convenience, it's configured to exhibit the name of the current working directory.

In contrast to ***absolute pathnames*** that start from the root directory and traverse down to the destination, ***relative pathnames*** originate from the working directory. To achieve this, they employ special notations indicating relative positions within the file system tree, namely "." (dot) and ".." (dot dot).

The "." notation signifies the working directory itself, while ".." indicates the parent directory of the working directory. Here's how these notations function:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698040086013/4d95514f-ed28-447d-a5d7-84aa6aa5e63b.png align="center")

First, we navigated into the /usr/bin folder using the ***absolute pathname*** with `cd`, then we went back to the parent folder, "usr" using the ***relative pathname*** with the ".." notation. Then, we went back to the bin folder using the ***relative pathname*** with the "." notation. Note that the "./" can be ignored most of the time when trying to go into a file or subdirectory within the current directory.

Something worth noting in this example is that, in the first use of "..", it meant the /usr folder which was the parent folder at the time because we were in the usr/bin folder, a subdirectory within that (parent) directory. When "." was used, however, it also meant the /usr directory/folder because it wasn't our parent directory, but our working directory at the time. I hope you understand the difference.

**Some shortcuts**

When we enter `cd` without specifying a directory, it will automatically switch the current working directory back to our home directory. Another (slower) method is to use "`cd` ~".

There's another quick method: typing "`cd` ~user\_name". With this command, `cd` will shift the working directory to the home directory of the specified user.

Additionally, typing "`cd` -" directs the working directory to the previous one we were in.

**Important facts about file names**

* Files starting with a period are considered hidden in Linux. This means that the `ls` command won't display them unless you specify `ls -a`. When your account was created, hidden files were added to your home directory for configuration purposes. Later, we'll explore these files in detail to show you how to personalize your environment. Additionally, some applications store their configuration files in your home directory as hidden files.
    
* In Linux, file names are case-sensitive. For instance, "File1" and "file1" are treated as distinct files.
    
* Unlike Windows systems, Linux doesn't rely on file extensions. You're free to name files however you prefer. Nevertheless, even though Linux itself isn't concerned about file extensions, many applications are.
    
* Linux does support lengthy file names that can include spaces and certain punctuation marks, although it's advisable to limit punctuation to period, dash, and underscore. Most importantly, avoid using spaces in file names. If you need to indicate spaces between words, it's better to use underscores. This practice will prove beneficial later on.
    

### Looking Around

Having learned how to navigate between directories, we're set to explore our Linux system. Along this journey, we'll uncover insights into its functionality. But before we embark on this adventure, it's essential to acquaint ourselves with some useful tools that will be valuable during our exploration. These tools include:

* `ls` (lists all files and directories within the current working directory).
    
* `less` (to view text files).
    
* `file` (classify the contents of a file).
    

### ls

The `ls` command lists all files and directories within the current working directory. It is arguably the most used Linux command. Below are examples of the use cases of `ls`:

| Command | What it does |
| --- | --- |
| `ls` | lists all files and directories within the current working directory. |
| `ls` **\-l** | lists all files and directories within the current working directory in the long format. |
| `ls` **/usr** | lists all files and directories within the "usr" directory. |
| `ls` **\-l /usr /proc** | lists all files and directories within the "usr" and "proc" directories in the long format. |
| `ls` **\-la ..** | lists all files and directories (including hidden ones) in the parent directory of the current working directory in the long format. |

These examples also point out an important concept about commands. Most commands operate like this:

`command` *\-option(s)* **&lt;argument(s)&gt;**

where `command` is the name of the command, *options* are flags that modify the bahaviour of the command, and **arguments** are the "object(s)" on which the command operates.

Considering my fourth example use case of `ls`, `ls` itself is the ***command name***, *\-l* is an ***option***(also called a ***flag***) to list in long format and ***/usr*** and ***/proc*** are the ***arguments*** of the command.

**The Long Format**

Using the *\-l* option with `ls` gives the long format file listing. Check out the image below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698044550054/801ecb67-cd79-4950-958f-c05176a81e67.png align="center")

The long format provides information about:

**File Name:** The title of the file or directory.

**Modification Time:** The most recent time the file was changed. If the last change occurred over six months ago, the date and year are displayed. Otherwise, the specific time of day is shown.

**Size:** The file's size, measured in bytes.

**Group**: The name of the group that holds file permissions, apart from the file's owner.

**Owner:** The name of the user who possesses the file.

**File Permissions:** A representation of the file's accessibility rights. The first character signifies the file type - a "-" denotes a regular file, while a "d" indicates a directory. The subsequent three characters indicate the read, write, and execute permissions of the file's owner. The following three represent the group's permissions, and the final three represent the permissions granted to everyone else. A more detailed explanation of this will be provided in an upcoming lesson.

### less

`less` is a program or command that lets us view text files. The importance of this cannot be over-exaggerated as we always work with files with text in them as programmers.

**What really is "text"?**

Representation of information between humans and computers can be done in numerous ways. Each one of these ways always involves devising a means by which the information is "understandable" to a computer by converting the information into numeric format, which is the only language computers understand in reality.

Various representation systems exhibit differing levels of complexity, ranging from intricate ones like compressed multimedia files to more straightforward formats. One of the earliest and basic systems is known as ASCII text. ASCII, short for American Standard Code for Information Interchange and pronounced as "As-Key," is a straightforward encoding method initially used on Teletype machines to convert keyboard characters into numerical values.

Text, in ASCII, adheres to a simple principle where characters are mapped to specific numbers. This method is highly space-efficient; fifty characters of text equate to fifty bytes of data. Text files in Linux systems often utilize this format, and numerous Linux tools are designed to handle such files. Even in Windows systems, the importance of ASCII text format is acknowledged. For instance, the renowned NOTEPAD.EXE program serves as an editor for plain ASCII text files.

The `less` command is used in this way:

`less` **&lt;text\_filename&gt;**

and this will display the file to be read (not edited).

**Navigating text files with** `less`

| Command | What it does |
| --- | --- |
| h | displays a complete list of `less` commands and options. |
| Page Up / b | scroll back one page. |
| Page Down / space | scroll forward one page. |
| G | go to the end of the text file. |
| 1G | go to the beginning of the text file. |
| */characters* | search forward in the text file for an occurence of the specified *characters.* |
| n | repeat the previous search. |
| q | quit. |

### file

While exploring our Linux system, it's beneficial to identify the type of data a file holds before attempting to view its contents. This is where the `file` command proves valuable. By using `file`, we can analyze a file and receive information about its file type.

The `file` command is used in this way:

`file` **&lt;file\_name&gt;**

The `file` command recognizes a wide range of file types. While it may seem that most files cannot be viewed as text, a surprising number can be. This is especially true of the important configuration files. During our adventure we will see that many features of the operating system are controlled by text configuration files and shell scripts. In Linux, there are no secrets!

### File Manipulation Commands

The main file manipulation commands which will be discussed in this topic are:

* `cp`
    
* `mv`
    
* `rm`
    
* `mkdir`
    

Certainly, certain tasks accomplished through these commands can be handled more conveniently with a graphical file manager. With such a tool, you can effortlessly drag and drop files between directories, cut, paste, and delete files, among other actions. So, what's the rationale behind using these traditional command line programs?

The answer lies in their power and versatility. While basic file operations are simple using a graphical file manager, complex tasks become more manageable with command line programs. Consider this scenario: how would you copy all **HTML** files from one directory to another, ensuring you only copy files that don't exist in the destination directory or are newer versions than those in the destination? This task might be quite challenging with a file manager but is relatively straightforward with the command line. It is done using the command below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698056516144/c74c5b78-910e-459d-afc9-704ac96f21cf.png align="center")

**Wildcards**

Before delving into specific commands, let's explore a feature within the shell that amplifies their effectiveness. Given the frequent use of filenames, the shell offers special characters known as wildcards. Wildcards enable quick selection of groups of filenames by matching patterns of characters. The following table outlines these wildcards and their corresponding selections:

| Wildcard | Meaning |
| --- | --- |
| \* | Matches any characters. |
| ? | Matches any single character. |
| \[characters\] | Matches any character that is a member of the set ***characters***. The set of characters may also be expressed as a ***POSIX character class*** such as one of the following: |

\[:alnum:\] --&gt; alphanumeric characters.  
\[:alpha:\] --&gt; alphabetic characters.  
\[:digit:\] --&gt; numeric characters.  
\[:upper:\] --&gt; uppercase alphabetic characters.  
\[:lower:\] --&gt; lowercase alphabetic characters.  
\[!characters\] --&gt; Matches any character that is not a member of the set ***characters***.

Some example use cases of wildcards are:

* \* --&gt; all filenames.
    
* b\* --&gt; all filenames beginning with the character "b".
    
* c\*.txt --&gt; all filenames beginning with a "c" and ending with ".txt".
    
* File??? --&gt; any file that begins with the characters "File" followed by exactly three more characters.
    
* \[abc\]\* --&gt; any filename beginning with an "a" or a "b" or a "c" followed by any other characters.
    
* \[\[:lower:\]\]\* --&gt; any filename that begins with a lowercase character. This is an example of a character class.
    
* Linux \[\[:digit:\]\] \[\[:digit:\]\] --&gt; any filename that begins with "Linux" followed by exactly two digits. It is another example of a character class.
    
* \*\[!\[:upper:\]\] --&gt; any filename that does not end with an uppercase letter.
    

We can use wildcards with any command that accepts filename arguments.

### cp

The `cp` command copies files and directories. In its simplest form, it copies a single file. It can also be used to copy multiple files and/or directories to a different directory. It can be done using the command below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698059195280/bf2016e4-e155-49dc-9fac-d91196da93a4.png align="center")

The "..." signifies that an item can be repeated one or more times. Other useful examples of `cp` and its options include:

* `cp` **&lt;file\_1&gt; &lt;file\_2&gt; --&gt;** copies the content of file\_1 into file\_2. If file\_2 does not exist, it is created.
    
* `cp` *\-i* **&lt;file\_1&gt; &lt;file\_2&gt; --&gt;** since the interactive ("*\-i"*) option is specified, if file\_2 exists, the user is prompted before it is overwritten with the contents of file\_1.
    
* `cp` **&lt;file\_1&gt; &lt;dir\_1&gt; --&gt;** copies the contents of file\_1 into a file named file\_1 inside of directory dir\_1.
    
* `cp` *\-R* **&lt;dir\_1&gt; &lt;dir\_2&gt; --&gt;** copies the contents of the directory dir\_1 into dir\_2. If directory dir\_2 does not exist, it is created. Otherwise, it creates a directory named dir\_1 within directory dir\_2.
    

### mv

The `mv` command can either relocate or rename files and directories, depending on its usage. It can move one or more files to another directory or change the name of a file or directory. When renaming a file, the command is utilized in the following manner:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698062133482/e8c92d2d-862d-4509-94ac-61a1464c9d74.png align="center")

This changes the name of &lt;**filename\_1&gt;** to &lt;**filename\_2&gt;**. On the other hand, moving a file or directory from one location to another is done this way:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698062531020/d4a565e4-218c-4f2e-84fa-f7ad4bcf9d3e.png align="center")

Example use cases of `mv` are applied as in `cp` above.

### rm

The `rm` command removes (deletes) files and directories. We use basic `rm` for files and the recursive `rm` ("`rm` *\-r*") for directories. Usage below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698063988959/34fd981f-69a2-48cb-8d22-ed45982bc7e7.png align="center")

Example use cases of `rm` and its options include:

* `rm` **&lt;file1&gt; &lt;file2&gt; --&gt;** deletes file1 and file2.
    
* `rm` *\-i* **&lt;file1&gt; &lt;file2&gt; --&gt;** deletes file1 and file2, but first displays a prompt (interactive) each time the deletion is to take place.
    
* `rm` *\-r* **&lt;dir1&gt; &lt;dir2&gt; --&gt;** deletes directories dir1 and dir2, along with all of their contents (recursive deletion).
    

**Note Below**

Exercise caution when using `rm`! Unlike some systems, Linux lacks an undelete feature. Once you delete a file with `rm`, it's permanently erased. Carelessness, especially with wildcards, can lead to significant damage to your system.

Before employing `rm` with wildcards, consider this useful approach: construct your command using `ls` instead. This way, you can preview the impact of your wildcards before deleting any files. After testing your command with `ls`, you can recall it using the up-arrow key and then replace `ls` with `rm` to execute the deletion.

### mkdir

This is simply a command used to create a new directory. Usage below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698065017077/1d613edb-66bf-409b-9631-0242f482cd1e.png align="center")

Some commands that were not outlined in this post are:

* `rmdir` --&gt; removes (deletes) an empty directory.
    
* `touch` --&gt; creates an empty file or updates file modification time.
    
* `du` --&gt; estimates file space usage.
    
* `echo` --&gt; "echoes" input. That is, it prints exactly the text typed in quotes after the `echo` command to standard output.
    

### Using Commands with Wildcards

As the commands discussed here allow multiple filenames and directories as inputs, you can employ wildcards to define them. Here are a few illustrations:

| Command | What it does |
| --- | --- |
| `cp` \*.txt ***text\_files*** | Duplicate all files in the present working directory that conclude with the ".txt" characters and move them to an existing directory named ***text\_files***. |
| `mv` &lt;**dir1&gt;** ../\*.bak &lt;**dir2&gt;** | Transfer the subdirectory &lt;**dir1&gt;** and all files with names ending in ".bak" from the parent directory of the current working directory to an existing directory called &lt;**dir2&gt;**. |
| rm \*~ | Remove all files in the current working directory that have names ending with the character "~". Certain applications generate backup files following this naming convention. Executing this command will clear these files from the directory. |

***Next Topic: Introduction to Text Editors: Vi(m) and Emacs.***