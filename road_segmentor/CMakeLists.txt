cmake_minimum_required (VERSION 3.5)

project ("RoadSegmentator" 
	VERSION 2.1 
	DESCRIPTION "Segments line geometries in an OSM" 
	LANGUAGES CXX
)

if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)
    set(CMAKE_CXX_EXTENSIONS OFF)
    set_property(GLOBAL PROPERTY USE_FOLDERS ON)
endif()

# build the following
add_subdirectory("src")