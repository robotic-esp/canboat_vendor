cmake_minimum_required(VERSION 3.8)
project(canboat_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
include(ExternalProject)

ExternalProject_Add(canboat
  GIT_REPOSITORY git@github.com:canboat/canboat.git
  GIT_TAG v5.1.3
  PREFIX ${CMAKE_BINARY_DIR}/external/
  SOURCE_DIR ${CMAKE_BINARY_DIR}/external/canboat/
  INSTALL_DIR ${CMAKE_INSTALL_PREFIX}
  CONFIGURE_COMMAND ""
  BUILD_COMMAND BUILDDIR=rel ${CMAKE_MAKE_PROGRAM} -C <SOURCE_DIR>
  INSTALL_COMMAND
    ${CMAKE_COMMAND} -E copy_directory
      <SOURCE_DIR>/rel
      <INSTALL_DIR>/lib/${PROJECT_NAME}
  UPDATE_COMMAND ""
)

ament_package()
