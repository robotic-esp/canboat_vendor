cmake_minimum_required(VERSION 3.8)

project(canboat_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
include(ExternalProject)

include(ExternalProject)
ExternalProject_Add(
  canboat
  PREFIX ${CMAKE_BINARY_DIR}/external
  GIT_REPOSITORY https://github.com/canboat/canboat.git
  GIT_TAG v5.1.3
  UPDATE_COMMAND ""
  CONFIGURE_COMMAND ""
  BUILD_IN_SOURCE 1
  BUILD_COMMAND ${CMAKE_MAKE_PROGRAM} -C <SOURCE_DIR> BUILDDIR=rel
  INSTALL_COMMAND
    ${CMAKE_COMMAND} -E make_directory
    $ENV{DESTDIR}${CMAKE_INSTALL_PREFIX}/lib/${PROJECT_NAME} &&
    ${CMAKE_COMMAND} -E copy_directory <SOURCE_DIR>/rel
    $ENV{DESTDIR}${CMAKE_INSTALL_PREFIX}/lib/${PROJECT_NAME}
)

ament_package()
