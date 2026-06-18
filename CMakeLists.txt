# Generated from MQSearchItem.vcxproj
# This file is designed to work with add_subdirectory()

# ---------------------------------------------------------------------
# Props file includes
# ---------------------------------------------------------------------
include("../../Plugin.cmake")

# ---------------------------------------------------------------------
# Header files
# ---------------------------------------------------------------------
set(MQSearchItem_HEADERS
    "resource.h"
)

source_groups("Header Files" ${MQSearchItem_HEADERS})

# ---------------------------------------------------------------------
# Other files
# ---------------------------------------------------------------------
set(MQSearchItem_OTHERFILES
    "MQSearchItem.rc"
    "README.md"
)

source_group("Resource Files" FILES ${MQSearchItem_OTHERFILES})

# ---------------------------------------------------------------------
# Source files
# ---------------------------------------------------------------------
set(MQSearchItem_SOURCES
    "MQSearchItem.cpp"
)

source_groups("Source Files" ${MQSearchItem_SOURCES})

# ---------------------------------------------------------------------
# Target definition
# ---------------------------------------------------------------------
add_library(MQSearchItem SHARED
    ${MQSearchItem_HEADERS}
    ${MQSearchItem_OTHERFILES}
    ${MQSearchItem_SOURCES}
)

set_target_properties(MQSearchItem PROPERTIES FOLDER "external")

# ---------------------------------------------------------------------
# Apply props file configurations
# ---------------------------------------------------------------------
target_Plugin_props(MQSearchItem)

# ---------------------------------------------------------------------
# Project dependencies
# ---------------------------------------------------------------------
target_link_libraries(MQSearchItem PRIVATE MQ2Main)

# ---------------------------------------------------------------------
# PRE_BUILD events
# ---------------------------------------------------------------------

add_custom_command(TARGET MQSearchItem PRE_BUILD
    COMMAND powershell.exe -ExecutionPolicy Bypass -NoProfile -NonInteractive -File "${CMAKE_SOURCE_DIR}/tools/build_scripts/Plugin_Versioning.ps1" -ProjectName "${PROJECT_NAME}" -ProjectDirectory "${CMAKE_CURRENT_SOURCE_DIR}/"
    COMMENT "Updating version resource for ${PROJECT_NAME}..."
    VERBATIM
)

# ============================================================================
# MANUAL CONVERSION NOTES
# ============================================================================
#
# - Review and adjust as needed
