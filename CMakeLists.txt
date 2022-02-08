cmake_minimum_required(VERSION 3.20)

project(game1)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_BINARY_DIR})

include(${CMAKE_CURRENT_BINARY_DIR}/conanbuildinfo.cmake)

set(CONAN_CMAKE_SILENT_OUTPUT ON)

conan_basic_setup()

file(GLOB_RECURSE src ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp)
file(GLOB_RECURSE headers ${CMAKE_CURRENT_SOURCE_DIR}/src/*.hpp)

add_executable(game1 ${src} ${headers})

target_include_directories(game1 PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/src)

target_compile_features(game1 PUBLIC cxx_std_20)

find_package(alya QUIET REQUIRED)

target_link_libraries(game1 PRIVATE alya::alya)
