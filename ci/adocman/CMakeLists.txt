cmake_minimum_required(VERSION 3.14)

project(test-adocman
  LANGUAGES C
)

include(GNUInstallDirs)
include(AdocMan)
add_adoc_man("${CMAKE_CURRENT_SOURCE_DIR}/testadoc.1.adoc")
