cmake_minimum_required(VERSION 3.20)
project(os)


if (TARGET COMiC::os)
    message("using external os api")
else ()
    add_subdirectory(windows)
    if (NOT TARGET COMiC::os)
        message(FATAL_ERROR "current os not supported")
    endif ()
endif ()