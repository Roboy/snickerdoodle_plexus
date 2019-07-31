cmake_minimum_required(VERSION 2.8.3)
project(snickerdoodle_plexus)
SET(CMAKE_SYSTEM_NAME "Linux")
SET(CMAKE_SYSTEM_VERSION 1)

set (CMAKE_SYSTEM_NAME      "Linux")

# specify the cross compiler
set (CMAKE_SYSTEM_PROCESSOR "arm")
set (CROSS_PREFIX           "arm-linux-gnueabihf-")

#set (CMAKE_MAKE_PROGRAM     "C:/Xilinx/SDK/2017.4/gnuwin/bin/make.exe" CACHE PATH "" FORCE)
set (CMAKE_C_COMPILER       "${CROSS_PREFIX}gcc" CACHE PATH "" FORCE)
set (CMAKE_CXX_COMPILER     "${CROSS_PREFIX}g++" CACHE PATH "" FORCE)
set (CMAKE_ASM_COMPILER     "${CROSS_PREFIX}gcc" CACHE PATH "" FORCE)
set (CMAKE_AR               "${CROSS_PREFIX}ar" CACHE FILEPATH "Archiver")

set (CMAKE_FIND_ROOT_PATH_MODE_PROGRAM	NEVER)
set (CMAKE_FIND_ROOT_PATH_MODE_LIBRARY	NEVER)
set (CMAKE_FIND_ROOT_PATH_MODE_INCLUDE	NEVER)

SET(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -g")

find_package(catkin REQUIRED COMPONENTS
	roscpp
	std_msgs
)

include(findros)

catkin_package(CATKIN_DEPENDS
	message_runtime
)

include_directories(
	${catkin_INCLUDE_DIRS}
)

add_executable(main main.cpp)
target_link_libraries(main ${ros_LIBRARIES})
