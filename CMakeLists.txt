
# Copyright 2025 NXP
#
# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.22.0)

include(
    ${SdkRootDirPath}/cmake/extension/mcux.cmake
)

project(
    wifi_cli
    PROJECT_BOARD_PORT_PATH ${board_root}/${board}/wifi_examples/wifi_cli
    LANGUAGES C CXX ASM
)

include(
    ${SdkRootDirPath}/CMakeLists.txt
)

mcux_add_source(
    BASE_PATH ${CMAKE_CURRENT_LIST_DIR}
    SOURCES main.c
)

mcux_add_include(
    BASE_PATH ${CMAKE_CURRENT_LIST_DIR}
    INCLUDES .
)
mcux_add_iar_configuration(
	CC "--dlib_config full\
		--no_inline"
	CX "--no_clustering"
	LD "--semihosting"
)

include(
    ${SdkRootDirPath}/${board_root}/${board}/wifi_examples/wifi_cli/reconfig.cmake OPTIONAL
)
mcux_convert_binary(BINARY ${APPLICATION_BINARY_DIR}/${MCUX_SDK_PROJECT_NAME}.bin)