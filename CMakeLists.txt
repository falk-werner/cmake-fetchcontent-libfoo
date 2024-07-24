cmake_minimum_required(VERSION 3.20)
project(libfoo)

include(GNUInstallDirs)

add_library(foo STATIC src/foo.c)
target_include_directories(foo PUBLIC inc/foo)

set_target_properties(foo PROPERTIES PUBLIC_HEADER inc/foo/foo.h)

configure_file(foo.pc.in foo.pc @ONLY) 
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/foo.pc
    DESTINATION "${CMAKE_INSTALL_LIBDIR}/pkgconfig")

install(TARGETS foo
    PUBLIC_HEADER DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/foo")

