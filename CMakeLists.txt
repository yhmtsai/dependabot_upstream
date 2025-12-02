cmake_minimum_required(VERSION 3.14)
project(UpStream)

if(EXISTS "${UpStream_SOURCE_DIR}/.git")
    find_package(Git QUIET)
    if(GIT_FOUND)
        execute_process(
            COMMAND
                ${GIT_EXECUTABLE} log -1 --format=%h ${UpStream_SOURCE_DIR}
                WORKING_DIRECTORY ${UpStream_SOURCE_DIR}
                OUTPUT_VARIABLE GIT_SHORTREV
                OUTPUT_STRIP_TRAILING_WHITESPACE
            )
        message(STATUS "GIT COMMIT SHA ${GIT_SHORTREV}")
    endif()
endif()
