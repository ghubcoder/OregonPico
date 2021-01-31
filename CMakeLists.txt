cmake_minimum_required(VERSION 3.12)
include(pico_sdk_import.cmake)
project(test_project)
pico_sdk_init()


add_library(Sensor Sensor.cpp)

add_library(RCSwitch RCSwitch.cpp)
target_link_libraries(RCSwitch pico_stdlib)

add_library(RcOok RcOok.cpp)
target_link_libraries(RcOok pico_stdlib)

add_executable(
  test
  test.cpp
)

pico_enable_stdio_uart(test 1)
pico_add_extra_outputs(test)
target_link_libraries(test Sensor RCSwitch RcOok pico_stdlib)
