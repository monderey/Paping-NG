cmake_minimum_required(VERSION 3.15)
cmake_policy(SET CMP0091 NEW)

project(paping VERSION 1.0.2 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD          20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS        OFF)

add_executable(paping src/paping.cpp)

set_property(TARGET paping PROPERTY
    MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

if(MSVC)
    target_compile_options(paping PRIVATE
        /O2
        /W4
        /WX-
        /utf-8
    )
else()
    target_compile_options(paping PRIVATE -O3 -Wall -Wextra -Wpedantic)
endif()

if(WIN32)
    target_link_libraries(paping PRIVATE ws2_32)
endif()
