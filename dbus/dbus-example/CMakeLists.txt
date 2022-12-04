cmake_minimum_required(VERSION 2.8.11)

project(dbus C CXX)
        
set (CMAKE_CXX_STANDARD 17)

set(DBUS_SRC_FILES src/dbus-example.cpp )

string(LENGTH "${CMAKE_SOURCE_DIR}/" SOURCE_PATH_SIZE)
add_definitions("-DSOURCE_PATH_SIZE=${SOURCE_PATH_SIZE}")
  
find_package(Threads)
add_executable(dbus ${DBUS_SRC_FILES})
target_include_directories(dbus PUBLIC  inc)

set(CMAKE_CFLAGS  "-I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include")
set(CMAKE_LDFLAGS "-lglib-2.0 -l dbus-glib-1")

set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS}  ${CMAKE_CFLAGS} ${CMAKE_LDFLAGS} -lrt -lm -g -pipe -Wall -lpthread ")

target_link_libraries(dbus rt pthread )
