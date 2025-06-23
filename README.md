````markdown
# mymalloc

This project implements our own version of `malloc` for dynamically allocating memory, instead of using the API provided by the C library.

The idea is to understand how memory is allocated during runtime, and the implementation does exactly that with no additional features.
````
## How to Run

To compile and run the program, use the following commands:

```bash
g++ mymalloc.cpp -o program_name
./program_name
````

## Implementation Details

Linux provides a system call (`sbrk`) for manipulating the heap region of the process. Whenever the programmer requests dynamic memory, `sbrk` is invoked and returns the address if the allocation is successful.

Instead of returning the freed blocks to the OS, we keep them for future reusability by storing metadata in the form of a linked list whenever a new request comes up.

The implementation has no memory leaks and has been verified via Valgrind.

## Future Improvements

* Testing with `mmap` instead of `sbrk`
* Adding more features to make the API more robust
