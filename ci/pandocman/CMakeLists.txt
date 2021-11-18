cmake_minimum_required(VERSION 3.14)

project(test-pandocman
  LANGUAGES C
)

include(GNUInstallDirs)
include(PandocMan)
add_pandoc_man("${CMAKE_CURRENT_SOURCE_DIR}/testpandoc.1.md")
