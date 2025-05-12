cmake_minimum_required(VERSION 3.23)

# Project name and version
project(cpp-mem)

include(ExternalProject)
message("CMakeLists.txt for cpp-mem")
message("PROJECT_SOURCE_DIR: ${PROJECT_SOURCE_DIR}")
message("CMAKE_BINARY_DIR: ${CMAKE_BINARY_DIR}")

set(PACKAGE_NAME trm-mem)

# Add subdirectories for source and include files
# Add source files
set(SOURCES
    src/memsys.cc
)

# Add stubs for undefined functions
list(APPEND SOURCES src/stubs.cc)

add_library(${PACKAGE_NAME} SHARED 
    ${SOURCES}
)

target_include_directories(${PACKAGE_NAME}
    PUBLIC
        $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
)


############################################################
# Create an executable
############################################################

# No executable in this code, this is a library

############################################################
# Install
############################################################
include("${CMAKE_COMMON}/install_lib.cmake") # Get the generic install function

install_lib(${PACKAGE_NAME})