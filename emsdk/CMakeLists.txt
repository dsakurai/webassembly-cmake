include(ExternalProject)

set(EMSCRIPTEN_VERSION "1.39.18" CACHE STRING "Can be `latest`. Also, `emsdk list` shows the available versions.")

set(EMSCRIPTEN_SDK_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/emsdk-vcs"
    CACHE PATH "Path to the emscripten SDK source directory")

set(EMSCRIPTEN_ROOT_PATH "${EMSCRIPTEN_SDK_SOURCE_DIR}/upstream/emscripten"
    CACHE PATH "Path to the emscripten SDK source directory")

externalproject_add(emsdk
    SOURCE_DIR "${EMSCRIPTEN_SDK_SOURCE_DIR}"
    CONFIGURE_COMMAND ""
    BUILD_IN_SOURCE yes
    BUILD_COMMAND
        "<SOURCE_DIR>/emsdk" install --build=Release "${EMSCRIPTEN_VERSION}"
    && "<SOURCE_DIR>/emsdk" activate --build=Release "${EMSCRIPTEN_VERSION}"
    INSTALL_COMMAND ""
    )


