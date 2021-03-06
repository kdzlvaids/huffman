cmake_minimum_required(VERSION 2.4)

project(huffcomp C CXX)

# We need C++ 11
if(${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION} GREATER 3.1)
    set(CMAKE_CXX_STANDARD 11)
    set(CMAKE_CXX_STANDARD_REQUIRED on)
else(${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION} GREATER 3.1)
    set(CMAKE_CXX_FLAGS "-std=c++11")
endif(${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION} GREATER 3.1)

# Make an environment for build
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/build/bin)
set(LIBRARY_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/build/lib)

include_directories(${PROJECT_SOURCE_DIR}/include)

# Add the executable that is built from the source files
add_executable(huffcomp ${PROJECT_SOURCE_DIR}/src/main.cpp)

# Link the executable to the library
target_link_libraries(huffcomp LINK_PUBLIC huffman)
