cmake_minimum_required(VERSION 3.13.0)

project(AiFrameworkTestApp)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_subdirectory(vendor/AiFramework)

add_executable(AiFrameworkTestApp app.cpp)

target_link_libraries(AiFrameworkTestApp PUBLIC AiFramework)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/output)