cmake_minimum_required(VERSION 3.16)
project(emscripten_super)


add_subdirectory(emsdk)

include(ExternalProject)

externalproject_add(cpp
    SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/cpp"
    CMAKE_ARGS
        "-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}"
        "-DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX}"
        "-DCMAKE_TOOLCHAIN_FILE=${EMSCRIPTEN_ROOT_PATH}/cmake/Modules/Platform/Emscripten.cmake"
    INSTALL_COMMAND
        echo "\\nEnter ${CMAKE_CURRENT_BINARY_DIR}/cpp-prefix/src/cpp-build and type python -m SimpleHTTPServer 8000 to start the web server.\\n"
    )

add_dependencies(cpp emsdk)


