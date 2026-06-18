cmake_minimum_required(VERSION 4.3.0)

set(CMAKE_EXPERIMENTAL_CXX_IMPORT_STD "451f2fe2-a8a2-47c3-bc32-94786d8fc91b")

project(XayahUtil VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_EXPERIMENTAL_CXX_MODULE_CMAKE_API ON)
set(CMAKE_CXX_SCAN_FOR_MODULES ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

if (MSVC)
    add_compile_options($<$<COMPILE_LANGUAGE:CXX>:/Zc:preprocessor>)
endif ()

add_library(xayah-util-xcli)
target_sources(
        xayah-util-xcli
        PRIVATE
        xcli.cpp
        PUBLIC
        FILE_SET cxx_modules TYPE CXX_MODULES FILES
        xcli.ixx
)
set_property(TARGET xayah-util-xcli PROPERTY CXX_MODULE_STD ON)
