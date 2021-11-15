## Some System Calls in strace_log

---

- Line 1
  `execve("./224.o", ["./224.o"], 0x7ffd754c0758 /* 46 vars */) = 0`
- ` int execve(const char *pathname, char *const argv[],char *const envp[]);`

execve() executes the program referred to by pathname.  This causes the program that is currently being run by the calling process to be replaced with a new program, with newly initialized stack, heap, and (initialized and uninitialized) data segments.

---
- Line 2 `brk(NULL)                               = 0x6a8000`
- `int brk(void *addr);`

change data segment size

---

- Line 3 `arch_prctl(0x3001 /* ARCH_??? */, 0x7ffc60d68b80) = -1 EINVAL (Invalid argument)`
- `int syscall(SYS_arch_prctl, int code, unsigned long addr);`

- `int syscall(SYS_arch_prctl, int code, unsigned long *addr);`

arch_prctl() sets architecture-specific process or thread state. code selects a subfunction and passes argument addr to it; addr is interpreted as either an unsigned long for the "set" operations, or as an unsigned long *, for the "get" operations.


---

- Line 4 `access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)`
- `int access(const char *pathname, int mode);`

access() checks whether the calling process can access the file pathname. The mode specifies the accessibility check(s) to be performed, and is either the value F_OK, or a mask consisting of the bitwise OR of one or more of R_OK, W_OK, and X_OK.  

---

- Line 5 `openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3`
- `int openat(int dirfd, const char *pathname, int flags);`

The open() system call opens the file specified by pathname. If the specified file does not exist, it may optionally (if O_CREAT is specified in flags) be created by open().  The argument flags must include one of the following access modes: O_RDONLY, O_WRONLY, or O_RDWR.  These request opening the file read-only, write-only, or read/write, respectively.

---

- Line 6 `newfstatat(3, "", {st_mode=S_IFREG|0644, st_size=58416, ...}, AT_EMPTY_PATH) = 0`
- `int fstat(int fd, struct stat *statbuf);`

It is used to get file status. fstat() is identical to stat(), except that the file about which information is to be retrieved is specified by the file descriptor fd.

---

- Line 7 `mmap(NULL, 58416, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fc73f51c000`
- ` void *mmap(void *addr, size_t length, int prot, int flags, int fd, off_t offset);`

mmap() creates a new mapping in the virtual address space of the calling process.  The starting address for the new mapping is specified in addr.  The length argument specifies the length of the mapping (which must be greater than 0).

 ---

- Line 8 `close(3)                                = 0`
- `int close(int fd);`

close() closes a file descriptor, so that it no longer refers to any file and may be reused.

  ---

- Line 10 `read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260|\2\0\0\0\0\0"..., 832) = 832`
- `ssize_t read(int fd, void *buf, size_t count);`

read() attempts to read up to count bytes from file descriptor fd into the buffer starting at buf.

  ---

- Line 11 `pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784`
- `ssize_t pread(int fd, void *buf, size_t count, off_t offset);`

pread() reads up to count bytes from file descriptor fd at offset (from the start of the file) into the buffer starting at buf.  The file offset is not changed.

   ---

- Line 18 `mprotect(0x7fc73f371000, 1679360, PROT_NONE) = 0`
- ` int mprotect(void *addr, size_t len, int prot);`

mprotect() changes the access protections for the calling process's memory pages containing any part of the address range in the interval [addr, addr+len-1]. 

Some prot flags:

*PROT_NONE* : The memory cannot be accessed at all.

*PROT_READ* : The memory can be read.

*PROT_WRITE* : The memory can be modified.

*PROT_EXEC* : The memory can be executed.

---

- Line 33 `write(1, "Enter the filename to open for r"..., 40) = 40`
- ` ssize_t write(int fd, const void *buf, size_t count);`

write() writes up to count bytes from the buffer starting at buf to the file referred to by the file descriptor fd.

---

- Line 49 `lseek(0, -1, SEEK_CUR)                  = -1 ESPIPE (Illegal seek)`
- `off_t lseek(int fd, off_t offset, int whence);`

lseek() repositions the file offset of the open file description associated with the file descriptor fd to the argument offset according to the directive whence as follows:

*SEEK_SET* : The file offset is set to offset bytes.

*SEEK_CUR* : The file offset is set to its current location plus offset bytes.

*SEEK_END* : The file offset is set to the size of the file plus offset bytes.

---

- Line 50 `exit_group(0)                           = ?`

exit all threads in a process

---

## Reference(s):
 - https://man7.org/linux/man-pages/dir_all_by_section.html
