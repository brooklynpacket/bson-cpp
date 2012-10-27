cmake_minimum_required(VERSION 2.8)
project(bson-cpp)

set(CMAKE_XCODE_ATTRIBUTE_GCC_VERSION "com.apple.compilers.llvm.clang.1_0")
set(CMAKE_XCODE_ATTRIBUTE_CLANG_CXX_LANGUAGE_STANDARD "c++11")
set(CMAKE_XCODE_ATTRIBUTE_CLANG_CXX_LIBRARY "libc++")
include_directories(${CMAKE_CURRENT_SOURCE_DIR})


if (CMAKE_COMPILER_IS_GNUCXX OR CMAKE_COMPILER_IS_GNUCC)
  set ( CMAKE_CXX_FLAGS "-std=c++0x")
  #set ( CMAKE_CXX_FLAGS_DEBUG "")
  #set ( CMAKE_CXX_FLAGS_RELEASE  "" )
endif ()
set(BSON_HEADERS
	inc/bson-inl.h
	inc/bson.h
	inc/bsonassert.h
	inc/bsonelement.h
	inc/bsonmisc.h
	inc/bsonobj.h
	inc/bsonobjbuilder.h
	inc/bsonobjiterator.h
	inc/bsontypes.h
	inc/inline_decls.h
	inc/oid.h
	inc/ordering.h
	inc/stringdata.h
	inc/util/builder.h
	inc/util/embedded_builder.h
	inc/util/hex.h
	inc/util/misc.h
	inc/util/noncopyable.h
	inc/util/optime.h
	inc/util/time_support.h
)
set(BSON_SOURCE
	src/bsonobj.cpp
        src/oid.cpp
        lib/base64.cpp
        lib/md5.c
        lib/nonce.cpp
)

add_library(bsoncpp ${BSON_SOURCE} ${BSON_HEADERS})


install(TARGETS bsoncpp
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib)
install(FILES 
)
