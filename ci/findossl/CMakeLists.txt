cmake_minimum_required(VERSION 3.14)

project(test-findopenssl
  LANGUAGES C
)

find_package(OpenSSL 1.1.1 REQUIRED)
include(FindOpenSSLFeatures)

foreach(feature "HASHES" "CIPHERS" "CURVES" "PUBLICKEY" "FEATURES")
  list(LENGTH "OPENSSL_SUPPORTED_${feature}" _feature_len)
  if(_feature_len LESS 5)
    message(FATAL_ERROR "OPENSSL_SUPPORTED_${feature} contains too few elements")
  endif()
endforeach()

list(LENGTH "OPENSSL_SUPPORTED_PROVIDERS" _providers_len)
if(_providers_len LESS 1)
  message(FATAL_ERROR "OPENSSL_SUPPORTED_PROVIDERS contains too few elements")
endif()

foreach(feature "AES-128-ECB" "AES-256-ECB" "rsaEncryption" "dsaEncryption" "Ed25519" "X25519" "default")
  OpenSSLHasFeature("${feature}" _openssl_has_${feature})
  if (NOT _openssl_has_${feature})
    message(FATAL_ERROR "OpenSSL feature is missing: ${feature}")
  endif()
endforeach()
