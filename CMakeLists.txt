cmake_minimum_required(VERSION 2.8)
project(SuiteSparse)

set(SS_MAJOR_VERSION 4)
set(SS_MINOR_VERSION 5)
set(SS_PATCH_VERSION 4)
set(SS_VERSION ${SS_MAJOR_VERSION}.${SS_MINOR_VERSION}.${SS_PATCH_VERSION})

option(BUILD_SHARED "" ON)

if(BUILD_SHARED)
  set(SuiteSparse_BUILD_SHARED SHARED)
endif()

add_subdirectory("metis-5.1.0")
add_subdirectory("SuiteSparse_config")
add_subdirectory("AMD")
add_subdirectory("CAMD")
add_subdirectory("COLAMD")
add_subdirectory("CCOLAMD")
add_subdirectory("CHOLMOD")
