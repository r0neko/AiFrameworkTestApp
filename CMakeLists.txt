cmake_minimum_required(VERSION 3.13.0)

project(AiFrameworkTestApp)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_subdirectory(vendor/AiFramework)

add_executable(AiFrameworkTestApp app.cpp)

target_link_libraries(AiFrameworkTestApp AiFramework)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/output)

# move AiFramework into our build folder
# dirty hack but it should work I guess.
if (WIN32 OR LINUX)
    add_custom_command(TARGET AiFrameworkTestApp POST_BUILD
            COMMAND ${CMAKE_COMMAND} -E copy_directory
            "${CMAKE_BINARY_DIR}/vendor/AiFramework"
            $<TARGET_FILE_DIR:AiFrameworkTestApp>)
endif ()