cmake_minimum_required(VERSION 3.27)
project(modtest)

# setup modules support

set(CMAKE_EXPERIMENTAL_CXX_MODULE_CMAKE_API "aa1f7df0-828a-4fcd-9afc-2dc80491aca7")
set(CMAKE_EXPERIMENTAL_CXX_MODULE_DYNDEP 1)
# Default to C++ extensions being off. Clang's modules support have trouble
# with extensions right now.
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_CXX_STANDARD 20)

add_link_options(-fuse-ld=lld -stdlib=libc++)
add_compile_options(-stdlib=libc++)

add_subdirectory(lib)

add_executable(modtest main.cpp)
target_link_libraries(modtest PRIVATE a)
