cmake_minimum_required (VERSION 3.0.0)
project(neuralnetworks)

set(CMAKE_C_COMPILER             "clang")
set(CMAKE_C_FLAGS                "-Wall -std=c11")
set(CMAKE_C_FLAGS_DEBUG          "-g -D_DEBUG")
set(CMAKE_C_FLAGS_RELEASE        "-O3 -DNDEBUG")

set(SHARED_CXX_FLAGS "-ffast-math -DIMGUI_DEFINE_MATH_OPERATORS -DBT_THREADSAFE=1 -DGLM_ENABLE_EXPERIMENTAL -DBT_USE_DOUBLE_PRECISION")
set(CMAKE_CXX_COMPILER             "clang++")
set(CMAKE_CXX_FLAGS                "-Wall -std=c++17 ${SHARED_CXX_FLAGS}")
set(CMAKE_CXX_FLAGS_DEBUG          "-g -D_DEBUG")
set(CMAKE_CXX_FLAGS_RELEASE        "-O4 -DNDEBUG")

set(CMAKE_VERBOSE_MAKEFILE ON)

set(SOURCE_DIR "src")
#set(SUBMODULES_DIR "submodules")

file(GLOB PRIVATE_SOURCES
  ${SOURCE_DIR}/*.cpp
  )

#set(SOURCES ${PRIVATE_SOURCES} ${SUBMODULE_SOURCES})
set(SOURCES ${PRIVATE_SOURCES})

set(PRIVATE_INCLUDE_DIRS
  ${SOURCE_DIR}
)

link_directories(${PRIVATE_LIB_DIRS})
add_executable(neuralnetworks ${SOURCES})
