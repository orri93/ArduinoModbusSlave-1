cmake_minimum_required(VERSION 3.15.0)

project(ArduinoModbusSlave VERSION 1.0.0.0
  DESCRIPTION "Arduino Modbus Slave"
  LANGUAGES CXX)

set(arduinomodbusslave_target libarduinomodbusslave)

list(APPEND arduinomodbusslave_include
  "${CMAKE_CURRENT_SOURCE_DIR}/src")
  
list(APPEND arduinomodbusslave_source 
  "${CMAKE_CURRENT_SOURCE_DIR}/src/ModbusSlave.cpp")
list(APPEND arduinomodbusslave_public_header
  "${CMAKE_CURRENT_SOURCE_DIR}/src/ModbusSlave.h")

add_library(${arduinomodbusslave_target} ${arduinomodbusslave_source})

target_compile_definitions(${arduinomodbusslave_target} PUBLIC ARDUINO_ARCH_AVR)

target_include_directories(${arduinomodbusslave_target} PUBLIC
  ${arduinomodbusslave_include})

set_target_properties(${arduinomodbusslave_target}
  PROPERTIES PUBLIC_HEADER
  "${arduinomodbusslave_public_header}")

install(TARGETS ${arduinomodbusslave_target}
  LIBRARY DESTINATION lib
  PUBLIC_HEADER DESTINATION include/Arduino
  ARCHIVE DESTINATION lib)