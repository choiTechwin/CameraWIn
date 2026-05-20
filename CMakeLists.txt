cmake_minimum_required(VERSION 3.20)

project(CameraWinVision LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(OpenCV REQUIRED)

add_executable(camera_win
    src/main.cpp
)

target_include_directories(camera_win PRIVATE
    ${OpenCV_INCLUDE_DIRS}
)

target_link_libraries(camera_win PRIVATE
    ${OpenCV_LIBS}
)

if (MSVC)
    target_compile_options(camera_win PRIVATE /W4 /permissive-)
else()
    target_compile_options(camera_win PRIVATE -Wall -Wextra -Wpedantic)
endif()
