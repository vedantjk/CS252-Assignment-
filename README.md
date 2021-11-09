# CS-252-OS-Assignment

The assignment consists of two questions from the exercise section of the 10th edition of Operating
System Concepts by Abraham Silberschatz, Peter Baer Galvin and Greg Gagne.



## Questions
**[Question 1: Chapter 2- 2.24]**

In Section 2.3, we described a program that copies the contents of one file
to a destination file. This program works by first prompting the user for
the name of the source and destination files. Write this program using
either the POSIX or Windows API. Be sure to include all necessary error
checking, including ensuring that the source file exists.

Once you have correctly designed and tested the program, if you used
a system that supports it, run the program using a utility that traces system calls. Linux systems provide the strace utility, and macOS systems
use the dtruss command. (The dtruss command, which actually is a
front end to dtrace, requires admin privileges, so it must be run using
sudo.) These tools can be used as follows (assume that the name of the
executable file is FileCopy:

**Linux:
strace ./FileCopy**

**macOS:
sudo dtruss ./FileCopy**

Since Windows systems do not provide such a tool, you will have to
trace through the Windows version of this program using a debugger.

**[Question 2: Chapter 10- 10.44]**

Write a program that implements the FIFO, LRU, and optimal ( OPT)
page-replacement algorithms presented in Section 10.4. Have your pro-
gram initially generate a random page-reference string where page
numbers range from 0 to 9. Apply the random page-reference string to
each algorithm, and record the number of page faults incurred by each
algorithm. Pass the number of page frames to the program at startup.
You may implement this program in any programming language of
your choice.


## Author(s)

Vedant Kodagi - 191ME194
