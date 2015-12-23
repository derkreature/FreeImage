cmake_minimum_required(VERSION 3.0)

project(LibRawLite)

set(HEADERS ${CMAKE_CURRENT_SOURCE_DIR})

set(SOURCES 
		internal/dcraw_common.cpp
		internal/dcraw_fileio.cpp
		internal/demosaic_packs.cpp
		src/libraw_c_api.cpp
		src/libraw_cxx.cpp
		src/libraw_datastream.cpp
	)	
		
add_library(LibRawLite STATIC ${SOURCES})
target_include_directories(LibRawLite PUBLIC ${HEADERS})