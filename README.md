To create a static library and link it with the main source code, do the following steps:

1. Compile modules:
    g++ -std=c++17 -c tools.cpp
    This will produce the object file tools.o

2. Organize modules into libraries:
    ar rcs libmytools.a tools.o <other_modules>
    The archiver takes the module tools.o and creates a static library named libtools.a
    It is important to start the library name with 'lib'

3. Compile main application:
    g++ -std=c++17 -c main.cpp
    This will produce main.o

4. Link main application with the libraries:
    g++ -std=c++17 main.o -L . -lmytools -o main
    -L = To indicate the path of the library to the linker
    -lmytools = To tell the linker to link against the libmytools.a library