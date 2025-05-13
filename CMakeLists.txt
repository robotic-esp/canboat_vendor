cmake_minimum_required(VERSION 3.8)
project(canboat_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
include(ExternalProject)
include(GNUInstallDirs)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

set(CANBOAT_SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR}/canboat)

ExternalProject_Add(canboat
  SOURCE_DIR ${CANBOAT_SRC_DIR}
  CONFIGURE_COMMAND ""
  INSTALL_DIR ${CMAKE_INSTALL_PREFIX} 
  BUILD_COMMAND BUILDDIR=rel ${CMAKE_MAKE_PROGRAM} -C <SOURCE_DIR>
  INSTALL_COMMAND
    ${CMAKE_COMMAND} -E copy_directory
      <SOURCE_DIR>/rel
      <INSTALL_DIR>/lib/${PROJECT_NAME}
  UPDATE_COMMAND ""
)

ament_package()
