# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20.0)

find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(52prac3)
add_library(cjson STATIC mylib/cJSON.c)
target_sources(app PRIVATE src/main.c mylib/btscan52.c mylib/bt52.c)
target_include_directories(app PRIVATE include)
target_sources(app PRIVATE ${app_sources})

if(IBEACON_RSSI)
  zephyr_compile_definitions(IBEACON_RSSI=${IBEACON_RSSI})
endif()