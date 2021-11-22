cmake_minimum_required(VERSION 3.0)

add_library(__COMiC__os_include INTERFACE)

target_link_libraries(__COMiC__os_include INTERFACE COMiC::types)
target_include_directories(__COMiC__os_include INTERFACE include)

install(
        TARGETS __COMiC__os_include
        PUBLIC_HEADER DESTINATION ./include
)

add_library(COMiC::os::_include ALIAS __COMiC__os_include)

if (TARGET COMiC::os)
    message("using external os api")
else ()
    add_subdirectory(windows)
    if (NOT TARGET COMiC::os)
        message(FATAL_ERROR "current os not supported")
    endif ()
endif ()