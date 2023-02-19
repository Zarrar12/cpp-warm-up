To create a static library and link it with the main source code, do the following steps:
a. Manual Method:
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

b. Automated Method:
1. add_library(tools tools.cpp) 
    This statement creates the object file of tools.cpp and also generates the static library using tools.o. This means that steps 1 and 2 have combined in this.

2. add_executable(main main.cpp)
    Similar to step 3 of manual method.

3. target_link_libraries(main tools)
    Similar to step 4 of manual method.

To use this method create 'build' folder in the project directory, cd to the driectory and run 'cmake ../' and then 'make'.
