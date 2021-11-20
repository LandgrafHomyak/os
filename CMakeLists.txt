cmake_minimum_required(VERSION 3.20)
project(os)

if (${WIN32})
    add_subdirectory(windows)
    set_target_properties(os_windows PROPERTIES OUTPUT_NAME os)
    add_library(os ALIAS os_windows)
endif()
