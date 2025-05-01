cmake_minimum_required(VERSION 3.31)

project(imgui-test
  VERSION 1.0
  LANGUAGES CXX
)

set(LINK_DEPS_STATIC TRUE)

add_subdirectory(ui)

set(CMAKE_CXX_STANDARD 20)
