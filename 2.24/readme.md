
# Q 2.24 Solution

Note: All the information written below is specific to Fedora operating system

---

## Requirements

You will require the GNU Compiler Collection (GCC) in order to be able to run the program **224.c**. By default Fedora comes installed with GCC.

---

## Steps to run the program
 - Open the terminal and navigate to the directory where the file **224.c** is present.
 - Create a text file (used as an input file) from which you would like to copy the contents in the same directory as the source file.
 - `gcc answer.c -o 224.o`
 - `./224.o`
 - The program will prompt to enter the name of the input file and output file.
 -  If it has been executed successfully, a "Contents copied to output.txt" message will be displayed.

## Screenshots
- Creating the files.

![App Screenshot](https://github.com/vedantjk/CS252-Assignment-/blob/main/2.24/images/Creating%20input%20and%20output%20files.png)

- Running the program.

![App Screenshot](https://github.com/vedantjk/CS252-Assignment-/blob/main/2.24/images/Compiling%20and%20running%20the%20code.png)

- After running the program.

![App Screenshot](https://github.com/vedantjk/CS252-Assignment-/blob/main/2.24/images/Result%20after%20running%20the%20code.png)

- After refreshing the output file.

![App Screenshot](https://github.com/vedantjk/CS252-Assignment-/blob/main/2.24/images/Result%20after%20refreshing%20the%20output%20page.png)

---

### Command to create a log file in which the system calls are logged
- Installing strace.

![App Screenshot](https://github.com/vedantjk/CS252-Assignment-/blob/main/2.24/images/Installing%20strace.png)
- `strace -ostrace_log ./224.o`
- The program will prompt the user to provide the name of the input file and output file
- If it has been executed successfully, a "Contents copied to output.txt" message will be displayed

## Screenshots
- Running the strace command to trace the system calls

[View the strace_log file](https://github.com/vedantjk/CS252-Assignment-/blob/main/2.24/strace_log)

![App Screenshot](https://github.com/vedantjk/CS252-Assignment-/blob/main/2.24/images/Running%20the%20strace%20command.png)


---

## Implementation

- A program was written in C language for copying the contents from an existing file and paste the contents into a new file (which does not exist before executing the program).
- The input file was input.txt from which the contents were copied.
- The output file was output.txt to which the copied content was pasted.
- A strace_log file was also created in which all the system calls were logged.



## Reference(s)
- https://www.geeksforgeeks.org/c-program-copy-contents-one-file-another-file/
- The code for the assignment has been taken from the above repository
- https://man7.org/linux/man-pages/dir_all_by_section.html
- The above link was used to refer to the different system calls logged in the **strace_log** file
