Download Link: https://assignmentchef.com/product/solved-cs-444-project-3-working-with-inodes-mystat
<br>
For this part of this assignment, you will write a C program that will <strong>display the </strong><strong>inode meta data for each file given on the command line</strong>. You must call you source file mystat.c and your program will be called mystat. <strong>This program will run directly on </strong><strong>os2, not within </strong><strong>xv6.</strong>

An example of how my program displays the inode data is shown the Figure 4. You might also want to look at the output from the stat command (the command not a system function, man section 1). Though not as pretty (or in some cases as complete as the replacement you will write), it is the standard for showing inode information.

<strong>Requirements</strong> for your program are:

<ol>

 <li><strong>The output of your program should look exactly like mine</strong>.</li>

 <li>Display the file type (regular, directory, symbolic link, …) as a human readable string. If the file is a symbolic link, look 1 step further to find the name of the file to which the symbolic link points.</li>

</ol>

If the file to which the link points does not exist, indicate that. See Figure 4.

<ol start="3">

 <li>Display the inode</li>

 <li>Display the device id.</li>

 <li>Display the mode as both its <strong>octal</strong> value and its symbolic representation. The symbolic representation will be the rwx string for user, group, and other. See Figure 4 or ‘ls -l’ for how this should look.</li>

 <li>Show the hard link count.</li>

 <li>Show both the uid and gid for the file, as both the symbolic values (names) and numeric values. <strong>This will be pretty darn easy if you read through the list of suggested function calls</strong>. See Figure 4 for how this should look.</li>

 <li>File size, in bytes.</li>

 <li>Block count.</li>

 <li>Show the 3 time values in <strong>local time/date</strong>. This will be pretty darn easy if you read through the list of suggested function calls. See Figure 4 for how these appear.</li>

</ol>

Figure 1: A sample of files to use for your testing. Found in ~chaneyr/Classes/cs444/Labs/Lab3

System and function calls that I believe you will find interesting include: stat()and lstat() (<strong>you really want to do “</strong><strong>man 2 stat” and read that </strong><strong>man entry closely, all of it [yes really, all of it])</strong>, readlink(), memset(), getpwuid(), getgrgid(), strcat(), localtime(), and

strftime(). Notice that ctime() is NOT in that list and you don’t want to use it. Since you must be able to show the file type if a file is a symbolic link, I encourage you consider lstat() over stat().

My implementation is about 280 lines long, but there is some dead code in my file. I have code commented out to support features not required for your assignment. There is no complex logic for this application, just a lot of long code showing values from the struct stat structure from sys/stat.h. Honestly, the longest portion of your code will likely be devoted to displaying the symbolic representation of the mode. Formatting these strings is a little <em>awkweird</em>. I suggest you create a function. Don’t worry about sticky bits or set uid/gid bits. Do you know what sticky bits are for or how they used to be used?

You must to be able to show the following file types:

<ul>

 <li>regular file,</li>

 <li>directory,</li>

 <li>character device,</li>

 <li>block device,</li>

 <li>FIFO/pipe,</li>

 <li>socket, and</li>

 <li>symbolic link (both a good one and a broken one).</li>

</ul>

When formatting the human readable time for the local time, I’d suggest you consider this “%Y-%m-%d

%H:%M:%S %z (%Z) %a”, but read through the format options on strftime(). The executable version of my code is in the directory. You are welcome to run it to see the output.

I have some examples of both a FIFO/pipe, a socket, symbolic link in my Lab3 directory for you to use in testing (the FUNNY* files, Figure 2). You can

find a block device as

/dev/sda and a <sup>character device as </sup>Figure 3: Block and character files.

/dev/sg0. See Figure 3.

You must have a Makefile that builds the mystat program, <strong>without any warnings from the compiler</strong>. You must use the following gcc command line options (with gcc as your compiler) in your Makefile when compiling your code:

-g

-Wall

-Wshadow

-Wunreachable-code

-Wredundant-decls

-Wmissing-declarations

-Wold-style-definition

-Wmissing-prototypes

-Wdeclaration-after-statement

When we grade your program, we will issue the following commands to build your executable.

make clean make all

<strong>There must be zero (0) warnings from the compiler. If your program compiles and produces warnings (using the above command line options for </strong><strong>gcc), then it is a zero. </strong>

<h1>Final note</h1>

The labs in this course are intended to give you basic skills. In later labs, we will <strong><em>assume</em></strong> that you have mastered the skills introduced in earlier labs. <strong>If you don’t understand, ask questions. </strong>

For those of you have read this far and are actually reading the entire assignment, thank you. As a reward, if you look at the section 2 man page for stat(), down near the bottom, I think you’ll like it. That is:

man 2 stat


