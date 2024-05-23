cmake_minimum_required (VERSION 3.6)
project (libadd_cpp
  DESCRIPTION "a library example to learn CMake"
  VERSION 0.1.0
  LANGUAGES CXX)

include(GNUInstallDirs)

# set header files
set(LIBADD_HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/include/add.h)

# set source files
set(LIBADD_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/src/add.cpp)

add_library (add_cpp SHARED)
target_include_directories(add_cpp PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_sources(add_cpp
 PRIVATE
  ${LIBADD_SOURCES}
  ${LIBADD_HEADERS}
)

# install part (optional)
install(FILES ${LIBADD_HEADERS} DESTINATION include/libadd_cpp)

install(TARGETS
    add_cpp
    EXPORT add_cppConfig
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

# create cmake script to find libadd_cpp in other projects
export(TARGETS
        add_cpp
    NAMESPACE add_cpp::
    FILE "${CMAKE_CURRENT_BINARY_DIR}/add_cppConfig.cmake"
)

# install created cmake script in system's cmake folder
install(EXPORT
        add_cppConfig
    DESTINATION "${CMAKE_INSTALL_DATADIR}/cmake/add_cpp"
    NAMESPACE add_cpp::
)
