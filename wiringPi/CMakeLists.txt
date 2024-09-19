add_library(wiringPi)
add_library(wiringPi::wiringPi ALIAS wiringPi)

set_property(TARGET wiringPi PROPERTY VERSION ${PROJECT_VERSION})
set_property(TARGET wiringPi PROPERTY SOVERSION ${PROJECT_VERSION_MAJOR})
set_property(TARGET wiringPi PROPERTY INTERFACE_wiringPi_MAJOR_VERSION ${PROJECT_VERSION_MAJOR})
set_property(TARGET wiringPi APPEND PROPERTY COMPATIBLE_INTERFACE_STRING wiringPi_MAJOR_VERSION)

configure_file(version.in.h version.h @ONLY)

target_include_directories(wiringPi PUBLIC 
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}>"
    "$<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>"
)
target_sources(wiringPi PRIVATE 
    ads1115.c
    ads1115.h
    bmp180.c
    bmp180.h
    drcNet.c
    drcNet.h
    drcSerial.c
    drcSerial.h
    ds18b20.c
    ds18b20.h
    htu21d.c
    htu21d.h
    max5322.c
    max5322.h
    max31855.c
    max31855.h
    mcp23s08.c
    mcp23s08.h
    mcp23s17.c
    mcp23s17.h
    mcp23x08.h
    mcp23x0817.h
    mcp3002.c
    mcp3002.h
    mcp3004.c
    mcp3004.h
    mcp3422.c
    mcp3422.h
    mcp4802.c
    mcp4802.h
    mcp23008.c
    mcp23008.h
    mcp23016.c
    mcp23016.h
    mcp23016reg.h
    mcp23017.c
    mcp23017.h
    pcf8574.c
    pcf8574.h
    pcf8591.c
    pcf8591.h
    piHiPri.c
    piThread.c
    pseudoPins.c
    pseudoPins.h
    rht03.c
    rht03.h
    sn3218.c
    sn3218.h
    softPwm.c
    softPwm.h
    softServo.c
    softServo.h
    softTone.c
    softTone.h
    sr595.c
    sr595.h
    wiringPi.c
    wiringPi.h
    wiringPiI2C.c
    wiringPiI2C.h
    wiringPiLegacy.c
    wiringPiLegacy.h
    wiringPiSPI.c
    wiringPiSPI.h
    wiringSerial.c
    wiringSerial.h
    wiringShift.c
    wiringShift.h
    wpiExtensions.c
    wpiExtensions.h
)
install(FILES 
    wiringPi.h
    wiringSerial.h
    ${CMAKE_CURRENT_BINARY_DIR}/version.h
DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/wiringPi
)

