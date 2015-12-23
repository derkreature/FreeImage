cmake_minimum_required(VERSION 3.0)

project(LibPNG)

set(HEADERS ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../zlib ${CMAKE_CURRENT_SOURCE_DIR}/zlib ${CMAKE_CURRENT_SOURCE_DIR}/zlib/include ${CMAKE_CURRENT_SOURCE_DIR}/../zlib/include ${CMAKE_CURRENT_SOURCE_DIR}/../../zlib/include ${CMAKE_CURRENT_SOURCE_DIR}/../../../zlib/include)

set(SOURCES 	  
	  png.c
	  pngerror.c
	  pngget.c
	  pngmem.c
	  pngpread.c
	  pngread.c
	  pngrio.c
	  pngrtran.c
	  pngrutil.c
	  pngset.c
	  pngtrans.c
	  pngwio.c
	  pngwrite.c
	  pngwtran.c
	  pngwutil.c
	)	
				
add_library(LibPNG STATIC ${SOURCES})
target_include_directories(LibPNG PUBLIC ${HEADERS})
target_link_libraries(LibPNG)

