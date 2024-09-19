cmake_minimum_required(VERSION 3.22)
project(WiringPi 
  VERSION 3.10.1 
  LANGUAGES C
  HOMEPAGE_URL "https://github.com/WiringPi/WiringPi"
  DESCRIPTION "The wiringPi libraries, headers and gpio command Libraries to allow GPIO access on a Raspberry Pi from C and C++ programs as well as from the command-line"
)

include(GNUInstallDirs)
include(CMakePackageConfigHelpers)

set(BUILD_SHARED_LIBS ON) # wiringPi/noMoreStatic
set(CMAKE_DEBUG_POSTFIX "_d")

add_subdirectory(wiringPi)

install(TARGETS wiringPi
    EXPORT wiringPiTargets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    INCLUDES DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

install(EXPORT wiringPiTargets
    FILE wiringPiTargets.cmake
    NAMESPACE wiringPi::
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/wiringPi
)

configure_package_config_file(${CMAKE_CURRENT_SOURCE_DIR}/cmake/Config.cmake.in
  "${CMAKE_CURRENT_BINARY_DIR}/wiringPiConfig.cmake"
  INSTALL_DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/wiringPi
)

write_basic_package_version_file(
  "${CMAKE_CURRENT_BINARY_DIR}/wiringPiConfigVersion.cmake"
  VERSION "${version}"
  COMPATIBILITY AnyNewerVersion
)

install(FILES
          "${CMAKE_CURRENT_BINARY_DIR}/wiringPiConfig.cmake"
          "${CMAKE_CURRENT_BINARY_DIR}/wiringPiConfigVersion.cmake"
        DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/wiringPi
)
set(CPACK_PACKAGE_CONTACT "Grazer Computer Club - GC2 <wiringpi@gc2.at>")
include(CPack)
