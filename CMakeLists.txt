cmake_minimum_required(VERSION 3.30)
project(LTest VERSION 1.0.0)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT ${PROJECT_NAME})
set_property(GLOBAL PROPERTY USE_FOLDERS ON)
set(CMAKE_SUPPRESS_REGENERATION TRUE)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_FLAGS /experimental:module)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)

set (SOURCES src/main.cpp)

source_group("Source files/Source" FILES "scr/main.cpp")
source_group("Header files/Header" FILES)

add_executable(${PROJECT_NAME} ${SOURCES})

if (MSVC)
	target_compile_options(${PROJECT_NAME} PRIVATE /FAc)
endif()
