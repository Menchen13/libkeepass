cmake_minimum_required(VERSION 3.14)
project(libkeepass LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add all sources (adjust if you reorganize)
file(GLOB LIBKEEPASS_SOURCES src/*.cc)

add_library(keepass STATIC ${LIBKEEPASS_SOURCES})
target_include_directories(keepass PUBLIC include)

# Dependencies: zlib + OpenSSL
find_package(zlib REQUIRED)
find_package(OpenSSL REQUIRED)

target_link_libraries(keepass PRIVATE ZLIB::ZLIB OpenSSL::Crypto)

