# Minimum CMake version for build process
cmake_minimum_required(VERSION 4.2)

# Define the project and tell CMake it is a C/C++ project
project(
    Pkmn_Emerald_Tileset_Viewer
    VERSION 1.0
    DESCRIPTION ""
    LANGUAGES CXX
)

# Set C++ standard
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set output directory for the executable
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/../bin")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/../bin")

# --- Load third-party libraries --- #

include(FetchContent)

# spdlog
FetchContent_Declare(
    spdlog
    GIT_REPOSITORY https://github.com/gabime/spdlog.git
    GIT_TAG v1.17.0
    GIT_SHALLOW ON
    FIND_PACKAGE_ARGS NAMES spdlog
)
FetchContent_MakeAvailable(spdlog)

# Stb
add_library(Stb STATIC
    ${CMAKE_SOURCE_DIR}/vendor/stb/stb_image.cpp
)

target_include_directories(Stb PUBLIC ${CMAKE_SOURCE_DIR}/vendor)

# WxWidgets
set(wxBUILD_SHARED OFF)

FetchContent_Declare(
   wxWidgets
   GIT_REPOSITORY https://github.com/wxWidgets/wxWidgets.git
   GIT_TAG v3.3.4
   GIT_SHALLOW ON
)
FetchContent_MakeAvailable(wxWidgets)

# Load subdirectories
add_subdirectory(src/data)
add_subdirectory(src/gui)

# Add the executable
add_executable(Main
    src/main.cpp
)

# Add include directories for the main executable
target_include_directories(Main PUBLIC "${CMAKE_SOURCE_DIR}/include")

target_link_libraries(Main PRIVATE
    Gui

    # Vendor libraries
    wxbase
    wxcore
    wxnet
)
