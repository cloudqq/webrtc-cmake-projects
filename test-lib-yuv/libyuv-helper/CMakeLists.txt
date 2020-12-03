cmake_minimum_required(VERSION 3.17)

configure_file(CMakeLists.txt.in libyuv-download/CMakeLists.txt)
execute_process(COMMAND ${CMAKE_COMMAND} -G "${CMAKE_GENERATOR}" .
        RESULT_VARIABLE result
        WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/libyuv-download)
if(result)
    message(FATAL_ERROR "CMake step for libyuv failed: ${result}")
endif()

execute_process(COMMAND ${CMAKE_COMMAND} --build .
        RESULT_VARIABLE result
        WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/libyuv-download)
if(result)
    message(FATAL_ERROR "Build step for libyuv failed: ${result}")
endif()

add_subdirectory(${CMAKE_CURRENT_BINARY_DIR}/libyuv-src
        ${CMAKE_CURRENT_BINARY_DIR}/libyuv-build
        EXCLUDE_FROM_ALL )
