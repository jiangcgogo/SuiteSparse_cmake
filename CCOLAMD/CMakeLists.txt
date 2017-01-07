cmake_minimum_required(VERSION 2.8)
project(SuiteSparse_CCOLAMD)

include_directories(Include)
include_directories(../SuiteSparse_config)

add_definitions(-Wno-unused-parameter)

file(GLOB CCOLAMD_SRCS "Source/*.c")

set(LIBRARY_NAME "ccolamd")

add_library(${LIBRARY_NAME} ${SuiteSparse_BUILD_SHARED} ${CCOLAMD_SRCS})
target_link_libraries(${LIBRARY_NAME} m)

install(DIRECTORY Include/
  DESTINATION include/suitesparse/CCOLAMD
  FILES_MATCHING PATTERN "*.h")

install(TARGETS ${LIBRARY_NAME}
  EXPORT ${PROJECT_NAME}Targets
  RUNTIME DESTINATION bin
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib)
