cmake_minimum_required (VERSION 2.8.11)
project (libadd_cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

# set header files
set(headers include/add.h)

# set source files
set(sources src/add.cpp)

add_library (add SHARED
  ${sources}
  ${headers}
)

install(TARGETS add DESTINATION lib/libadd_cpp)
install(FILES ${headers} DESTINATION include/libadd_cpp)
