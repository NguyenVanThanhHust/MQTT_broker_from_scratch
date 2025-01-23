cmake_minimum_required(VERSION 3.10)

project(mqtt)

option(DEBUG "add debug flags" OFF)

if(DEBUG)
    message(STATUS "configure build for debug")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -Wunused -Werror -std=c11 -O3 -pedantic -luuid -ggdb -fsanitize=address -fsanitize=undefined -fno-omit-frame-pointer -pg")
else
    message(STATUS "configure build for release")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -Wunused -Werror -Wextra -std=c11 -O3 -pedantic -luuid")
endif(DEBUG)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR})

file(GLOB SOURCES src/*.c)

set(AUTHOR "Nguyen Van Thanh")
set(ORIGINAL_AUTHOR "Andrea Giacomo Baldan")
set(LICENSE "BSD2 license")

# Executable
add_executable(sol ${SOURCES})