cmake_minimum_required(VERSION 2.6)

# Play with the following defines
# Disable auto-linking. 
add_definitions( -DBOOST_ALL_NO_LIB )
# In case of a Shared Boost install (dlls), you should then enable this
# add_definitions( -DBOOST_ALL_DYN_LINK )

# Explicitly tell find-package to search for Static Boost libs (if needed)
set( Boost_USE_STATIC_LIBS ON ) 
find_package( Boost REQUIRED COMPONENTS thread system)

include_directories( ${Boost_INCLUDE_DIRS} )
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

add_library(bson 
	src/util/json.cpp
	src/bsonobj.cpp
	src/oid.cpp
	lib/base64.cpp
	lib/md5.c
	lib/nonce.cpp
)

target_link_libraries(bson ${Boost_LIBRARIES} )

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)
add_executable(bson_test test/framework.cpp test/test_bsonobj.cpp)
target_link_libraries(bson_test bson)