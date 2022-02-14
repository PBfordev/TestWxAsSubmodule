cmake_minimum_required(VERSION 3.1 FATAL_ERROR)
project(TestWxAsSubmodule)

set(SOURCES myapp.cpp)
if (WIN32)
  list(APPEND SOURCES myapp.rc)
endif()

if (MSVC) # the manifest is added with wxUSE_RC_MANIFEST in myapp.rc
  set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /MANIFEST:NO")
endif()

add_subdirectory(Submodules/wx)
add_executable(${PROJECT_NAME} WIN32 ${SOURCES})
target_link_libraries(${PROJECT_NAME} wx::core wx::base)
if (wxBUILD_SHARED AND WIN32)
  target_compile_definitions(${PROJECT_NAME} PRIVATE WXUSINGDLL)
endif()