cmake_minimum_required(VERSION 3.10)
project(I2CPP)

set(CMAKE_CXX_STANDARD 11)
## Install libraries (if any) to <install_directory>/bin
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

if(UNIX AND NOT APPLE)
    set(LINUX TRUE)
endif()



file(GLOB_RECURSE SOURCES src/*.cpp)


add_library(i2cpp ${SOURCES})

target_include_directories(i2cpp PUBLIC include)
target_include_directories(i2cpp PRIVATE src)
if(NOT LINUX)
    target_include_directories(i2cpp PRIVATE hack_include)
endif()