cmake_minimum_required(VERSION 3.15)
project(XMP-Toolkit-SDK)

include(GNUInstallDirs)
include(CMakePackageConfigHelpers)

add_subdirectory(XMPCore)
add_subdirectory(XMPFiles)

install(EXPORT XMP-Toolkit-SDK
        FILE xmp-toolkit-sdk-targets.cmake
        NAMESPACE XMP::
        DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/xmp-toolkit-sdk
)

configure_package_config_file(cmake/xmp-toolkit-sdk-config.cmake.in
        ${CMAKE_CURRENT_BINARY_DIR}/xmp-toolkit-sdk-config.cmake
        INSTALL_DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/xmp-toolkit-sdk
)

install(FILES ${CMAKE_CURRENT_BINARY_DIR}/xmp-toolkit-sdk-config.cmake
        DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/xmp-toolkit-sdk
)

install(DIRECTORY public/include/
        DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/xmp-toolkit-sdk
)