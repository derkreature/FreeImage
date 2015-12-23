cmake_minimum_required(VERSION 3.0)

project(LibJXR)

set(HEADERS ${CMAKE_CURRENT_SOURCE_DIR} image/sys jxrgluelib common/include)

set(SOURCES 
		image/decode/decode.c
		image/decode/JXRTranscode.c
		image/decode/postprocess.c
		image/decode/segdec.c
		image/decode/strdec.c
		image/decode/strdec_x86.c
		image/decode/strInvTransform.c
		image/decode/strPredQuantDec.c
		image/encode/encode.c
		image/encode/segenc.c
		image/encode/strenc.c
		image/encode/strenc_x86.c
		image/encode/strFwdTransform.c
		image/encode/strPredQuantEnc.c
		image/sys/adapthuff.c
		image/sys/image.c
		image/sys/strcodec.c
		image/sys/strPredQuant.c
		image/sys/strTransform.c
		jxrgluelib/JXRGlue.c
		jxrgluelib/JXRGlueJxr.c
		jxrgluelib/JXRGluePFC.c
		jxrgluelib/JXRMeta.c
	)	
		
add_definitions(-D__MINGW64_TOOLCHAIN__)
add_library(LibJXR STATIC ${SOURCES})
target_include_directories(LibJXR PUBLIC ${HEADERS})