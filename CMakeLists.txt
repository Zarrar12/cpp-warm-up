cmake_minimum_required(VERSION 3.1)
project(dynamic_library)

add_library(tools SHARED tools.cpp)
add_executable(main main.cpp)
target_link_libraries(main tools)