cmake_minimum_required(VERSION 2.8)
project(SuiteSparse_AMD)

include_directories(Include)
include_directories(../SuiteSparse_config)

add_definitions(-Wno-unused-parameter)

file(GLOB AMD_SRCS "Source/*.c")

set(LIBRARY_NAME "amd")

add_library(${LIBRARY_NAME} ${AMD_SRCS})
target_link_libraries(${LIBRARY_NAME} m)

install(DIRECTORY Include/
  DESTINATION include/suitesparse/AMD
  FILES_MATCHING PATTERN "*.h")

install(TARGETS ${LIBRARY_NAME}
  EXPORT ${PROJECT_NAME}Targets
  RUNTIME DESTINATION bin
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib)
