cmake_minimum_required(VERSION 3.17)
project(test_lib_yuv)

set(CMAKE_CXX_STANDARD 14)

FIND_PACKAGE(JPEG)
add_subdirectory(libyuv-helper)

add_executable(test_lib_yuv main.cpp

        )

target_link_libraries(
        test_lib_yuv

        yuv
)

