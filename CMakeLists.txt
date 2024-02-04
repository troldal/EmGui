cmake_minimum_required(VERSION 3.26)

project(EmGui
        VERSION 0.0.1
        LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_subdirectory(ImGui)
add_subdirectory(ImPlot)
add_subdirectory(Demo)
