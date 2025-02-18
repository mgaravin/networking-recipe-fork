# CMake build file for Stratum code.
#
# Copyright 2022-2023 Intel Corporation
# SPDX-License-Identifier: Apache 2.0
#

# Version 3.15 is the baseline for P4 Control Plane.
cmake_minimum_required(VERSION 3.15)

#############################
# Symbolic path definitions #
#############################

set(GOOGLEAPIS_SOURCE_DIR
    "${CMAKE_CURRENT_SOURCE_DIR}/googleapis" CACHE PATH
    "Path to Google APIs source directory")
mark_as_advanced(GOOGLEAPIS_SOURCE_DIR)

set(P4RUNTIME_SOURCE_DIR
    "${CMAKE_CURRENT_SOURCE_DIR}/p4runtime" CACHE PATH
    "Path to P4Runtime source directory")
mark_as_advanced(P4RUNTIME_SOURCE_DIR)

set(STRATUM_SOURCE_DIR
    "${CMAKE_CURRENT_SOURCE_DIR}/stratum" CACHE PATH
    "Path to Stratum source directory")
mark_as_advanced(STRATUM_SOURCE_DIR)

set(PB_OUT_DIR "${CMAKE_BINARY_DIR}/pb.out" CACHE PATH
    "Path to directory for generated Protobuf files")
mark_as_advanced(PB_OUT_DIR)
file(MAKE_DIRECTORY ${PB_OUT_DIR})

set(STRATUM_INCLUDES
    ${STRATUM_SOURCE_DIR}
    # Protobuf C++ header files.
    ${PB_OUT_DIR}
)

add_subdirectory(proto)
add_subdirectory(stratum)
