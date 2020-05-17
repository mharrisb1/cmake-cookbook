cmake_minimum_required(VERSION 3.13 FATAL_ERROR)
project(recipe-03 LANGUAGES CXX)

option(USE_LIBRARY "Compile sources into library"  OFF)

message(STATUS "Compile sources into a library? ${USE_LIBRARY}")

set(BUILD_SHARED_LIBS OFF)

list(APPEND _sources 
    include/message.hpp 
    src/message.cpp
    )

if(USE_LIBRARY)
    # add_library will create a static library
    # since BUILD_SHARED_LIBS is off
    add_library(message ${_sources})
    add_executable(hello-world src/main.cpp)
    target_link_libraries(hello-world message)
else()
    add_executable(hello-world src/main.cpp ${_sources})
endif()
