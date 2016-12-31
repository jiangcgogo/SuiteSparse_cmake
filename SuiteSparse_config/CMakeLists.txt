cmake_minimum_required(VERSION 2.8)
project(SuiteSparse_config)

set(LIBRARY_NAME SuiteSparse_config)
add_library(${LIBRARY_NAME} SuiteSparse_config.c)
target_link_libraries(${LIBRARY_NAME})

install(FILES SuiteSparse_config.h
  DESTINATION include/suitesparse)

install(TARGETS ${LIBRARY_NAME}
  EXPORT ${PROJECT_NAME}Targets
  RUNTIME DESTINATION bin
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib)
