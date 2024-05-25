# add_cpp
a small C++ project to show CMake

# CMake Tutorial
- creates project files or Makefiles
- thus an indirect build system

## create a library
- have a library with:
  - `add.h`
  - `add.cpp`
- set variables: `LIBADD_HEADERS` and `LIBADD_SOURCES`
- add library:
  `add_library` - specify target name + mark as shared lirbary (`*.so`)
- set target sources:
  `target_sources` - add sorces files via defined variables
## specify installation of library
- four things need to be done for installation if an library
  - build `*.so` file need to be copied in library path (`/usr/lib`)
  - header files `*.h` need to be copied in include directory (`/usr/include`)
  - pkg-config files `*.pc` need to be created and copied to pkgconfig directory (`/usr/share/pkgconfig`)
    - TODO
  - CMake files `*.cmake` need to be copied in cmake directory (`/usr/share/cmake`)
    - implemented
### 1. Build shared library
- `add_library (add_cpp SHARED)` - defines that lib `add_cpp` will build as a shared lib,
  - that means that other libs can dynically load it (dynamic linked)
- `target_include_directories(add_cpp ...)` - defines headers search path
- `target_sources(add_cpp ...)` - defines the sources (predefined within variables)
### 2+3+4. Install Part
- install header files (`*.h`) in systems include-path
  - `install(FILES ${LIBADD_HEADERS} DESTINATION include/libadd_cpp)`
  -  headerfiles are set with variable `LIBADD_HEADERS`
  - here `include/libadd_cpp` is used as destination
    - TODO: use `CMAKE_INSTALL_INCLUDEDIR`
- install shared library:
  - `install(TARGETS add_cpp ... LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} ...)`
  - `EXPORT add_cppConfig` in `install(...)` section is used to create later `*.cmake` files

