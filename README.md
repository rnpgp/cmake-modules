CMake modules
=============

This repository contains useful cmake modules.

PandocMan.cmake
---------------

This module can be used to generate and install man pages in **troff** format from the Markdown, using the **Pandoc**.

Just add files named like `utility.1.md` with manual page contents, and add line `add_pandoc_man("${CMAKE_CURRENT_SOURCE_DIR}/utility.1.md")` to the corresponding `CMakeLists.txt` to have your markdown rendered to **troff** and installed via `make install`.

AdocMan.cmake
-------------

This module can be used to generate and install man pages in **troff** format from the AsciiDoc, using the **AsciiDoctor**.

Just add files named like `utility.1.adoc` with manual page contents, and add line `add_adoc_man("${CMAKE_CURRENT_SOURCE_DIR}/utility.1.adoc")` to the corresponding `CMakeLists.txt` to have your AsciiDoc rendered to **troff** and installed via `make install`.

FindOpenSSLFeatures.cmake
-------------------------

This module can be used to list available OpenSSL features, without dependency on openssl binary. Instead of running openssl binary it compiles small utility (see `findopensslfeatures.c`) and runs it to retrieve all needed lists.
Following features are supported: hashes, symmetric ciphers, elliptic curves and publickey engines.
