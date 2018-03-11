cmake_minimum_required( VERSION 2.8 )

project(snippets)
#set(VERSION 0.1.0)
#set(OWR_API_VERSION 0.1)

#------------
find_package(PkgConfig 0.29.1 REQUIRED)
#SET(ENV{PKG_CONFIG_PATH} ${_PKG_CONFIG_PATH})

#include( AutoCMake.cmake )

#------------

#add_definitions( -DOWR_LITE)
#autocmake_pkgconfig_init()

pkg_check_modules(BASE  REQUIRED
                  gstreamer-1.0>=1.12.2
                  gstreamer-base-1.0>=1.12.2)

#MESSAGE("GSTREAMER_LIBRARIES    : ${BASE_LIBRARIES}   " )
#MESSAGE("GSTREAMER_LIBRARY_DIRS : ${BASE_LIBRARY_DIRS}" )
#MESSAGE("GSTREAMER_INCLUDE_DIRS : ${BASE_INCLUDE_DIRS}" )


include_directories(${CMAKE_SOURCE_DIR})
include_directories(${BASE_INCLUDE_DIRS}) 
link_directories(${BASE_LIBRARY_DIRS})


include_directories(transceiver)
link_directories( ${this_LINK_DIRECTORIES} )

add_executable (dynamic-filter dynamic-filter.c)
target_link_libraries(dynamic-filter ${BASE_LIBRARIES})



add_executable (dynamic-tee-vsink dynamic-tee-vsink.c)
target_link_libraries(dynamic-tee-vsink ${BASE_LIBRARIES})

#add_dependencies(transceiver libwebrtctransport )

#add_subdirectory( libwebrtctransport  )
#add_subdirectory( tests/transceiver  )
#install(DIRECTORY web DESTINATION testkits/openwebrtc )
