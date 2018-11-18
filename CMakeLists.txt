set(SOURCES src/nfd_common.c)

# add specific implementations
if (WIN32)
    list(APPEND SOURCES src/nfd_win.cpp)
elseif (APPLE)
    list(APPEND SOURCES src/nfd_cocoa.m)
elseif (UNIX)
    list(APPEND SOURCES src/nfd_gtk.c)
elseif (UNIX)
    message(FATAL_ERROR "Cannot detect your system, please report to https://github.com/aarcangeli/nativefiledialog-cmake/issues")
endif ()

add_library(nativefiledialog ${SOURCES})

target_include_directories(nativefiledialog PUBLIC src/include)
