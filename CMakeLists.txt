
cmake_minimum_required(VERSION 2.8.12)

project(OxygenFont)

find_package(ECM 0.0.11 REQUIRED NO_MODULE)

set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR})

include(KDEInstallDirs)
include(ECMPackageConfigHelpers)
include(ECMSetupVersion)
include(FeatureSummary)


# create a Config.cmake and a ConfigVersion.cmake file and install them
set(CMAKECONFIG_INSTALL_DIR "${CMAKECONFIG_INSTALL_PREFIX}/OxygenFont")

include(ECMPackageConfigHelpers)


ecm_setup_version(0.4 VARIABLE_PREFIX OXYGENFONT
                  PACKAGE_VERSION_FILE "${CMAKE_CURRENT_BINARY_DIR}/OxygenFontConfigVersion.cmake"
)

ecm_configure_package_config_file("${CMAKE_CURRENT_SOURCE_DIR}/OxygenFontConfig.cmake.in"
                                  "${CMAKE_CURRENT_BINARY_DIR}/OxygenFontConfig.cmake"
                                  INSTALL_DESTINATION  ${CMAKECONFIG_INSTALL_DIR}
)

install(FILES
        "${CMAKE_CURRENT_BINARY_DIR}/OxygenFontConfig.cmake"
        "${CMAKE_CURRENT_BINARY_DIR}/OxygenFontConfigVersion.cmake"
        DESTINATION "${CMAKECONFIG_INSTALL_DIR}"
        COMPONENT Devel)

feature_summary(WHAT ALL FATAL_ON_MISSING_REQUIRED_PACKAGES)

if(NOT DEFINED OXYGEN_FONT_INSTALL_DIR)
  set(OXYGEN_FONT_INSTALL_DIR  ${CMAKE_INSTALL_PREFIX}/${SHARE_INSTALL_PREFIX}/fonts/oxygen)
endif()

set(fontFiles
    oxygen-fonts/mono-400/OxygenMono-Regular.ttf
    oxygen-fonts/Bold-700/Oxygen-Sans-Bold.ttf
    oxygen-fonts/Regular-400/Oxygen-Sans.ttf
)

install(FILES ${fontFiles} DESTINATION ${OXYGEN_FONT_INSTALL_DIR})
