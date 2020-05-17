cmake_minimum_required(VERSION 3.13 FATAL_ERROR)
project(recipe-02)

include_directories(include)

add_library(message
    STATIC
      include/message.hpp
      src/message.cpp
    )

add_executable(hello-world src/main.cpp)
target_link_libraries(hello-world message)

