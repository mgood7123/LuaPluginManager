cmake_minimum_required(VERSION 3.23)

project(lua)

function(BUILD_LUA)
    FILE(GLOB SOURCES "${ARGV0}/src/*.c")
    LIST(REMOVE_ITEM SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/${ARGV0}/src/lua.c")
    LIST(REMOVE_ITEM SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/${ARGV0}/src/luac.c")
    add_library(${ARGV0}-lib STATIC ${SOURCES})
    add_executable(${ARGV0}-interpreter ${ARGV0}/src/lua.c)
    add_executable(${ARGV0}-compiler ${ARGV0}/src/luac.c)
    target_link_libraries(${ARGV0}-interpreter ${ARGV0}-lib)
    target_link_libraries(${ARGV0}-compiler ${ARGV0}-lib)
endfunction()

BUILD_LUA(lua-5.4.4)