cmake_minimum_required(VERSION 3.5)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(FaaRay VERSION 0.1 LANGUAGES CXX)

#add_compile_definitions(CLASS_DEBUG)
#add_compile_definitions(SHARED_POINTER_DEBUG)

execute_process(COMMAND git submodule update --init --recursive
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})

add_subdirectory(extern/GFA)

file(GLOB MORE_TARGETS RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} */*.cpp )
add_library(FaaRay ${MORE_TARGETS})
target_link_libraries(FaaRay PRIVATE GFA)
target_include_directories(FaaRay PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
