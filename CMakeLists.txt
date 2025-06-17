cmake_minimum_required(VERSION 3.8)

project(canboat_vendor)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
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
  INSTALL_COMMAND ""
)
ExternalProject_Get_Property(canboat SOURCE_DIR)
install(
  PROGRAMS ${SOURCE_DIR}/rel/actisense-serial
           ${SOURCE_DIR}/rel/analyzer
           ${SOURCE_DIR}/rel/analyzer-explain
           ${SOURCE_DIR}/rel/analyzer-j1939
           ${SOURCE_DIR}/rel/analyzer-explain-j1939
           ${SOURCE_DIR}/rel/candump2analyzer
           ${SOURCE_DIR}/rel/command-group-function
           ${SOURCE_DIR}/rel/ikonvert-serial
           ${SOURCE_DIR}/rel/iptee
           ${SOURCE_DIR}/rel/n2kd
           ${SOURCE_DIR}/rel/n2kd_monitor
           ${SOURCE_DIR}/rel/nmea0183-serial
           ${SOURCE_DIR}/rel/request-group-function
           ${SOURCE_DIR}/rel/replay
           ${SOURCE_DIR}/rel/socketcan-writer
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
