# SPDX-License-Identifier: Apache-2.0

set(BOARD nrf52840dongle_nrf52840)
set(CONF_FILE prj.conf usb.conf bt.conf console.conf)
set(DTC_OVERLAY_FILE dtc_console.overlay)

cmake_minimum_required(VERSION 3.20.0)
find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(BASE_NODE)

#Add Include Directories
include_directories(inc/
                    ../lib/inc)

#Add Target Sources
target_sources(app PRIVATE  src/main.c
                            src/ble_base.c
                            ../lib/src/led_driver.c)

zephyr_library_include_directories(${ZEPHYR_BASE}/samples/bluetooth)