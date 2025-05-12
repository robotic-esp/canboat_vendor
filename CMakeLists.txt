cmake_minimum_required(VERSION 3.8)
project(ros_canboat)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
include(ExternalProject)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

execute_process(
  COMMAND uname
  WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
  OUTPUT_VARIABLE OS_NAME
  OUTPUT_STRIP_TRAILING_WHITESPACE
)
string(TOLOWER "${OS_NAME}" OS_NAME_LOWER)

execute_process(
  COMMAND uname -m
  OUTPUT_VARIABLE ARCH
  OUTPUT_STRIP_TRAILING_WHITESPACE
)
set(BUILD_DIR "rel/${OS_NAME_LOWER}-${ARCH}")
message(STATUS "Canboat building into: ${BUILD_DIR}")

ExternalProject_Add(canboat
  GIT_REPOSITORY https://github.com/canboat/canboat.git
  GIT_TAG master
  CONFIGURE_COMMAND ""
  BUILD_COMMAND make
  INSTALL_COMMAND ""
  BUILD_IN_SOURCE 1
)

file(GLOB CANBOAT_BINARIES
  "${CMAKE_CURRENT_SOURCE_DIR}/external/canboat/${BUILD_DIR}/*"
)

install(PROGRAMS
  ${CANBOAT_BINARIES}
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
