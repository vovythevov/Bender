#============================================================================
#
# Program: Bender
#
# Copyright (c) Kitware Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0.txt
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
#============================================================================

cmake_minimum_required(VERSION 2.6)

set(KIT Cleaver)
project(Bender${KIT})
string(TOUPPER ${KIT} KIT_UPPER)

#-----------------------------------------------------------------------------
# Get ITK
find_package(ITK REQUIRED)
include(${ITK_USE_FILE})

#-----------------------------------------------------------------------------
# Get Cleaver
find_package(Cleaver REQUIRED)
include(${Cleaver_USE_FILE})

#-----------------------------------------------------------------------------
include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}
  ${CMAKE_CURRENT_BINARY_DIR}
  ${Cleaver_INCLUDE_DIRS}
  )

set_property(GLOBAL APPEND PROPERTY Bender_INCLUDE_DIRS
  ${CMAKE_CURRENT_SOURCE_DIR}
  ${CMAKE_CURRENT_BINARY_DIR}
  )

#-----------------------------------------------------------------------------
# Add testing
if (BUILD_TESTING)
  add_subdirectory(Testing)
endif()
