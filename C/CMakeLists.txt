# == DO NOT EDIT THE FOLLOWING LINES for the Raspberry Pi Pico VS Code Extension to work ==
if(WIN32)
    set(USERHOME $ENV{USERPROFILE})
else()
    set(USERHOME $ENV{HOME})
endif()
set(sdkVersion 2.1.0)
set(toolchainVersion 13_3_Rel1)
set(picotoolVersion 2.1.0)
set(picoVscode ${USERHOME}/.pico-sdk/cmake/pico-vscode.cmake)
if (EXISTS ${picoVscode})
    include(${picoVscode})
endif()
# ====================================================================================
set(PICO_BOARD pico2_w CACHE STRING "Board type")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

cmake_minimum_required(VERSION 3.12)

#include(pico-sdk/pico_sdk_init.cmake)
# Pull in PICO SDK (must be before project)
include(pico_sdk_import.cmake)
project(rp2040_arducam)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
pico_sdk_init()
add_subdirectory(ArduCAM)
# Compile choose demo 
#add_subdirectory(Examples/Arducam_MINI_2MP_Plus_Videostreaming)
#add_subdirectory(Examples/ArduCAM_Mini_2MP_Plus_4CAM_VideoStreaming)
add_subdirectory(Examples/Arducam_MINI_5MP_Plus_Videostreaming)
#add_subdirectory(Examples/ArduCAM_Mini_5MP_Plus_4CAM_VideoStreaming)