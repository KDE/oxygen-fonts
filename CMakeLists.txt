project(OxygenFont)
set(PROJECT_VERSION "5.3.0")
cmake_minimum_required(VERSION 2.8.12)

find_package(ECM 1.2.0 REQUIRED NO_MODULE)

set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR})

include(KDEInstallDirs)
include(ECMPackageConfigHelpers)
include(ECMSetupVersion)
include(FeatureSummary)

# create a Config.cmake and a ConfigVersion.cmake file and install them
set(CMAKECONFIG_INSTALL_DIR "${CMAKECONFIG_INSTALL_PREFIX}/OxygenFont")

include(ECMPackageConfigHelpers)

ecm_setup_version(${PROJECT_VERSION} VARIABLE_PREFIX OXYGENFONT
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

if(NOT DEFINED OXYGEN_FONT_INSTALL_DIR)
  set(OXYGEN_FONT_INSTALL_DIR  ${CMAKE_INSTALL_PREFIX}/${SHARE_INSTALL_PREFIX}/fonts/truetype/oxygen)
endif()

find_program(FONTFORGE_EXECUTABLE NAMES fontforge)
if(FONTFORGE_EXECUTABLE)
    message(STATUS "FontForge found: ${FONTFORGE_EXECUTABLE}")
else()
    message(FATAL_ERROR "Could not find FontForge executable")
endif()

feature_summary(WHAT ALL FATAL_ON_MISSING_REQUIRED_PACKAGES)

add_custom_target(regular ALL fontforge ${CMAKE_CURRENT_SOURCE_DIR}/generate-ttf.pe
                   ${CMAKE_CURRENT_SOURCE_DIR}/oxygen-fonts/Regular-400/src/Oxygen-Sans.sfd
                   ${CMAKE_CURRENT_BINARY_DIR}/Oxygen-Sans.ttf
                  )
add_custom_target(bold ALL fontforge ${CMAKE_CURRENT_SOURCE_DIR}/generate-ttf.pe
                   ${CMAKE_CURRENT_SOURCE_DIR}/oxygen-fonts/Bold-700/src/Oxygen-Sans-Bold.sfd
                   ${CMAKE_CURRENT_BINARY_DIR}/Oxygen-Sans-Bold.ttf
                  )
add_custom_target(mono ALL fontforge ${CMAKE_CURRENT_SOURCE_DIR}/generate-ttf.pe
                   ${CMAKE_CURRENT_SOURCE_DIR}/oxygen-fonts/mono-400/src/OxygenMono-Regular.sfd
                   ${CMAKE_CURRENT_BINARY_DIR}/OxygenMono-Regular.ttf
                  )

set(fontFiles
    ${CMAKE_CURRENT_BINARY_DIR}/OxygenMono-Regular.ttf
    ${CMAKE_CURRENT_BINARY_DIR}/Oxygen-Sans-Bold.ttf
    ${CMAKE_CURRENT_BINARY_DIR}/Oxygen-Sans.ttf
)

install(FILES ${fontFiles} DESTINATION ${OXYGEN_FONT_INSTALL_DIR})
