cmake_minimum_required(VERSION 2.8)


set(CMAKE_XCODE_ATTRIBUTE_GCC_VERSION "com.apple.compilers.llvm.clang.1_0")
set(CMAKE_XCODE_ATTRIBUTE_CLANG_CXX_LANGUAGE_STANDARD "c++11")
set(CMAKE_XCODE_ATTRIBUTE_CLANG_CXX_LIBRARY "libc++")
include_directories(${CMAKE_CURRENT_SOURCE_DIR})


if (CMAKE_COMPILER_IS_GNUCXX OR CMAKE_COMPILER_IS_GNUCC)
  set ( CMAKE_CXX_FLAGS "-std=c++0x")
  #set ( CMAKE_CXX_FLAGS_DEBUG "")
  #set ( CMAKE_CXX_FLAGS_RELEASE  "" )
endif ()

add_library(bsoncpp SHARED
	src/bsonobj.cpp
	src/oid.cpp
	lib/base64.cpp
	lib/md5.c
	lib/nonce.cpp
	#headers, for things like xcode to see
	src/bson-inl.h
	src/bson.h
	src/bsonassert.h
	src/bsonelement.h
	src/bsonmisc.h
	src/bsonobj.h
	src/bsonobjbuilder.h
	src/bsonobjiterator.h
	src/bsontypes.h
	src/inline_decls.h
	src/oid.h
	src/ordering.h
	src/stringdata.h
	src/util/builder.h
	src/util/embedded_builder.h
)
