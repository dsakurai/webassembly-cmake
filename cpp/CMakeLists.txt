project(emscripten_cpp)


if (EMSCRIPTEN)
    if (CMAKE_BUILD_TYPE MATCHES Debug)
        set(CMAKE_CXX_FLAGS_DEBUG "-g4")
    endif (CMAKE_BUILD_TYPE MATCHES Debug)
    set(CMAKE_EXECUTABLE_SUFFIX ".html")
endif()

# index.html
add_executable(index main.cpp)

