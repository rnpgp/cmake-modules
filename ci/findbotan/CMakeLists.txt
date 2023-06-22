cmake_minimum_required(VERSION 3.14)

project(test-findbotan
  LANGUAGES C
)

include(FindBotan)
find_package(Botan 2.0 REQUIRED)

file(WRITE findbotan.txt "BOTAN_LIBRARY: ${BOTAN_LIBRARY}\n")
file(APPEND findbotan.txt "BOTAN_INCLUDE_DIR: ${BOTAN_INCLUDE_DIR}\n")

if(NOT DEFINED BOTAN_LIBRARY OR "${BOTAN_LIBRARY}" STREQUAL "")
  message(FATAL_ERROR "BOTAN_LIBRARY is not set.")
endif()

if(NOT DEFINED BOTAN_INCLUDE_DIR OR "${BOTAN_INCLUDE_DIR}" STREQUAL "")
  message(FATAL_ERROR "BOTAN_INCLUDE_DIR is not set.")
endif()
