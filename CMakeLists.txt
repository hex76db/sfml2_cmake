cmake_minimum_required(VERSION 2.7)

project(mazing)

set(SFML_ROOT "${PROJECT_SOURCE_DIR}/SFML2")
set(CMAKE_MODULE_PATH "${SFML_ROOT}/cmake/Modules" ${CMAKE_MODULE_PATH})

find_package(SFML 2 REQUIRED system window graphics network audio)

include_directories(${SFML_INCLUDE_DIR})

add_executable(mazing Main.cpp)
target_link_libraries(mazing ${SFML_LIBRARIES})

add_custom_command(TARGET mazing POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
        "${SFML_ROOT}/bin"
        $<TARGET_FILE_DIR:mazing>)