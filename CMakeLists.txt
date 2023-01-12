cmake_minimum_required(VERSION 3.10)
project(tinyxml_vendor)

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_vendor_package REQUIRED)

list(INSERT CMAKE_MODULE_PATH 0 "${CMAKE_CURRENT_SOURCE_DIR}/cmake/Modules")
find_package(TinyXML QUIET)

ament_vendor(tinyxml_vendor
  SATISFIED ${TinyXML_FOUND}
  VCS_TYPE tar
  VCS_URL https://downloads.sourceforge.net/project/tinyxml/tinyxml/2.6.2/tinyxml_2_6_2.tar.gz
  VCS_VERSION tinyxml
  PATCHES patches
)

install(DIRECTORY cmake DESTINATION share/${PROJECT_NAME})

ament_package(
  CONFIG_EXTRAS "tinyxml_vendor-extras.cmake"
)
