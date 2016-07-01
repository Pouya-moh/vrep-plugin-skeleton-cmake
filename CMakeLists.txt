project(v_repExtCMAKETEST)
# IMPORTANT NOTE! the name of .so file should be in the form of [lib]v_repExt*.so
# and that * should not contain underscore. Not my design!

cmake_minimum_required(VERSION 2.8)

# debugging and prettification
# set(CMAKE_VERBOSE_MAKEFILE ON)
# set(CMAKE_COLOR_MAKEFILE   ON)

# sources and includes. some say this is not a good approach!
file(GLOB SOURCES ${PROJECT_SOURCE_DIR}/common/*.cpp ${PROJECT_SOURCE_DIR}/src/*.cpp)
include_directories(${PROJECT_SOURCE_DIR}/include ${PROJECT_SOURCE_DIR}/common)

# needed for pthread
find_package(Threads REQUIRED)

# building it
add_library(${PROJECT_NAME} SHARED ${SOURCES})

# linking it against other object files
target_link_libraries(${PROJECT_NAME} ${CMAKE_THREAD_LIBS_INIT} ${CMAKE_DL_LIBS})