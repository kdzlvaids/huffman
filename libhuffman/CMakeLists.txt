cmake_minimum_required(VERSION 2.4)

project(libhuffman C CXX)

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

# Create a library
add_library(huffman SHARED ${PROJECT_SOURCE_DIR}/lib/huffman.cpp)

# Make sure the compiler can find include files for our library
target_include_directories(huffman PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
