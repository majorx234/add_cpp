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
