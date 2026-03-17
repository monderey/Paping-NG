cmake_minimum_required(VERSION 3.20)
project(paping LANGUAGES CXX)

set(CMAKE_CXX_STANDARD          20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS        OFF)

add_executable(paping src/paping.cpp)

if(MSVC)
    target_compile_options(paping PRIVATE
        /O2         # maximize speed
        /W4         # high warning level
        /WX-        # warnings not errors (tolerate MSVC pedantry)
        /utf-8      # source & execution charset UTF-8
        /GL         # whole-program optimization
    )
    target_link_options(paping PRIVATE /LTCG)
else()
    target_compile_options(paping PRIVATE -O3 -Wall -Wextra -Wpedantic)
endif()

if(WIN32)
    # ws2_32 is already pulled in by the #pragma comment for MSVC;
    # this covers MinGW / Clang-cl builds.
    target_link_libraries(paping PRIVATE ws2_32)
endif()
