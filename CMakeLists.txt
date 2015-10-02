cmake_minimum_required(VERSION 2.8.4)
cmake_policy(SET CMP0042 NEW)
project(44a)
set(APP_NAME 44a)
set(BUNDLE_NAME "44a")

# ===================== oF Directory =====================
set(OF_DIRECTORY "/Users/jude/developer/of_v0.8.4_osx_release")
# ========================================================

# ===================== Compiler Flags =====================
set(CMAKE_C_COMPILER "/usr/bin/clang")
set(CMAKE_C_FLAGS "")

set(CMAKE_CXX_COMPILER "/usr/bin/clang++")
set(CMAKE_CXX_FLAGS "-stdlib=libstdc++ -D__MACOSX_CORE__")

set(CMAKE_OSX_ARCHITECTURES i386)
add_compile_options(-Wno-deprecated-declarations)
# ==========================================================

# ===================== Source Files =====================
set(SOURCE_FILES
        src/main.cpp
        src/ofApp.cpp)
# ========================================================

# =========== Set Global Properties ==============
include(addons.cmake)
include(openFrameworks.cmake)
# ================================================

# ===================== System Frameworks =====================

# =============================================================

# ===================== Include Dirs =====================

# ========================================================

# ===================== Libs =====================

# ================================================

# ============ Compile and Link ==================
add_executable(${APP_NAME} MACOSX_BUNDLE ${SOURCE_FILES})
add_dependencies(${APP_NAME} of_shared)
target_link_libraries(${APP_NAME} $<TARGET_FILE:of_shared>)
# ================================================

# ============ MACOSX_BUNDLE Settings ============
#set_source_files_properties( # Copy app icon
#        resources/icon-debug.icns
#        PROPERTIES
#        MACOSX_PACKAGE_LOCATION Resources
#)

ADD_CUSTOM_COMMAND(TARGET ${APP_NAME}
        POST_BUILD
        COMMAND ${CMAKE_INSTALL_NAME_TOOL}
        ARGS -change "@rpath/libopenFrameworks.dylib" "@loader_path/../Frameworks/libopenFrameworks.dylib" $<TARGET_FILE:${APP_NAME}>
)

set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_INFO_STRING "Cmake openFrameworks CLion test app")
#set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_ICON_FILE icon-debug.icns)
# set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_GUI_IDENTIFIER)
set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_LONG_VERSION_STRING "0.0.1 pre-release alpha")
set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_BUNDLE_NAME ${BUNDLE_NAME})
set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_SHORT_VERSION_STRING 0.0.1)
set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_BUNDLE_VERSION 0.0.1)
set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_COPYRIGHT "(c) kureta 2015")
set_target_properties(${APP_NAME} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
# ================================================