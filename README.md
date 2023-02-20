To create a dynamic library and link it with the main source code, do the following steps:

a. Manual Method:
1. Compile modules:
    g++ -std=c++17 -c tools.cpp -fpic OR
    g++ -std=c++17 -c tools.cpp -fPIC
    -fpic generates position independent code (PIC) suitable for use in the shared library, if supported on the target machine. Such code accesses all constant addresses through global offset table (GOT). The dynamic loader resolves the GOT entries when the program starts (the dynamic loader is not part of GCC but the OS).

2. Organize modules into libraries:
    g++ tools.o -shared -o libtools.so
    -shared produces a shared object which can then be linked with other objects to form an executable.
    It is important to start the library name with 'lib'

3. Compile main application:
    g++ -std=c++17 -c main.cpp
    This will produce main.o

4. Link main application with the libraries:
    There are two ways to link the library:
    
    Method-1:   Add the path of the folder containing the library to the environment variable LD_LIBRARY_PATH.
    a) pwd to get the /path/to/the/library
    b) export LD_LIBRARY_PATH=:/path/to/the/library
    C) g++ -std=c++17 main.o -L . -lmytools -o main
    -L = To indicate the path of the library to the linker
    -lmytools = To tell the linker to link against the libmytools.a library

    Method-2:   Place the *.so file in /usr/lib/
    a) cp from/the/folder/*.so /usr/lib/
    b) g++ main.o -ltools -o main