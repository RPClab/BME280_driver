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
set(CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR}/bin)
set(CMAKE_LIBRARY_PATH ${CMAKE_SOURCE_DIR}/bin/lib)


##BME280-Driver Sources
set(BME280-Driver ${PROJECT_SOURCE_DIR}/bme280.c )
include_directories(${PROJECT_SOURCE_DIR})

add_library(BME280 STATIC ${BME280-Driver})
configure_file(${PROJECT_SOURCE_DIR}/bme280.h ${CMAKE_SOURCE_DIR}/bin/include/bme280/bme280.h COPYONLY)
configure_file(${PROJECT_SOURCE_DIR}/bme280_defs.h ${CMAKE_SOURCE_DIR}/bin/include/bme280/bme280_defs.h COPYONLY)
## Install executable
install(TARGETS BME280 ARCHIVE DESTINATION ${PROJECT_SOURCE_DIR}/bin/lib LIBRARY DESTINATION ${PROJECT_SOURCE_DIR}/bin/lib)
