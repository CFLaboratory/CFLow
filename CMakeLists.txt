### CMakeLists.txt
#
## Description
#
# Primary file for CFLow build system
#
## License
#
# SPDX-License-Identifier: Apache-2.0

## Basic configuration
cmake_minimum_required(VERSION 3.0)
project(CFLab
  LANGUAGES CXX
  VERSION 0.0)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

include(GNUInstallDirs)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/${CMAKE_INSTALL_BINDIR})

## Documentation
add_custom_target(doc
  doxygen
  COMMAND make -C man/latex
  WORKING_DIRECTORY ${CMAKE_SOURCE_DIR})
