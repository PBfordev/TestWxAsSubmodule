cmake_minimum_required(VERSION 3.1 FATAL_ERROR)
project(TestWxAsSubmodule)

add_subdirectory(Submodules/wx)
add_executable(myapp myapp.cpp)
target_link_libraries(myapp wx::core wx::base)
