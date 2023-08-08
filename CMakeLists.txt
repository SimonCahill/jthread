cmake_minimum_required(VERSION 3.10)

project(jthread VERSION 1.0.0 LANGUAGES CXX DESCRIPTION "CMake-compatible version of the jthread library made by josuttis/jthread")
set(CMAKE_CXX_STANDARD 11)

# Get files
file(GLOB_RECURSE HEADERS FOLLOW_SYMLINKS ${CMAKE_CURRENT_SOURCE_DIR}/source/*.hpp)

set(INCLUDE_DIR ${CMAKE_CURRENT_BINARY_DIR}/include)

file(MAKE_DIRECTORY ${INCLUDE_DIR})

foreach (header ${HEADERS})
    file(COPY ${header} DESTINATION ${INCLUDE_DIR})
endforeach()

add_library(${PROJECT_NAME} INTERFACE)
target_include_directories(${PROJECT_NAME} INTERFACE ${INCLUDE_DIR})
