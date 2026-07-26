cmake_minimum_required(VERSION 3.14)

project(SGP4
    VERSION 1.0.0
    DESCRIPTION "SGP4 satellite orbit propagation library"
    LANGUAGES CXX)

include(GNUInstallDirs)
include(CMakePackageConfigHelpers)

if(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    set(CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}/install" CACHE PATH "Install prefix" FORCE)
endif()

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

option(BUILD_EXAMPLES "Build example programs (sattrack, runtest, passpredict)" ON)
option(BUILD_TESTS "Build unit tests" ON)

include(FetchContent)
FetchContent_Declare(
    googletest
    GIT_REPOSITORY https://github.com/google/googletest.git
    GIT_TAG v1.14.0)
FetchContent_MakeAvailable(googletest)

enable_testing()
include(GoogleTest)

configure_file(
    "${CMAKE_CURRENT_SOURCE_DIR}/SGP4-VER.TLE"
    "${CMAKE_CURRENT_BINARY_DIR}/SGP4-VER.TLE"
    COPYONLY)

add_subdirectory(libsgp4)

if(BUILD_EXAMPLES)
    add_subdirectory(sattrack)
    add_subdirectory(runtest)
    add_subdirectory(passpredict)
    add_subdirectory(csvprop)
endif()

if(BUILD_TESTS)
    add_subdirectory(tests)
endif()
