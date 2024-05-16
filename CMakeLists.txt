cmake_minimum_required (VERSION 2.8.11)
project (libadd_cpp)

include(GNUInstallDirs)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

# set header files
set(headers include/add.h)

# set source files
set(sources src/add.cpp)

add_library (add_cpp SHARED)
target_sources(add_cpp
 PRIVATE
  ${sources}
  ${headers}
)

# install part (optional)
install(FILES ${headers} DESTINATION include/libadd_cpp)

install(TARGETS
        add_cpp
    EXPORT add_cppConfig
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
export(TARGETS
        add_cpp
    NAMESPACE add_cpp::
    FILE "${CMAKE_CURRENT_BINARY_DIR}/add_cppConfig.cmake"
)

install(EXPORT
        add_cppConfig
    DESTINATION "${CMAKE_INSTALL_DATADIR}/cmake/add_cpp"
    NAMESPACE add_cpp::
)
