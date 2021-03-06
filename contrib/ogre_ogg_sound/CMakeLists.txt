PROJECT(OgreOggSound)

CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

FIND_PACKAGE(Boost COMPONENTS thread)
FIND_PACKAGE(OpenAL REQUIRED)
FIND_PACKAGE(OGRE REQUIRED)
FIND_PACKAGE(Ogg REQUIRED)
FIND_PACKAGE(Vorbis REQUIRED)

AUX_SOURCE_DIRECTORY(src OGREOGGSOUND_SRCS)

INCLUDE_DIRECTORIES(
    include
    ${Boost_INCLUDE_DIRS}
    ${OGRE_INCLUDE_DIRS}
    ${OpenAL_INCLUDE_DIRS}
    ${OGG_INCLUDE_DIRS}
    ${VORBIS_INCLUDE_DIRS}
)



LINK_LIBRARIES(
    ${Boost_LIBRARIES}
    ${OGRE_LIBRARIES}
    ${OpenAL_LIBRARIES}
    ${Ogg_LIBRARIES}
    ${Vorbis_LIBRARIES}
)

ADD_DEFINITIONS(
    -DHAVE_EFX=0
    -DOGGSOUND_THREADED=1
)

ADD_LIBRARY(OgreOggSound SHARED ${OGREOGGSOUND_SRCS})

set_target_properties(OgreOggSound PROPERTIES PREFIX "")

INSTALL(TARGETS OgreOggSound
		LIBRARY DESTINATION bin
		RUNTIME DESTINATION bin
)
