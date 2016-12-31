cmake_minimum_required(VERSION 2.8)
project(SuiteSparse_CAMD)

include_directories(Include)
include_directories(../SuiteSparse_config)

add_definitions(-Wno-unused-parameter)

file(GLOB CAMD_SRCS "Source/*.c")

set(LIBRARY_NAME "camd")

add_library(${LIBRARY_NAME} ${CAMD_SRCS})
target_link_libraries(${LIBRARY_NAME} m)

install(DIRECTORY Include/
  DESTINATION include/suitesparse/CAMD
  FILES_MATCHING PATTERN "*.h")

install(TARGETS ${LIBRARY_NAME}
  EXPORT ${PROJECT_NAME}Targets
  RUNTIME DESTINATION bin
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib)
