cmake_minimum_required(VERSION 3.0)

project(LibOpenJPEG)

set(HEADERS ${CMAKE_CURRENT_SOURCE_DIR})

set(SOURCES 
		bio.c 
		cio.c 
		dwt.c 
		event.c
		function_list.c
		image.c 
		invert.c
		j2k.c 
		jp2.c 
		mct.c
		mqc.c 
		openjpeg.c
		opj_clock.c
		pi.c 
		raw.c 
		t1.c 
		t2.c
		tcd.c 
		tgt.c
	)	
	
add_library(LibOpenJPEG STATIC ${SOURCES})
target_include_directories(LibOpenJPEG PUBLIC ${HEADERS})