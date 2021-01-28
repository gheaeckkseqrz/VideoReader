cmake_minimum_required(VERSION 3.12.4)
project(VideoReader)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON) # Generate data for clang-tidy

add_executable(VideoReader main.cpp)

enable_testing()
add_subdirectory(tests)
