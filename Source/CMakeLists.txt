cmake_minimum_required(VERSION 3.0)

option(BUILD_SHARED_LIBS "Build shared library." ON)


if(WIN32)
  add_definitions (/D "_CRT_SECURE_NO_WARNINGS")
  if(BUILD_SHARED_LIBS)
    set(LIBTYPE SHARED)
  else()
    set(LIBTYPE STATIC)
  endif()
endif()

if(BUILD_SHARED_LIBS)
	add_definitions(-DFREEIMAGE_EXPORTS)
  else()
	add_definitions(-DFREEIMAGE_LIB)
endif()

add_definitions(-DOPJ_STATIC -DLIBRAW_NODLL -DDISABLE_PERF_MEASUREMENT -DCINTERFACE)
add_definitions( "/W3 /D_CRT_SECURE_NO_WARNINGS /wd4005 /wd4996 /wd4477 /wd4267 /wd4244 /wd4018 /wd4305 /wd4018 /wd4838 /wd4101 /wd4800 /wd4554 /wd4101 /wd4146 /wd4804 /wd4309 /wd4146 /wd4102 /nologo" ) 



# Static build
  set(CompilerFlags
        CMAKE_CXX_FLAGS CMAKE_CXX_FLAGS_DEBUG CMAKE_CXX_FLAGS_RELEASE
        CMAKE_CXX_FLAGS_MINSIZEREL CMAKE_CXX_FLAGS_RELWITHDEBINFO
        CMAKE_C_FLAGS CMAKE_C_FLAGS_DEBUG CMAKE_C_FLAGS_RELEASE
        CMAKE_C_FLAGS_MINSIZEREL CMAKE_C_FLAGS_RELWITHDEBINFO)
  foreach(CompilerFlag ${CompilerFlags})
    string(REPLACE "/MD" "/MT" ${CompilerFlag} "${${CompilerFlag}}")
  endforeach()



add_subdirectory(OpenEXR)
add_subdirectory(LibWebP)
add_subdirectory(LibTIFF4)
add_subdirectory(LibRawLite)
add_subdirectory(LibPNG)
add_subdirectory(LibOpenJPEG)
add_subdirectory(LibJXR)
add_subdirectory(LibJPEG)

project(FreeImage)

set(HEADERS ${CMAKE_CURRENT_SOURCE_DIR} DeprecationManager ${CMAKE_CURRENT_SOURCE_DIR}/../../zlib ${CMAKE_CURRENT_SOURCE_DIR}/../../zlib/include )

set(SOURCES
		FreeImage/BitmapAccess.cpp
		FreeImage/ColorLookup.cpp
		FreeImage/ConversionRGBA16.cpp
		FreeImage/ConversionRGBAF.cpp
		FreeImage/FreeImage.cpp
		FreeImage/FreeImageIO.cpp
		FreeImage/GetType.cpp
		FreeImage/LFPQuantizer.cpp
		FreeImage/MemoryIO.cpp
		FreeImage/PixelAccess.cpp
		FreeImage/NNQuantizer.cpp
		FreeImage/WuQuantizer.cpp
		FreeImage/Conversion.cpp
		FreeImage/Conversion16_555.cpp
		FreeImage/Conversion16_565.cpp
		FreeImage/Conversion24.cpp
		FreeImage/Conversion32.cpp
		FreeImage/Conversion4.cpp
		FreeImage/Conversion8.cpp
		FreeImage/ConversionFloat.cpp
		FreeImage/ConversionRGB16.cpp
		FreeImage/ConversionRGBF.cpp
		FreeImage/ConversionType.cpp
		FreeImage/ConversionUINT16.cpp
		FreeImage/Halftoning.cpp
		FreeImage/tmoColorConvert.cpp
		FreeImage/tmoDrago03.cpp
		FreeImage/tmoFattal02.cpp
		FreeImage/tmoReinhard05.cpp
		FreeImage/ToneMapping.cpp
		FreeImage/J2KHelper.cpp
		FreeImage/MNGHelper.cpp
		FreeImage/Plugin.cpp
		FreeImage/PluginBMP.cpp
		FreeImage/PluginCUT.cpp
		FreeImage/PluginDDS.cpp
		FreeImage/PluginEXR.cpp
		FreeImage/PluginG3.cpp
		FreeImage/PluginGIF.cpp
		FreeImage/PluginHDR.cpp
		FreeImage/PluginICO.cpp
		FreeImage/PluginIFF.cpp
		FreeImage/PluginJ2K.cpp
		FreeImage/PluginJNG.cpp
		FreeImage/PluginJP2.cpp
		FreeImage/PluginJPEG.cpp
		FreeImage/PluginJXR.cpp
		FreeImage/PluginKOALA.cpp
		FreeImage/PluginMNG.cpp
		FreeImage/PluginPCD.cpp
		FreeImage/PluginPCX.cpp
		FreeImage/PluginPFM.cpp
		FreeImage/PluginPICT.cpp
		FreeImage/PluginPNG.cpp
		FreeImage/PluginPNM.cpp
		FreeImage/PluginPSD.cpp
		FreeImage/PluginRAS.cpp
		FreeImage/PluginRAW.cpp
		FreeImage/PluginSGI.cpp
		FreeImage/PluginTARGA.cpp
		FreeImage/PluginTIFF.cpp
		FreeImage/PluginWBMP.cpp
		FreeImage/PluginWebP.cpp
		FreeImage/PluginXBM.cpp
		FreeImage/PluginXPM.cpp
		FreeImage/PSDParser.cpp
		FreeImage/TIFFLogLuv.cpp
		DeprecationManager/Deprecated.cpp
		DeprecationManager/DeprecationMgr.cpp
		FreeImage/CacheFile.cpp
		FreeImage/MultiPage.cpp
		FreeImage/ZLibInterface.cpp
		Metadata/Exif.cpp
		Metadata/FIRational.cpp
		Metadata/FreeImageTag.cpp
		Metadata/IPTC.cpp
		Metadata/TagConversion.cpp
		Metadata/TagLib.cpp
		Metadata/XTIFF.cpp
		FreeImageToolkit/Background.cpp
		FreeImageToolkit/BSplineRotate.cpp
		FreeImageToolkit/Channels.cpp
		FreeImageToolkit/ClassicRotate.cpp
		FreeImageToolkit/Colors.cpp
		FreeImageToolkit/CopyPaste.cpp
		FreeImageToolkit/Display.cpp
		FreeImageToolkit/Flip.cpp
		FreeImageToolkit/JPEGTransform.cpp
		FreeImageToolkit/MultigridPoissonSolver.cpp
		FreeImageToolkit/Rescale.cpp
		FreeImageToolkit/Resize.cpp
	)
		
add_library(FreeImage ${LIBTYPE} ${SOURCES})
target_include_directories(FreeImage PUBLIC ${HEADERS})
target_link_libraries(FreeImage OpenEXR LibWebP LibTIFF4 LibRawLite LibPNG LibOpenJPEG LibJXR LibJPEG ws2_32)











