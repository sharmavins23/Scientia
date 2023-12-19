In [[Operating System|OS]] abstractions, files are objects that the compiler handles which can store memory for longer periods of time. Files can be written to and read from. The operating system handles these via file descriptors, which are integers that also hold their positions in the files.

The file descriptors are stored in a file table, which is a listing of all file descriptors. The first three values are generally set to `stdin=0`, `stdout=1`, and `stderr=2`.

## Examples

### Printing to Stdout

Let's look at the following code:

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>

int main(int argc, char* argv) {
	char buffer[4] = "abc";
	char buffer2[4];

	// Assume "file.txt" exists but is empty
	int fd0 = open("file.txt", O_RDWR | O_CREAT, 0666);
	int fd1 = open("file.txt", O_RDWR | O_CREAT, 0666);
	int fd2 = 0;

	write(fd0, buffer, 3);
	write(fd0, buffer, 3); // File = abcabc

	read(fd1, buffer2, 2); // buffer2 = ab
	write(1, buffer2, 2); // Print ab

	dup2(fd1, fd2); // fd2 <= fd1

	read(fd2, buffer2, 2); // buffer2 = ca
	write(1, buffer2, 2); // Print ca
	read(fd2, buffer2, 1); // buffer2 = b
	write(1, buffer2, 1); // Print b

	return 0;
}
```

Let's examine this code more closely. Notice that the file descriptors individually track their position - As such, after the two `write()` calls, the file is written `abcabc`. The position for `fd0` is after the final `c`.

After the read and write, `fd1` reads from the start `[ab]cabc`. The print to `stdout` is handled within the `write()` call.

Next, `dup2()` stores `fd1` in `fd2`. As such, `fd2` now points to the file and has position of `ab|cabc`.

The next reads and writes read `ab[ca]bc` to the buffer, printing it out. Then, they read `abca[b]c` and print that single byte out.

### File Printing

Let's look at another example:

```c
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <unistd.h>

int main() {
    char buffer[4] = "abc";
    // Assume "file.txt" is initially empty
    int fd0 = open("file.txt", O_RDWR); // Init to 3
    int fd1 = 0;                        // Init to 0
    int fd2 = open("file.txt", O_RDWR); // Init to 4

    read(fd0, buffer, 1); // Empty, so no overwrite

    dup2(fd0, fd1); // fd1 now points to the file

    read(fd2, buffer+1, 2); // Empty, so no overwrite
    write(fd0, buffer, 3); // Writes "abc" to the file

    read(fd2, buffer, 1); // Reads 'a' from the file
    write(fd1, buffer, 1); // Writes 'a' back

	// Buffer now has "abc"
	// File now has "abca"

    return 0;
}
```

Looking through the code: The first read will not overwrite the buffer, nor will it increment the position of the file (since positions are only advanced when data is read or written).

The read for `fd2` will do nothing. The write then writes `abc` to the file. Note that `fd0` is now positioned at `abc|`. Since the `dup2()` call went through, `fd1`'s position is also at `abc|`, since these file 'pointers' are effectively equal.

Now that the file has information in it, `fd2`'s position is still at `|abc`. As such, the read will take one character and place it into the buffer - Now, the buffer overwrites `abc`'s first byte with `a`. As such, the buffer now has `abc`. The write simply places the `a` into the last position, so the file ends up with `abca|`.
