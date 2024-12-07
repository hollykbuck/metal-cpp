cmake_minimum_required(VERSION 3.26)

project(metal-cpp VERSION 1.0.0)

include(GNUInstallDirs)

# if not debug, install header
if(NOT CMAKE_BUILD_TYPE MATCHES Debug)
    install(DIRECTORY include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
endif()

include(CMakePackageConfigHelpers)

configure_package_config_file(
    "${CMAKE_CURRENT_SOURCE_DIR}/metal-cpp-config.cmake.in"
    "${CMAKE_CURRENT_BINARY_DIR}/metal-cpp-config.cmake"
    INSTALL_DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/metal-cpp
)

write_basic_package_version_file(
    "${CMAKE_CURRENT_BINARY_DIR}/metal-cpp-config-version.cmake"
    VERSION ${PROJECT_VERSION}
    COMPATIBILITY SameMajorVersion
)

install(
    FILES
        ${CMAKE_CURRENT_BINARY_DIR}/metal-cpp-config.cmake
        ${CMAKE_CURRENT_BINARY_DIR}/metal-cpp-config-version.cmake
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/metal-cpp
)