cmake_minimum_required(VERSION 3.13.4)
set (CMAKE_CXX_STANDARD 17)
if(CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR)
project(sreelang)
find_package(LLVM REQUIRED HINTS "${LLVM_CMAKE_PATH}")
list(APPEND CMAKE_MODULE_PATH ${LLVM_DIR})
include(AddLLVM)
include(HandleLLVMOptions)
include_directories("${LLVM_BINARY_DIR}/include" "${LLVM_INCLUDE_DIR}")
link_directories("${LLVM_LIBRARY_DIR}")
llvm_map_components_to_libnames(llvm_libs Core)
set(SREELANG_BUILT_STANDALONE 1)
endif()

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules")
if(CMAKE_SOURCE_DIR STREQUAL CMAKE_BINARY_DIR)
message(FATAL_ERROR "In-source builds are not allowed. Create a build directory and build from there.")
endif()

set(SREELANG_VERSION_STRING "0.1")
configure_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/include/sreelang/Basic/Version.inc.in 
    ${CMAKE_CURRENT_BINARY_DIR}/include/sreelang/Basic/Version.inc
)

include(AddSreelang)
include_directories(
    BEFORE
    ${CMAKE_CURRENT_BINARY_DIR}/include
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)
add_subdirectory(lib)
add_subdirectory(tools)
