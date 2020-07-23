cmake_minimum_required (VERSION 3.5)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_CXX_FLAGS "-std=c++11")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)


FIND_PACKAGE( OpenCV REQUIRED )
message(STATUS "OpenCV library status:")
message(STATUS "    VERSION: ${OpenCV_VERSION}")
message(STATUS "    LIBS: ${OpenCV_LIBS}")
message(STATUS "    INCLUDE_PATH: ${OpenCV_INCLUDE_DIRS}")

# Requires OpenCV v4.2 or later
IF (${OpenCV_VERSION} VERSION_LESS 4.2.0)
    MESSAGE(FATAL_ERROR 
        "OpenCV version is not compatible : ${OpenCV_VERSION}. Requires atleast OpenCV v4.2.0")
ENDIF()


set (SRCS
    ./main.cpp
    ./segmentation_methods.cpp
    ./thinning_methods.cpp
    ./flood_fill_methods.cpp
    ./json.hpp
    ./road_segmentation.h
)

if(WIN32)
	add_executable(${PROJECT_NAME} WIN32
		${SRCS}
	)
else()
	add_executable(${PROJECT_NAME}
		${SRCS}
	)
endif()

TARGET_LINK_LIBRARIES( ${PROJECT_NAME}  ${OpenCV_LIBS} )
