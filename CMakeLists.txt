########################################################
# Top-level CMakeLists.txt to build BME280-Driver Libraries
# @author LAGARDE Francois
cmake_minimum_required(VERSION 3.1 FATAL_ERROR)
########################################################

# ----- Project name and version -----
project(BME280-Driver)
set( ${PROJECT_NAME}_VERSION_MAJOR 3 )
set( ${PROJECT_NAME}_VERSION_MINOR 3 )
set( ${PROJECT_NAME}_VERSION_PATCH 4 )

# set the C++ standard to C++ 11
set(CMAKE_CXX_STANDARD 11)

##BME280-Driver Sources
set(BME280-Driver ${PROJECT_SOURCE_DIR}/bme280.c )
file(GLOB BME280_DRIVER_PUBLIC_HEADERS ${PROJECT_SOURCE_DIR}/*.h)
include_directories(${PROJECT_SOURCE_DIR})

add_library(bme280 STATIC ${BME280-Driver})

# install configuration
install(FILES ${BME280_DRIVER_PUBLIC_HEADERS} DESTINATION include/bme280)
install(TARGETS bme280 ARCHIVE DESTINATION lib RUNTIME DESTINATION bin LIBRARY DESTINATION lib)
