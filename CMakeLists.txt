cmake_minimum_required(VERSION 3.10)
project(CS2Overlay)

set(CMAKE_CXX_STANDARD 17)

add_executable(CS2Overlay 
    src/main.cpp
)

target_link_libraries(CS2Overlay 
    User32
    Gdi32
)
