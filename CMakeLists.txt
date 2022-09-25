cmake_minimum_required(VERSION 3.9)
project(readerwriterqueue VERSION 1.0.0)

option (READERWRITERQUEUE_DISABLE_INSTALL "disables installation of readerwriterqueue headers" OFF)

include(GNUInstallDirs)

add_library(${PROJECT_NAME} INTERFACE)
add_library(readerwriterqueue::readerwriterqueue ALIAS readerwriterqueue)

target_include_directories(readerwriterqueue INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})

if (READERWRITERQUEUE_DISABLE_INSTALL)
else()
    install(FILES atomicops.h readerwriterqueue.h readerwritercircularbuffer.h LICENSE.md
            DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME})
endif()
