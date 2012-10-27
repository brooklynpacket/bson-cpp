cmake_minimum_required(VERSION 2.8)


set(CMAKE_XCODE_ATTRIBUTE_GCC_VERSION "com.apple.compilers.llvm.clang.1_0")
set(CMAKE_XCODE_ATTRIBUTE_CLANG_CXX_LANGUAGE_STANDARD "c++11")
set(CMAKE_XCODE_ATTRIBUTE_CLANG_CXX_LIBRARY "libc++")
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

#find_package( Boost REQUIRED COMPONENTS system)

#include_directories( ${Boost_INCLUDE_DIRS} )

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

# Disabling the test application for now, incompatibility because of json's req for
# boost thread.
# Play with the following defines
# Disable auto-linking. 
#add_definitions( -DBOOST_ALL_NO_LIB )
# In case of a Shared Boost install (dlls), you should then enable this
# add_definitions( -DBOOST_ALL_DYN_LINK )

# Explicitly tell find-package to search for Static Boost libs (if needed)
#set( Boost_USE_STATIC_LIBS ON ) 
#find_package( Boost REQUIRED COMPONENTS system)

#include_directories( ${Boost_INCLUDE_DIRS} )

#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)
#add_executable(bson_test 
#	test/framework.cpp 
#	test/test_bsonobj.cpp
#	test/json.cpp
#)
#target_link_libraries(bson_test bsoncpp ${Boost_LIBRARIES})
