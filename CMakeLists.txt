cmake_minimum_required(VERSION 3.12.4)

# Include Hunter.
# Hunter is a CMake based package manager that will clone the source code of FFmpeg, build it localy,
# and make the libraries available as if they where installed as system packages.
include("third_party/cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/cpp-pm/hunter/archive/v0.23.291.tar.gz"
    SHA1 "4f57243b24a02b9c7ec5ea02c09d5c77c6a97cba"
)
project(VideoReader)

# Will download and build FFMpeg from source
hunter_add_package(ffmpeg)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON) # Generate data for clang-tidy

add_executable(VideoReader main.cpp)

enable_testing()
add_subdirectory(tests)
